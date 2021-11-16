---
lang: en
layout: post
title: "The CAT's Out Of The Bag: Chia Releases the CAT1 Standard"
date: 2021-11-15
author: 
- "[Matt Howard](https://github.com/matt-o-how)"
- "[Matt Hauff](https://github.com/quexington)"
- "[Dan Perry](https://github.com/danieljperry)"
---

<p align="center"><img src="/assets/blog/cats.jpg" alt="Chia Pets" width="75%"></p>

<p style="text-align: center;"><em>A selection of Chia employees’ cats (not to be confused with CATs)</em></p>

We're excited to announce the release of the [CAT1 Standard](https://chialisp.com/docs/puzzles/cats "CAT1 Standard Documentation"). This marks the addition of a powerful set of new features to Chia's ecosystem. We can't wait to see the creative breeds of CATs our community comes up with!


## What Are CATs?

**C**hia **A**sset **T**okens are _fungible_ tokens that are minted from XCH and live on Chia's blockchain. CATs have the property of being "marked" in a way that makes them unusable as regular XCH. However, it is often possible to "retire" CATs, which then "melt" back into XCH.

>**Reminder**
>
>>**Fungible tokens** can be split apart, or merged together. They can also be substituted for a token of equal value. Some common examples include gold, oil, and dollars.
>
>>**Non-fungible tokens**, on the other hand, are indivisible and cannot be merged. They are unique, so they cannot be substituted. Some common examples include cars, baseball cards, and cloakroom tickets.

If you're finding it difficult to visualize the process of minting and retiring CATs, it might help to think in terms of copper and pennies:

* In the real world, if you have a sheet of copper, you can mint pennies. The face value of the pennies is not directly linked to the value of the copper they are made from. In Chia, if you have a bit of XCH, you can mint CATs. The value of the CATs is not directly linked to the value of the XCH they are made from.
* In the real world, it's possible melt pennies into raw copper. In Chia, it's possible to retire your CATs, which melt into XCH. 

(Obviously you aren't allowed to mint your own pennies, or even to melt them. This is just an analogy.)

Any CATs you create are required to follow whatever rules you put into place. You have total creative control over how these assets are minted and retired.

A few use cases for CATS are:
* Stablecoins
* Stock issuance
* Voting shares


## What distinguishes one CAT from another?

All CATs share the same [base code](https://github.com/Chia-Network/chia-blockchain/blob/protocol_and_cats_rebased/chia/wallet/puzzles/cat.clvm "cat.clvm -- the Chialisp puzzle that all CATs share"), written in Chialisp. However, they are bound by different rules of issuance, which are created in a second Chialisp program that follows a specific structure.

We call this issuance program the -- wait for it -- **T**oken and **A**sset **I**ssuance **L**imiter. Yes, it's a **TAIL**.

TAILs are the only thing that distinguishes one CAT from another. In other words, if two CATs use the same TAIL, they are of the same type. The TAIL defines the CAT.

## What functionality can a TAIL have?

TAILs are required to have certain arguments passed to them, but otherwise, they can have as much, or little, functionality as desired. The TAIL's primary purpose is to check that all of the CAT's supply rules were followed. It has the freedom to add more conditions, to invalidate the whole spend, and even to create new coins!

Different tokens can have vastly different issuance and melting requirements, which are entirely up to the CAT's creator. Let's look at a few examples:

* Stablecoins - The creator will want to issue new tokens as they gain funds to back them.
* Limited supply tokens - The creator will want to run a single minting, with the guarantee that no more tokens of the same type can ever be minted.
* Asset redemption tokens - The creator will want to allow the CAT's owners to retire the tokens into standard XCH, as long as they follow certain rules.

In each of these cases, the TAIL will be run when a coin is spent, giving its creator control over the asset's minting and melting. The TAIL can also be dependent on other coins on Chia's blockchain, such as Decentralized Identifiers (DIDs). This allows for enormous functionality and compatibility between CATs. It even opens the door to _decentralized issuance_. In other words, a TAIL could be designed to allow anyone to securely mint new coins.


## Are TAILs all-powerful?

No. Given the functionality listed above, you might think that TAILs can do anything. However, there is one important limitation to their power. Only the CAT's _owner_ can run the TAIL, so the CAT's _creator_ cannot freeze or confiscate funds without the owner's permission. This means that the TAIL's power is limited to minting and melting.

You -- and only you -- have access to your own CATs.


## Where can I learn more?

* For more non-technical details, check out our [FAQs](https://chialisp.com/docs/faq "Feline Asked Questions (FAQs)").
* Bram has put together a [glossary of CAT1 terms](https://www.chia.net/2021/09/23/chia-token-standard-naming.en.html "Chia Token Standard Naming") on our blog.
* For a technical deep-dive into how CATs and TAILs work, check out our [CAT1 Standard](https://chialisp.com/docs/puzzles/cats "CAT1 Standard Documentation").
* And we have a tutorial to help you create your own CATs, for users of [Windows](https://chialisp.com/docs/tutorials/CAT_Launch_Process_Windows "Cat creation tutorial for Windows users") and [Linux/MacOs](https://chialisp.com/docs/tutorials/CAT_Launch_Process_Linux_MacOS "Cat creation tutorial for Windows users").

If you have questions about CATs, head over to the #chialisp channel on our [Keybase](https://keybase.io/team/chia_network.public "Chia's Keybase forum") forum.

We hope you find these new features _the cat's meow_. Happy minting!
