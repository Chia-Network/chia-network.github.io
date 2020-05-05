---
lang: en
layout: post
title:  "Launching Coloured Coins"
date:   2020-04-29
author: "[Bram Cohen](https://twitter.com/bramcohen)"
---

Blockchains should make issuing and using coins and assets easier and more trustworthy than in the analog world, but so far the functionality they provide is limited and hacked on awkwardly.

Today we debut one of Chialisp's most powerful smart transactions - Coloured coins.

Coloured coins are generally known for what they do, which is token issuances of
alternate coins, assets, and stable coins. Their current most common implementations are Omni protocol on Bitcoin and ERC-20 on Ethereum. The usage of those protocols makes up the vast majority of all smart transaction functionality used in cryptocurrencies today.

Both Omni and ERC-20 have problems in their basic functionality. We're releasing an initial implementation today that demonstrates not only fixes for those problems but exciting, truly decentralized exchange functionality on top of it.

A Coloured coin should be easy to use with a lightweight wallet on your phone and without requiring a trusted full node. Coloured coins shouldn’t have to implement a precise specification which must be enforced by the blockchain absolutely perfectly. It also should support inner smart transactions, where smart transaction functionality such as vaults and payment channels can be implemented in the Coloured coin making full use of the on-chain programming environment. Omni fails on the first of those and ERC-20 on the second.

Chia Coloured coins not only support all of this but offer new functionality that
someone can make an unfinished transaction called an 'offer.' You can simultaneously create
some Coloured coin out of nothing and burn some Chia (or vice versa) and this offer
can be distributed to others. Anyone in the universe that finds or sees an offer can make a transaction which finishes the other side. That paired transaction will be a valid transaction that can be introduced to the blockchain and it will go through. It's also possible to have much more complex offers involving multiple colours and to match chains of offers. As long as the sum totals work in the end, it's all valid.

Coloured coin offers allow a stable coin issuer to ship an app that would let an end user use their stable coin, pay transaction fees in their coin, and basically never know that this all occurred on the Chia blockchain. Inner smart transaction support means that that issuer can create a stable coin wallet that can only spend 100 coins every 24 hours or only send coins to designated payees or can claw back a transaction for the next 3 blocks to fix a typo. You can have this level of token functionality on top of what we expect will be one of the most distributed and secure validation networks ever.

All of this is extremely lightweight. You can simply create a new token and play with it. The on-chain programming environment which enables this is much simpler and more straightforward than the ones in Bitcoin or Ethereum. An environment that is able to self-referentially
talk about itself enables all the functionality you need. New variants and added
Coloured coin functionality can be built with no need to add functionality to our general
purpose environment.

In the future we'll add lots of polish to both our Coloured coin implementation
and our testnet on chain programming environment culminating in the launch of our mainnet
later this year. Mainnet is the point at which Chia will be ready for production use
involving real money. Chialisp and Coloured coins you create today are going to require very little modification to run on mainnet after launch.

Try them out in [Beta 1.4 now](https://github.com/Chia-Network/chia-blockchain).
