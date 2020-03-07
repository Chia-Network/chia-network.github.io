---
lang: en
layout: post
title:  "The ASIC Resistance of Proof of Space"
date:   2018-06-11
author: "[Bram Cohen](https://twitter.com/bramcohen) and [Gene Hoffman](https://twitter.com/hoffmang)"
---

A recent [podcast](http://multicoin.libsyn.com/conversations-with-multicoin-capital-dhruv-bansal) speculated quite a bit about the economics of Chia Network’s new proof of space and time consensus algorithm.

Let’s discuss the assertion that there are optimizations in storage technology allow for the creation of specialized Chia farming hardware that costs an order of magnitude less than commodity disks.

Even if it were possible to make such advantaged specialized hardware, it would likely be unprofitable to purchase storage solely for the purpose of farming. There’s $140 billion in storage capacity sold every year and a large fraction of that is unused and can easily be made to farm for Chia. Because Chia farming rewards will be much less than the replacement cost of that storage, work difficulty adjustment will make the reward per byte per day be substantially less than the amortized price of new storage. But even if all Chia farming hardware were purchased specifically for that use we believe the margin between specialized and unspecialized hardware will be within a factor of 2, and will explain why below.

(Let’s set aside proof of time for now because that’s a different issue with a different set of dynamics and we are not at all claiming that there can’t be specialized hardware for that.)

Some ground rules: The characteristics of a storage medium are:

* seek time,
* read rate,
* write rate
* price per terabyte.

Higher layer functionality of the file system such as inodes and indexing are a layer above the underlying hardware. It’s possible with all storage media to get access to a raw partition but applications rarely do that because modern mass storage is so unbelievably huge that the overhead added by such functionality doesn’t make a material impact on performance.

Optimizing storage technology for bulk storage applications, Chia farming included, is dominated by price per terabyte. Any technology which could do better than commodity hard drives would be dominating already. Any new innovation which does better will successfully take over the whole storage market, not just Chia farming.

The amount of time for the network to farm the next block will be at least one minute and will average five minutes. The speed of finding a proof of space doesn’t matter as long as it’s less than a minute, but rapidly makes farming not worth doing if it takes much more than a minute. Even the ‘glacial’ lookup and ‘slow’ read times on hard drives are still way better than what’s necessary to stay under a minute.

A bit of a math interlude to justify this claim:

The way proofs of space are formatted on disk is in a series of 8 lookup tables. The actual number may be slightly larger or smaller than 8. We haven’t finalized the details yet but it will be a single fixed value. When a challenge arrives a farmer has to do 8 sequential seeks to find out how good a response they have to that challenge and if so they do the complete set of 2⁸ (256) lookups to generate the complete proof of space and then publish it to the network. For most lookups which result in a non-winning response eight lookups even at 20 milliseconds per lookup will hardly even be noticeable in terms of drive performance, and the rare 256 lookups will clock in at around 5 seconds, well under the minute budget.

Tape drives, on the other hand, have seek times which are far too long to be used effectively. LTO-8 is the current industry fastest tape standard and supports read speeds of 360 MB/s uncompressed. Proofs of space are random enough to not be very compressible. Thus to stay under the minute threshold one would only have about 21 GB per minute per tape read head to find your proof of space on each tape. LTO-8 drives appear to priced higher than $2500 per drive and the LTO-8 data cartridge is about $180 for a 12TB tape. LTO-10 may increase the total read speed by a little more than a factor of 3 to 1.1 GB/s but that still leaves you with only about 66 GB per minute and that standard looks to be a ways off. We’ve concocted a “frankentape” idea of multiple infinity spools of tape of a size of about ~20GB under the LTO-8 standard but the cost of retail tape drives is indicative that stripping out the read heads and the motors is still going to be pretty expensive as you’ve got to have the equivalent of ~ 49 read heads and motor pairs to get through one terabyte in less than a minute. You would probably also need a full time tape repair person.

In talking to hard drive manufacturers, the biggest optimization they point out is potentially eliminating the cooling fan. Proof of space otherwise uses almost all of the other core requirements of generalized storage. You can potentially use older and slower seek times or bus technologies, but to get the read density needed, you have to use state of the art read and write heads. The core issue is that the demand for cheaper mass storage that is almost hot storage but a bit slower is very high already. Spinning disk has mostly become that solution as large storage buyers and even desktop computers have used spinning disk to help scale out SSD.

For storage costs there are two price points that matter. The best price to store a terabyte online is [Wasabi](https://wasabi.com/) at $5/Tb/month. The cheapest drive we could find on June 4, 2018 at Amazon was $22.00 per terabyte for a [Seagate 4TB drive](https://www.amazon.com/Seagate-SATA-3-5-Inch-Desktop-ST4000DM000/dp/B00B99JU4S/) before taxes and shipping (if any — thanks Prime!) Since Wasabi gets more expensive after about 18 weeks it’s pretty clear that ownership of the spinning drive is going to be the cheapest farming platform currently.

The most interesting alternative strategy that we’ve seen is write once blu-ray optical disc robots. A storage medium being limited to writing exactly once is less of a blocker for general purpose use than you might think, because that’s the usage pattern of a large fraction of all commercial storage and higher layer logic can be added to make such a thing look like a normal file system which happens to not free up space when you delete things and continues to lose empty space even when overwriting. Some ex-Facebook folks leveraged the near hot storage they’d created at Facebook to start a [blu-ray robot storage company](http://fortune.com/2015/05/27/sony-buys-former-facebook-execs-startup/) that Sony ended up acquiring. However it looks like Sony shelved the business shortly after acquiring it which doesn’t bode well for the technology. This is a potential optimization direction for pretty quick look up, write once optimization on proofs of space. But it is trading off the mass market scale of spinning disks for a new market of novel optical disk robots. They have to be quick to move through all the discs you’d want to read in the minute you have to find your best proof of space.

There is some truth to the general assertion that mass success of Chia could encourage storage innovations. The problem is that there isn’t (yet) an order of magnitude better way to store information. That puts the technology speculation out in the land of pure scientific discoveries. We are hard pressed to come up with a huge storage innovation that isn’t equally or more valuable to the buyers of the [585 million hard drives and SSDs expected to sell in 2018](https://www.statista.com/statistics/285474/hdds-and-ssds-in-pcs-global-shipments-2012-2017/).

There are a few optimizations in response to Chia’s success that we might see in storage technology. Letting a farm co-exist underneath a RAID that’s otherwise in use for other valuable purposes could unlock a lot of unused storage space, especially if the farm is beneath the RAID’s redundancy. We do expect to see custom ASICs added to some drives (and maybe all of them) to make it easy to seed a farm. But those are technologies for allowing the spare capacity on existing storage to be more expediently used for farming, not exclusively for farming. It is also important to note that the speed that [per terabyte prices are falling has slowed storage industry wide](https://www.backblaze.com/blog/hard-drive-cost-per-gigabyte/).

The primary attacks on proofs of space are algorithmic ones which use extra computational resources to get more rewards out of a fixed amount of space. Resisting those sorts of attacks is a major development focus for us and the subject of our [Asiacrypt paper](https://eprint.iacr.org/2018/183) which we’ve since made further improvements upon. We’re also going to have a best implementation competition with real cash rewards in the future after we’ve published a specification. We feel confident that such efforts will quickly result in a plateau of rewards for a modest amount of computation and that any better trade-offs will require an infeasible cost prohibitive amount of computational resources.
