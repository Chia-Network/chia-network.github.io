---
lang: en
layout: post
title:  "Building a Sustainable Blockchain, With Your Help"
date:   2019-03-25
author: "[Ali Shadle](https://twitter.com/AliShadle)"
---

Decentralized, digital currencies will soon evolve from being a futuristic concept to a mainstream reality. They’ll offer liquidity to those who live in countries with poorly run or corrupt central banks, and offer a universal currency for streamlined financial transfers. Currency not tied to the banking system is an idea whose time has come.

But like any new technology, digital coins bring new complications. The biggest thorn in this new wave of digital money? Sustainability.

Most digital currencies, including bitcoin, are created by solving “proofs-of-work,” which means
servers working at full capacity to solve complex equations. This “mining” process consumes vast amounts of energy, and is not ecologically sustainable.

Creating digital coins has so far involved a trade-off: We can solve many of the world’s liquidity problems, but only if we harm the planet to do so. But we don’t need to accept a trade-off like this anymore, because there are better ways to create digital currency. We don’t have to mine coins with energy-guzzling equipment, because we can create, or “farm,” them with a method that’s secure, broadly distributed and environmentally friendly.

#### Proofs of Space and Time


Digital coins are created via consensus, a mechanism that is used in blockchain systems to achieve agreement on a single data value among distributed processes or systems. With bitcoin and other digital coins, this consensus is reached by solving equations known as proofs-of-work.

Proofs-of-work rely on computing power, which means the mining operations that rely on these proofs are draining energy at an alarming rate. At the same time, miners are forming pools, which is bringing a sort of centralization to a world that purports to be decentralized.

Proofs-of-space and time—the method we are pioneering at Chia Network—don’t rely on computing power but on available disk space. This means creating coins doesn’t require energy. With Chia’s system, miners allocate unused disk space to the network, and the probability of successfully “farming” a digital coin being proportional to the amount of space allocated divided by the total capacity of the network.

The proofs-of-space and time are also resistant to centralization or mining pools, which delivers on the early promises of digital currencies: that they remain decentralized.

#### How We Innovate with VDFs


Chia's consensus algorithm, which is necessary in the creation of new coins, relies on cryptographic protocols called Verifiable Delay Functions (VDFs). Designing implementations for the VDFs we develop is critical in the design of a better blockchain and digital-currency system.

We have some of the best software engineers that can be found anywhere, but we also like to open up the challenge of creating VDF implementations to teams of programmers who can show what our VDFs are really capable of, in terms of both speed and security.

A few months ago we wrapped up our first VDF implementation competition, and were amazed by the excellent quality of the submissions. The top three contenders each came in at under one minute (the reference implementation was 169 seconds). Five other teams also finished implementations faster than the reference point. All submitted code was open-source, and can be found [here](https://www.chia.net/2019/01/17/chia-vdf-competition-round-1-results-and-announcements.en.html).

The second VDF competition will be split into two tracks:

* SIMD and GPU optimizations allowed
* SIMD and GPU optimizations not allowed

This is to help us separate the different kinds of optimizations - however if somebody from track 2 is confident about their entry they can submit their code to both as there is no necessity for a track 1 submission to use those techniques. You can read more on our GitHub (link coming soon). More on the final details and prize money soon!

We handed out $100,000+ to the contestants in our first VDF challenge, and there will be cash prizes for the second one as well.

As we build a blockchain that is truly decentralized, secure and environmentally sustainable, we are thrilled we get to tap the best minds and the best talent to help us refine our VDFs. A lot of gifted software engineers have helped us along the way, and it’s going be great to see where we can take this next.
