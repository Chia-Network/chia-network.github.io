---
lang: en
layout: post
title:  "Official Pooling Protocol Launched"
date:   2021-07-07
author: "[Bram Cohen](https://twitter.com/bramcohen)"
---

**TL;DR:** The new plot format has arrived. Upgrade to version 1.2.0 of the Chia Blockchain software to start plotting for pools now and be sure to set up a Plot NFT before doing so. Original plots will continue to be self-farmable but can not be safely used in pools.

---

Less than 3 months ago the very first chia transaction happened. In the following days we got a real coin price which came in a lot higher than expected. While this was a bonanza for everyone who got in on farming early, it led to an explosion in netspace from about 100 pebibytes at launch to over 30 exbibytes today.

We immediately got to work after transaction launch implementing a standard secure pooling protocol according to the plan outlined in [this earlier post](https://www.chia.net/2020/11/10/pools-in-chia.html). This has been on an extremely accelerated schedule and we prioritized portable pools over static ones because of overwhelming demand. The team has written and tested over nine thousand lines of code, and they’re now ready for the public to use. You can start making pool-enabled plots now even before selecting which pool you want to start with - or even deciding you want to use one. The pooling protocol has several important features which aim to make Chia the most decentralized cryptocurrency in the world.

With the portable pooling protocol, you can switch between pools and even go back to self-pooling (aka not being in a pool at all) whenever you want. The worst a pool can do is stiff you of the rewards you should be getting from them, and you can audit whether they’re doing that yourself. They can’t keep you from leaving.

On the flip side, pools are guaranteed to be able to collect any block rewards which someone currently farming with them finds. There’s a reasonable split of that reward to farmers to incentivize them to claim the reward when they find it. Double farming is impossible, and there’s no need for pools to vet farmers who wish to pool with them. Pools can allow farmers to join and leave whenever they choose, and pools compete based on fees and service. We’ve even put in hooks to make sure that if any other cryptocurrencies want to switch to proofs of space and time based off the existing Chia portable pool plots they’ll be able to keep pool functionality, but please make sure to upgrade to the latest plotting software to make sure this feature will work for you.

Portable pool functionality is built entirely on the base chia programming environment, hasn’t required any forks to get working, and makes farmers rather than pools make the blocks which is a big boon for security and decentralization. Even if a cabal of pools were to get over 51% of netspace, they couldn’t pull off a 51% attack on the network unless enough of their farmers wanted to participate in the attack as well. No security deposits or minimum balances are required for participating, a user can make plots and start getting paid out almost immediately.

Existing plots which don’t use portable pools will continue to work fine. If you wish to switch an existing farm to pooling, you can redo one plot at a time while leaving the old ones running. If you have a large enough farm that you get frequent rewards, we recommend that you not use a pool at all. There are almost 5000 reward events per day, so anyone who has a five thousandth of the total netspace will get about one reward per day on average, which results in not much variance over the course of months. Due to the overwhelming popularity of Chia farming, a five thousandth of netspace is still a lot, but it’s meaningfully lower than the equivalent proportion of space in Bitcoin–both for being able to self-pool and for a pool to hit a big enough size to be viable.

To learn more about how to plot and farm portable pool plots check out our [Pooling User Guide](https://github.com/Chia-Network/chia-blockchain/wiki/Pooling-User-Guide). For more details about how our pooling protocol works you can review our [reference implementation for pool operators](https://github.com/Chia-Network/pool-reference).
