---
lang: en
layout: post
title:  "Pooling Protocol Testing Entering Phase 2"
date:   2021-06-30
author: "[Gene Hoffman](https://twitter.com/hoffmang) and [Bram Cohen](https://twitter.com/bramcohen)"
---

Today we are entering the [second phase](https://www.chia.net/assets/presentations/2021-06-02_Pooling_for_Pool_Operators.pdf#13) of our testing and roll out of the official pooling protocol. ***This phase is for pooling operators to test the pooling protocol end to end with testnet bound portable pool plots.*** Over 9000 lines of new code - much of which is Chialisp - have been written by the team since transaction launch on 5/3 to implement what we think will be the best pooling protocol for a blockchain project to date.

Pool operators and those curious about how the pooling protocol works can find the reference pool operating code in the [pool-reference](https://github.com/Chia-Network/pool-reference) GitHub repository. The correct branch for testing is [pools.testnet9](https://github.com/Chia-Network/chia-blockchain/tree/pools.testnet9). Our original plan projected that we would leave three days for pool operators to test this pre-release version. However, with the holiday weekend in the United States, we expect that a full release of what will be version 1.2.0 of Chia will happen during the week of July 5 at the soonest. However, this testing phase may still find issues so there are no guarantees of which day 1.2.0 will be released for mainnet portable pooling plots. This also gives time for the operators of pools to be in position to accept new pool members after the release of 1.2.0.

There is still an up to 25% chance that we will have to make breaking changes to the plot NFT that would require replotting any portable pooling plot made with the current pre-release. We strongly advise farmers to wait for the actual 1.2.0 release before plotting any plots they intend to keep. Portable pooling plots made on testnet will not work on mainnet as a particular plot NFT is tied to the network it is created on.

To answer a frequently asked concern - your existing or "OG" plots do not require re-plotting and can continue to be self farmed and self farmed in parallel with the new portable pool plots once released. Only the creation of portable pool plots will require plotting.
