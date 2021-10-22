---
lang: en
layout: post
title:  "Mining vs. Farming, the data behind being Green"
date:   2021-10-20
author: "[Johnmichael Hands](https://twitter.com/lebanonjon)"
---

<p align="center">
<img src="/assets/blog/mining-vs-farming.png" alt="Mining vs Farming" width="75%">
</p>

## Introduction

Many opinion articles on cryptocurrency read something along the lines of "cryptocurrencies use resources, and thus they are bad.” We have to start here–Bitcoin kicked off the start of a revolution that has permanently transformed finance, commerce, and society. If you read the [business whitepaper](https://www.chia.net/assets/Chia-Business-Whitepaper-2021-02-09-v1.0.pdf), Chia acknowledges the strengths of Bitcoin, and we have taken the best parts and improved them; notably the programming model and energy use. Cryptocurrency is all about tradeoffs between scalability, performance, power, decentralization, and security. Proof of Work (PoW) was a breakthrough in providing permissionless and decentralized coordination of network participants, but the economics have devolved into purpose-built hardware that consumes too much energy. Even with all the advancements in cryptocurrency technology in the past decade, PoW coins hold the top spot in market cap and global trust–they provide the highest level of decentralization and security. Can we have our cake and eat it too? Can Chia exceed the decentralization provided by PoW in a sustainable way? Don’t forget the Chialisp frosting on top, which provides secure smart contract capability built directly into the coins!

Proof of Space and Time maintains Nakamoto consensus (decentralized and permissionless) while massively reducing energy consumption. We are going to explore the economics of why storage is the perfect medium for network security.

## Summary / TL:DR

* Farming in Chia has much lower energy consumption than mining in Proof of Work, up to 500x lower annual energy consumption at current network size. [1] For similar upfront costs of equipment, farming consumes 14x lower power than state of the art Bitcoin mining equipment.
* The majority of costs in farming are the upfront costs of the storage device, whereas in mining the majority of the cost is ongoing electricity. [6][7]
  * Storage for farming can be resold and repurposed for data storage, with a liquid market for second-use storage. Farming is a lightweight workload and the perfect use case for used storage. The economics of farming will incentivize the shift of Netspace towards used drives.
* Storage is a mature market at $65B [3] and 1.5 Zettabytes shipped in 2021 alone, with an install base of over 6.7 ZB as of 2020 [5]. Much of this is underutilized and provides a perfect medium for blockchain security.
* Miners need to purchase new equipment to stay competitive with the average device lifespan being only [1.29 years [2]](https://doi.org/10.1016/j.resconrec.2021.105901), forcing inefficient single-purpose ASIC miners into e-waste (Bitcoin’s impact alone is estimated at 30.7 metric kilotons) [2].

## Proof of Space and Time

Chia uses the novel Proof of Space and Time for blockchain consensus. Participants of the network called farmers allocate their underutilized storage space to the network in a farming process. The naming of farming implies that it is much more environmentally friendly than mining. The Chia proof of space construction is designed for efficient and quick verification of proofs, making the farming process very lightweight. Farming is low resource use both from CPU on a host machine and the number of read requests to the underlying storage device used for storing the plots (farming) - HDDs being idle 99.7% of the time and only using 0.6 IOPS (input/output operations per second), and CPU utilization low enough even a Rasberry Pi can farm hundreds of terabytes of storage.

<p align="center">
<img src="/assets/blog/mining-vs-farming-2.png" alt="Mining vs Farming" width="75%">
</p>

#### Terminology

Mining is the exchange of labor and time for a physical resource, so it makes a perfect analogy for the process in Proof of Work, where miners continuously use massive amounts of electricity to compete for block rewards. Chia decided to pick entirely different terminology that better describes how the protocol operates. This may seem silly and gratuitous at first, but once you understand how different Chia is from every other cryptocurrency out there, it will start to make sense.

* **Plotting** - creating the proofs of space into a “plot file” requires upfront one-time use of compute resources, so that proofs can be quickly and easily verified later.
  * “Plant the seed”
* **Harvesting** - the harvesters are individual machines controlled by the farmer that continuously and unintrusively check the plot files for proofs of space.
  * “Continuous growth with low work”
* **Farming** - farmers compete to create blocks when a proof of space is found that meets the challenge requirements.
  * “Earn income by selling the crops”
* **Full node** - maintains an entire copy of the blockchain, propagates blocks, transactions, and proofs between peers.
  * “The delivery truck”

#### Mining Efficiency

Mining as a metaphor is spot on - mining in Proof of Work requires a large amount of continuous resource use in electricity and time in exchange for network rewards. Proof of Work mining has also consolidated on custom-designed hardware to maintain competitiveness. For example, in Bitcoin high-power ASICs (Application Specific Integrated Circuits) that only perform the SHA256 algorithm at terahashes per second. This leads to purpose-built hardware for Bitcoin that is obsolescent quickly with the average lifespan of Bitcoin mining devices at only 1.29 years [2].  Mining efficiency is driven by process technology for the ASIC, which is why a few year old miner isn’t competitive on the network with average power costs. The metric of goodness for mining is J/TH, or the amount of energy in joules consumed to perform 1 terahash

<iframe width="600" height="371" seamless frameborder="0" scrolling="no" src="https://docs.google.com/spreadsheets/d/e/2PACX-1vROlPqAQj_4YZZLqMnhBd1C9IqQQTC_mHChAkYIMfyb3mbp0087Byz2Uy9mRqdLvB25DC4EGewSPNRj/pubchart?oid=1015763769&amp;format=interactive"></iframe>

#### Farming Efficiency

Farming is very different. For one, farming uses commodity storage hardware, mostly larger capacity hard disk drives (HDD). Farming also does not store user data, so lower quality storage media with a higher error rate can be used. The first order metric in farming is $/TB of the storage device, followed by W/TB for power efficiency. The Netspace in an efficient market will likely come from both underutilized storage and reused/recycled, refurbished, and 2nd use drives because these are lower upfront costs. Hyperscalers and cloud service providers (e.g. Facebook, Microsoft, Amazon) strive to meet growing data demands and often replace hardware every 3-5 years. There is a large opportunity to use these drives in Chia farming!

<iframe width="600" height="371" seamless frameborder="0" scrolling="no" src="https://docs.google.com/spreadsheets/d/e/2PACX-1vROlPqAQj_4YZZLqMnhBd1C9IqQQTC_mHChAkYIMfyb3mbp0087Byz2Uy9mRqdLvB25DC4EGewSPNRj/pubchart?oid=974378048&amp;format=interactive"></iframe>

#### Can someone make an ASIC for Chia farming?!

There is already a large market for HDDs, with an estimated TAM (Total Available Market) over $20B and 1.2 Zettabytes [2]. Storage vendors pour billions of dollars into R&D every year to increase the areal density of HDDs and NAND flash. I can’t believe I have to write this, but we regularly get asked the question “won’t someone just make an ASIC for Chia?” These hyperscalers have been searching for the holy grail of archive storage called write once, read many (WORM) storage that is high-capacity, low-power, and low-cost. NAND flash has dramatically changed the storage landscape in the last 10 years by increasing areal density through 3D NAND and moving to store more bits per cell. We think it is unlikely that an unknown player in the space will invent a new class of archive class storage device that is purpose-built for Chia–but if they do, they could make a lot of money selling that same product to the hyperscalers!

## A note on Proof of Stake

This article focuses on the difference between mining in Proof of Work, with a case study on Bitcoin, vs. farming in Chia. PoS is touted as an energy-efficient alternative to Proof of Work (PoW). This is a much longer discussion, which we will cover in an additional post, but [Bram](https://youtu.be/2Zlcgt8FVz4?t=511) and the [Chia](https://www.chia.net/assets/Chia-Business-Whitepaper-2021-02-09-v1.0.pdf) team believe that PoS is a large step backward in the blockchain world. In PoS the rich get richer and promote centralization, while funds get consolidated to professional validators and exchanges. The “features” of bonding and slashing to fix the “nothing at stake” problem rely on massive amounts of [social coordination](https://eth.wiki/concepts/proof-of-stake-faqs) and [weak subjectivity](https://vitalik.ca/general/2020/11/06/pos2020.html). The possible grinding attacks that can be performed in PoS are prevented in Chia through the VDF (Verifiable Delay Function) via a “Chia Timelord”.

<p align="center">
<img src="/assets/blog/mining-vs-farming-3.png" alt="Mining vs Farming" width="75%">
</p>

## Mining power usage vs farming

The power consumption of Bitcoin is well researched. I cite [The Cambridge Bitcoin Electricity Consumption Index (CBECI)](https://cbeci.org/) and [Digiconomist](https://digiconomist.net/bitcoin-energy-consumption/) for the comparison I did at [Chiapower.org](https://chiapower.org/).

<iframe width="600" height="371" seamless frameborder="0" scrolling="no" src="https://docs.google.com/spreadsheets/d/e/2PACX-1vQTo_q1WX68ONeRJZuHsdueYfgv71o3qmrXCwNQ-UScBSmLuHI781iRMXpsVntueyI2-DpS_PHpK6oK/pubchart?oid=1357003038&amp;format=interactive"></iframe>

Source: [Chiapower.org](https://chiapower.org/) model, [Digiconomist](https://digiconomist.net/)

Of course, I will urge anyone who wants to understand the methodology to read the site, but you can see even today Chia consumes up to 500 times less power than Bitcoin, and 200 times less than Ethereum.

In a much smaller example, we can explore the upfront cost (Capital Expenditure) vs. power consumption of a similar amount of investment. With $10k of equipment Bitcoin miners consume 14x the power compared to equivalent farming equipment. Bitcoin earns more per day but requires a tremendous amount more in electricity costs compared to a similar investment in Chia.

$10,000 spent on a single state of the art Bitcoin miner vs. 360TB of Hard Disk Drives and JBOD (just a bunch of disks) to hold and power on the drives

Earnings updated 10/19/2021, you can use [Nicehash calculator](https://www.nicehash.com/profitability-calculator/) or [Bitcoin TCO model](https://docs.google.com/spreadsheets/d/1fDCbrj9zALoKnpjX98I5L7Bz5TmOWKPyrLmdiPCVApY/edit?usp=sharing) and [Chiacalculator.com](https://chiacalculator.com/) for up to date estimates based on hashrate, Netspace, and price

|Equipment|Quantity|Cost|Power (W)|Earnings/day|Power Cost/Day|
|:---:|:---:|:---:|:---:|:---:|:---:|
|Antminer S19j Pro|1|$10,000|3050 W|$39.86|$4.47|
|WD HC550 18TB|20|$450 x20|123 W|$12.16|$0.25|
|18TB JBOD|1|$1000|100 W| | |

<br />

<p align="center">
<img src="/assets/blog/mining-vs-farming-4.png" alt="Mining vs Farming" width="40%">
<img src="/assets/blog/mining-vs-farming-5.png" alt="Mining vs Farming" width="40%">
</p>

## Are the hard drives used for Chia wasteful?

The Chia Netspace is an interesting beast. We saw earlier in the year that when farmers can get a high return on their investment in a short amount of time, they will rush out to buy new hardware. With the costs in Chia farming being dominated by the upfront costs of the disks rather than energy use, game theory would suggest that farmers seek out a competitive edge by using underutilized storage or second use storage that has a lower upfront cost. Over time, as the Netspace grows, this may be very apparent and may price out newly purchased hardware from being competitive. As the Netspace grows, work difficulty increases, and farming rewards go down proportionally. We are trying to incentivize farmers to use what they already have for farming and seek out used and recycled gear for plotting and farming. The mix of the Netspace from newly purchased capacity and underutilized space will be dependent on rapid Chia price increases and areal density growth of hard drives in the next decade (providing better power efficiency). Our prediction is that it will start gravitating towards underutilized and second-use storage (used).

<iframe width="600" height="371" seamless frameborder="0" scrolling="no" src="https://docs.google.com/spreadsheets/d/e/2PACX-1vRh6I5L-j9qQ0blgTSf1VGCyAlns6DdkftRwisROafy8nh-7qxZ3iAd8XJh-buiIw/pubchart?oid=1904247403&amp;format=interactive"></iframe>

## What about plotting?

Even though plotting requires compute, memory, temporary storage (SSD) and energy - it only has to be done once before the plot file is copied over to a hard drive (HDD) for farming. We addressed the concerns of Chia prematurely wearing out SSDs in a [blog post here](https://www.chia.net/2021/08/03/chia-and-ssd-endurance-big-progress-less-waste.html), but the biggest takeaway from it is this:

**Chia does not require ritual sacrifice of SSDs to create plots.**

Plots can be created using only HDD, it can be done completely in memory, using data center SSDs with high endurance that can last over 10 years in plotting, and new high TBW high-end consumer SSDs provide virtually unlimited plotting.

I made a conservative model for e-waste in Chia, using the full weight of the SSDs and estimated wearout based on a distribution of farmers assuming 50% of the Netspace was plotted with cheap consumer NVMe (which I do not actually believe...being conservative)

|Cryptocurrency|Bitcoin|Chia|
|:---:|:---:|:---:|
|e-waste metric Kilotons||30.7 [2]||0.0015 [7]|

<br />

In a relatively worst-case scenario, Chia would create 0.0015 metric kilotons of e-waste, or 20,000 times less than the estimated e-waste for Bitcoin.

## Total Cost of Ownership for mining vs. farming

Total cost of ownership (TCO) models are widely used in the data center world to make purchasing decisions, breaking up costs into capital expenditures (CapEx) of IT equipment and data center costs, and operational expenditures (OpEx) for recurring data centers costs, such as power and cooling. We recently published a user-friendly version of the Chia TCO model as part of the [https://chiacalculator.com/roi](https://chiacalculator.com/roi). A TCO model is how most data center operators, including miners and farmers, make decisions about profitability. I have developed a model for Bitcoin similar to the methodology I used for the Chia version, which is a forward-looking model to project the costs (which can be modeled accurately) and the return (which requires forecasting on future price, hashrate in Bitcoin, and Netspace in Chia). For the sake of simplicity, we just model with the current price and network sizes.

#### Bitcoin 3 year TCO

You can see if you buy new efficient Bitcoin mining hardware, CapEx is two-thirds of the TCO, and OpEx is the remaining third. With hardware that is a few years old, and reselling on eBay for much lower than its original price, OpEx costs make up the majority of the TCO. With power making up the majority of costs for Bitcoin miners, the competitive edge comes from the availability of the latest and most efficient miners paired with low electricity costs. Bitcoin miners are in search for [renewable](https://nydig.com/wp-content/uploads/2021/09/NYDIG-Bitcoin-Net-Zero.pdf) and cheap energy (which is a good thing), but the incentivization is heavily dependent on [local policies](https://niccarter.info/wp-content/uploads/txsummit_nc_oct08.pdf). A lot of the estimations on renewable energy use need to be updated after the major policy changes in China, where the majority of mining was prior to mid 2021. The [Digiconomist](https://digiconomist.net/bitcoin-energy-consumption) models this using a break-even efficiency in J/TH which sets the threshold of mining equipment that can profitably mine bitcoin given a current hashrate and Bitcoin price - concluding that old miners quickly become inefficient and uncompetitive.

<iframe width="573" height="355" seamless frameborder="0" scrolling="no" src="https://docs.google.com/spreadsheets/d/e/2PACX-1vROlPqAQj_4YZZLqMnhBd1C9IqQQTC_mHChAkYIMfyb3mbp0087Byz2Uy9mRqdLvB25DC4EGewSPNRj/pubchart?oid=1317699788&amp;format=interactive"></iframe>

#### Chia 3 year TCO

Chia is exactly the opposite of Bitcoin. The majority of the costs in farming Chia come from the upfront investment in the storage. With 18TB HDDs, which are the highest capacity drives shipping in volume today, you can see the CapEx in a 3 year TCO makes up 96% of the TCO!

**When using high capacity hard drives, power is a fraction of the cost for Chia farming compared to the cost of the storage**

Even 4TB HDDs (which were mainstream in 2013) can be profitable farming Chia, but it does increase the OpEx because older drives are less power efficient per TB. The constants for electricity cost and PUE are set to be consistent with state-of-the-art Bitcoin mining operations, which I think is much lower than what typical data centers operate at. This presents and opportunity similar to Bitcoin where farmers with access to older low cost storage and competitive electricity prices can profitably farm Chia.

In Chia, farming hardware can be safely resold if the farmer decides they no longer wish to participate in the Chia Network. This has a massive impact on the residual value of the CapEx spent on farming hardware. If a farmer wants to participate in the network and buys new storage to do this, the efficiency breakeven for the network for electricity and OpEx is very low. This is one of the reasons we don’t see a large decline in Netspace when Chia price goes down, because farmers have already spent the resources to obtain and plot the drives.

<iframe width="741" height="347" seamless frameborder="0" scrolling="no" src="https://docs.google.com/spreadsheets/d/e/2PACX-1vTRlxtBBNRZsx3hwkwLVhKzlAJp233Bhz5IkgLyksIacrEhZAnrW9JYODkdVekXHQ/pubchart?oid=2008163833&amp;format=interactive"></iframe>

## Summary
There are a lot of similarities between Chia and Bitcoin, as Bram has been very open about taking the great parts of Bitcoin and building on them in Chia. Netspace is very similar to hashrate in Bitcoin, but the fact that Chia uses storage to secure the network creates very interesting properties. Storage is already a large and mature market; it makes the perfect medium to leverage underutilized resources for network security. Storage devices are power efficient compared to GPUs, CPUs, and ASIC for mining other cryptocurrencies and consume a fraction of the energy, with Chia today consuming 500 times less electricity than Bitcoin at a higher node count and decentralization. ASIC for PoW mining creates a massive amount of e-waste, where Chia can promote reuse of storage for farming. Even at today’s Chia price, at a very tiny fraction of the market capitalization of Bitcoin, farming remains profitable vs Bitcoin mining while being much more accessible (people can start farming with a single 108GB plot on their current laptop or desktop, while Bitcoin mining requires investment in custom hardware).


##### References
1. Chiapower.org estimate
2. de Vries, A. and Stoll, C., 2021. [Bitcoin's growing e-waste problem](https://doi.org/10.1016/j.resconrec.2021.105901). Resources, Conservation and Recycling, 175, p.105901.
3. IDC Worldwide Hard Disk Drive Forecast Update, 2020–2024, Dec 2020
4. IDC Worldwide Solid State Drive Forecast Update, 2020–2024. Dec 2020
5. IDC Worldwide Global DataSphere Volume of Data Analyzed and Fed into AI Forecast, 2021–2025
6. [Bitcoin TCO model](https://docs.google.com/spreadsheets/d/1fDCbrj9zALoKnpjX98I5L7Bz5TmOWKPyrLmdiPCVApY/edit?usp=sharing) by JM Hands
7. [Chia TCO model](https://docs.google.com/spreadsheets/d/1i_4MHrCan0lolTdpnJCmFVSdfNP0VugD/edit?usp=sharing&ouid=108662600751303250659&rtpof=true&sd=true) by JM Hands
