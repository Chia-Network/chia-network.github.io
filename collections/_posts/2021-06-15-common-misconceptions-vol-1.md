---
lang: en
layout: post
title:  "Common Misconceptions, Vol. 1"
date:   2021-06-15
author: "[J. Eckert](https://twitter.com/sargonas) and [Roy Natian](https://www.linkedin.com/in/roynatian)"
---

Chia is a complex system. There is a lot of nuance and technicalities involved in understanding how all the components of Chia work together. Over the last several weeks we’ve seen several misconceptions floating around on social media and [Keybase](https://keybase.io/team/chia_network.public) regarding how Chia works.

We have compiled the most common misconceptions and questions with responses below.

Also, don’t forget to join us **today**, Tuesday, June 15 for an AMA on plotting speed and security with Bram, Gene, and the team.

**Chia Livestream: Plotting speed and security in Chia**
When: Jun 15, 2021 05:00 PM Pacific Time (12:00am UTC)
Where: [Zoom](https://chia-net.zoom.us/j/89843076167) or [Youtube](https://www.youtube.com/channel/UChFkJ3OAUvnHZdiQISWdWPA)

## Common Misconceptions and Questions

**hpool can conduct a 51% attack**

No, they're too small for that. At the time of writing, [going by blocks won](https://www.chiaexplorer.com/charts/topFarmers), they're currently hovering at around 33% of netspace. The numbers on their website disagree, but those likely include netspace reported by dishonest farmers—a problem that is specific to hpool and their custom pool protocol. Double-farmed net space does not win blocks, and in fact, does not even enter the Chia netspace calculation.

---

**A sufficiently large pool can conduct a 51% attack**

Not really, unless they manage to convince 51% of netspace to use a custom client that they can remote-control.

Traditionally in crypto there have been "hash pools" where miners receive work to process and submit results so the pool can create a winning block by combining all the miner's efforts. A network using pooling like this is highly susceptible to 51% attacks when a pool has 51% of the network (or coordinates with other hash pools) because the pool is the single source of data flowing into the blockchain. Chia changes this system by having individual farmers create the winning blocks alone, and uses "reward pools" to share coins among fellow participants of it, reducing the risk dramatically as a pool will have to coordinate (as in seize direct control) of hundreds of thousands of individual farmers within the pool, rather than just modify the output of the pool itself.

Long story short: Chia is different, and pools can't do a classic 51% attack. Traditional crypto pools control the entire pool's block response (and can modify it for personal gain if it has 51%). In a Chia pool, the individual farmers contribute the block themselves without interference from the pool, and every farmer in the pool would need to agree with the pool's rogue actions if it had 51%.

---

**The prefarm means Chia plans to rugpull at some point**

If Bram Cohen had wanted to do a rug pull, he would have led with an (illegal) ICO and walked away years ago with millions or even billions without the hard work of the last three years. Instead, he invented & co-invented several new types of math, [co-authored a paper in a peer-reviewed journal](https://link.springer.com/chapter/10.1007/978-3-319-70697-9_13), brought together a diverse team, and gained the confidence of globally respected investment firms. He is now just a minority owner of Chia Network, having given up 70% of that potential ICO profit to instead focus on the opportunity to change the world as part of something larger than himself.

---

**Chia is designed to kill NVMe drives**

[No](https://twitter.com/bramcohen/status/1393991791590838277). If you use the wrong tool for the job, the job may destroy that tool. This is to say, using some types of consumer NVMe SSD may result in those devices failing because of the high number of writes involved in the Chia plotting process. There will be some TBW wear on any NVMe drive used for Chia plotting, this does not mean all drives used for Chia plotting will fail. It is not recommended users purchase consumer NVMe drives for the purpose of Chia plotting. It is certainly not an intentional Chia feature that some consumer NVMe drives fail from Chia plotting. We do hope that farmers are using second-hand or already owned hardware whenever possible to make their Chia farm as green as possible.

Also, plotting on HDDs is slower but possible (and a lot of work went into ensuring that the stock plotter supports this). Alternative plotters again may be much lighter on writes, at the cost of higher RAM usage.

You can learn more here: [Chia and SSD Endurance](https://www.chia.net/2021/05/24/SSD-endurance.html)

---

**Is Chia really Green? You still use energy – and what about the e-waste?**

Chia is committed to being a truly sustainable digital currency. Not just less bad. Proof-of-Work was an amazing innovation but unforeseen challenges led to extremely high energy wastefulness and diminished decentralization. Bram recognized a need to conceive an evolved Nakamoto Consensus that is truly decentralized and not inherently wasteful and energy inefficient while retaining the network security of Proof-of-Work and improving on the programmability of Ethereum. Chia’s energy use is approximately 0.1% - 0.3% that of cryptocurrencies that rely on Proof of Work.  While other cryptocurrencies may deploy Proof of Stake to reduce energy consumption, those systems will not be able to assure the same network security or deliver on decentralization.  

We take our responsibility to the planet and society very seriously, and when Chia identified the risk of additional e-waste, we took immediate action.  Although spent NVMes is not an issue (see above), Chia will soon announce a partnership with top industry data center and storage companies to stop the current practice of shredding hard drives so they can be refurbished and have a second life once they are no longer dependable to store data.  We are confident this will reduce global e-waste dramatically and hope to make further announcements in the coming weeks.

---

**k33 plots are better than k32 plots**

There truly is no difference between k32, k33, and kXX plots aside from the fact that the larger numbered plots are, indeed, larger in size, and take orders of magnitude longer to make. Beyond that, you are not improving your chances in ANY way by plotting larger files than k32. We promise. (The only reason to look at larger plots at this time is a strategic use of them allows you to min-max drive usage and not leave <101GB unused per drive if you Tetris things right.)

Another way to think about it: a single k33 takes up twice the space of a single k32, but k33's are not denser in any way.

---

**`chia plots check` decides your plotfile qualities (sometimes called unlucky plots)**

The `chia plots check` CLI utility is a tool for detecting plot files containing bad data that will fail to farm. It is sending out a static challenge, with a diff fitting the kXX size of the plotfile, so that it, on average, should return `-n` proofs. It does not, in any way, indicate if a plot is more likely to win against the random challenges created on the network during normal operations. This check does not mean that they are then worse or better against other, real-world challenges. It is merely a tool to detect plots that are either unable to be harvested at all, or are returning proofs far outside the expected norm due to an error in generation.

---

**My node is synced, but my wallet is showing 0**

The wallet and the full node each have their own sqlite database file.  The full node contains the blockchain itself, and the wallet contains transactions important to your receive addresses. You have to have both the Full Node in sync, as well as the Wallet in sync, to see the current balance of your wallet.

---

**"Reported" netspace by Chia can't be trusted**

It's commonly argued that "Chia Network 'claims' the netspace is size X" or that the netspace is somehow a fabrication of marketing hype on Chia Network's part. It's important to note that the reported estimated size of the netspace is calculated by the software itself, using formulas and metrics that are openly documented in the open-source project in GitHub. No one person or entity is responsible for "claiming" the netspace size is X, it's simply math that is based on the current blockchain state, using algorithms that make estimates based on activity. Yes, it can be off by a percentage depending on the current network state, but never by a material amount, and it self-corrects regularly.

It's also important to note that blockchain explorers often use a different formula than the one in the Chia GUI to calculate netspace.

---

**Chia farming and holdings are dominated by one country**

60% of the world's population is in Asia, 10% of the population is in Europe, and 5% is in North America. It's simply a normal thing that the dispersion of any Blockchain network that exceeds critical mass is going to be a microcosm of normal world population expectations. The breakdown with any one region or country that has a disproportionate size of population is always going to be mirrored in a network of this size. To expect otherwise is simply unreasonable, because at the end of the day the global population is not remotely evenly distributed.

That said, based on traffic data, Chia is bigger in the US and Russia than in China.

---

**Lambo when?**

There is no "Lambo when?", it's "Tesla Roadster when?"... this is why you are disappointed, you're expecting the wrong car! 😉

---

**Is Bram okay?**

Bram is very open about his neurodivergence and being "on the spectrum", and aspects of that will result in behavioral tics that otherwise might seem out of place to a neurotypical person. Fact of the matter is, people like Bram simply communicate and interact with others a bit differently from you or I... so please stop accusing him of being on drugs just because he blinks more than you do, or stares off into space while formulating an answer.

There are far more people out there who are much more self-conscious about being on the spectrum than Bram is. When they see people react like this to his mannerisms, it undoes the work people like him do who openly embrace it, and can make those people feel insecure and self-conscious about themselves and their ability to "fit in" to the incorrect expectations these kinds of comments set.

---

**Chia is a bad clone of burst**

This is just a dismissive comment anyone can do for low effort. If you have read far enough along to get to THIS particular FAQ, you know enough to understand Chia and Burst have nothing in common beyond the fact they both use Storage and not PoW. One of the key differences is that Burst is not safe from Hellman Time-Space tradeoffs, and the optimal way to mine Burst is to add GPU Proof of Work to one's Burst storage.

---

**Chia is all whales, and only profitable for whales. Whales are going to take all the rewards**

Chia is designed around making spare space farming possible and profitable - as long as that is the case, whales are competing against farmers who have next to zero cost, and the whales' benefits to scale won't be enough to overcome that. So in the long run, the whales lose.

Also, even now there has never been a cryptocurrency with as many active nodes as Chia. As we approach 1,000,000 nodes, it is vital to keep in mind that 100,000 new users each adding only 50 TB each to netspace is 5 EB of new space added to the network.

---

### Acknowledgments
A big thank you to Justin England, Gene Hoffman, JM Hands, Shane Larsen, Chris Marslender, and @beechord, @efishcent, @pyl, @morebytes, @psydafke on Keybase for their contributions.
