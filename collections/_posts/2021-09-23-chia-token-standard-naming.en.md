---
lang: en
layout: post
title:  "Chia Token Standard Naming"
date:   2021-09-23
author: "[Bram Cohen](https://twitter.com/bramcohen)"
---

## TL;DR: The Chia token standard is going to be called CAT1

We’re in the process of making a real standard for tokens which will guarantee interoperability for developers who follow it, and it needs a name. In the past we’ve used the term ‘coloured coins’ in our documentation and code to refer to tokens built on top of Chia. This has the disadvantage that it’s an esoteric bit of jargon, refers to a general concept rather than our specific implementation, and ‘coloured’ is a loaded term in many parts of the world.

We have now spent millions of dollars with a brand marketing firm, gone through extensive creative processes and… nah just kidding, I did some research, ran a few surveys through our employees and made a decision. Here’s the new glossary:

## Glossary

_asset_ - a thing which can be owned. Most assets in the world have nothing to do with Chia.

_token_ - a representation of an underlying asset, including in this case a set of coins on a chain

_asset token_ - a divisible and fungible token, as opposed to a non-fungible token (NFT) which is less featureful

_coin_ - a thing which exists on the Chia blockchain, analogous to a UTXO in Bitcoin

_token coin_ - a coin which represents an underlying asset. In Chia the identity of coins changes even as the capability of being the underlying asset keeps getting passed between them

_asset coin_ - a coin which specifically represents an asset token as opposed to a non-fungible token, or NFT 

_NFT coin_ - a coin represents an NFT. It usually has a parent which was the same NFT and a child which is also the same NFT.

_CAT1_ - the first Chia Asset Token standard. We may make a CAT2 in the future but it will be a while, if ever.

_CAT_ - A Catch-all term for CAT1, CAT1.1 or CAT2 or possibly some other CAT standard in the future.

_CAT1_ token - a token which followers the CAT1 standard in its implementation

_CAT token_ - a term which doesn’t specify which CAT standard is being followed. Also used if you’re being more informal or are just too lazy to type the 1. If you’re being really informal or lazy you can use the lowercase cat. You can also just call it a CAT since ‘CAT token’ is short for ‘chia asset token token’ which is valid but sounds weird.

_CAT coin_ - a single coin which is part of a CAT token

_X_ -  a hypothetical name of a CAT token

_X coin_ - a coin which specifically represents part of the token X. Multiple X coins can be called a litter.
