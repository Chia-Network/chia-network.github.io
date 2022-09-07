---
lang: en
layout: post
title:  "Cypherpunks in Sportcoats: Blockchain in the Real World"
date:   2022-09-06
author: "[Gene Hoffman](https://twitter.com/hoffmang)"
---

Cryptocurrencies and underlying blockchain technologies are going through a phase of euphoria – awareness is high and adoption is growing, but current use cases are often dubious. There’s confusion around the types of problems and applications that secure and sustainable public blockchains can and should solve...

We believe there are six primary areas where blockchains offer a superior toolkit to current technologies, addressing challenges for real-world use: markets, process integrity, identity, custody, payments and gaming.

## Markets: Trustworthy, Inclusive, and Global Trading

A secure and sustainable blockchain featuring a trust-building smart contracting environment empowers individuals and enterprises to create a market for assets and immediately tap into global trading liquidity. Adding DeFi capabilities like [Chia Offers](https://www.chia.net/offers/) means that you can now instantly trade digital assets between any two or more entities anywhere in the world, at any time of day or night -- in a way that neither the maker nor the taker can cheat the other but instead makes completing a trade trustworthy and fast.

Chia's coin model also significantly reduces the ability of farmers or miners to reorder transactions for their benefit which goes a long way towards removing MEV (previously known as Miner Extractable Value, now referred to as Maximal Extractable Value) leading to transparent and consumer-protecting decentralized exchanges of payments, debt, NFTs, or equities between willing buyers and sellers.

Couple these native capabilities with the growing ecosystem of "exchanges" (decentralized exchange is a verb and not a noun, so a website facilitating DeFi with these truly custody-less and peer-to-peer trades is not an exchange) and automated market makers, and you will soon have the ability for your asset to tap into the liquidity found in an AMM or an on-chain options chain that automatically populates for your asset. You can obtain the full set of functionality that the most advanced markets have to offer for any asset issued on Chia.

And, you can bring governance and dividends of your assets on-chain in the form of a DAO. We'd like to add nuance to the current notion of what a DAO actually is. We think of them as  fully digitized LLCs, non-profits, corporations, or partnerships. Amassing capital, managing voting, and managing the distribution of profits, all on-chain, make the process of - especially closed-end projects - much easier and scalable across both time and geography.

The network effect of a platform where real-world assets trade means that your asset will be able to pair and trade with assets like dollar stable coins or, say, oil commodities and carbon offsets, or wBTC or XCH. The ability to compose and create trades between these assets trustlessly brings superior strength to an Internet of Markets™ built using inherently cross-border and cross-market final settlement blockchains.

## Process Integrity: Transparent, Trustless Tracking

Blockchains are excellent transparency engines. There has long been tension between wanting to run a private blockchain versus a public blockchain. Those tensions arise for a few reasons. First, very often a project wants many of the core elements of a public chain, like transparency and an append-only nature. However, many projects need some or total confidentiality. We built our DataLayer federated database technology with these needs front of mind. Leveraging the DataLayer technology, participants in your federated database can be totally pseudonymous to the outside world and as transparent (or not) internally. Additionally, there's a middle ground where you can prove inclusion or exclusion of select elements in your federated database to some or even all of the public. Or your use case is built to rely on full transparency and full disclosure.

The [World Bank Climate Warehouse](https://urldefense.proofpoint.com/v2/url?u=https-3A__www.theclimatewarehouse.org_work_climate-2Dwarehouse&d=DwMGaQ&c=euGZstcaTDllvimEN8b7jXrwqOf-v5A_CdpgnVfiiMM&r=bGYnQ2oBpGc_IFiC69q7OVqS8FwnxcsCD3JsJ43zwNw&m=2ahFYGxKZWHGS9Yhzj3wanBy3g3eMUEWSAnG1BTtNwc&s=z4HnZlM0xYOPk8z3uZmv0oMPULt8nZBzBwKTPfjdn08&e=) is an excellent example of a fully transparent application. The goal is to deploy technology to ensure that all voluntary and national registries of voluntary carbon offsets are accurately counted -- creating a more secure environment where one can't double-create or double-retire a specific carbon offset without creating a glaring public audit trail.

Two other types of tensions are highlighted by the Climate Warehouse project. This method of go-to-market means that no one entity can deny permission to participate in the federated database (beyond the partners in the federation). All partners in the federation are on an equal footing. For example, nations with geopolitical tension can both participate in the system without trusting one another. Finally, by using a federated database, the data elements stored and updated can be richer and larger than one should ever put on a very decentralized blockchain. PDF files should never themselves be stored on the public ledger, but the cryptographic hash of a database update that includes PDFs and full metadata is exactly the kind of thing that should be published and managed on a public blockchain.

These kinds of database integrity tools serve as the foundation for building much more transparent and less graft inducing processes. A number of nations in the Global South use agricultural warehouse receipts as a sort of bearer bond for farmers. The largely paper-based processes are ripe for fraud, and trying to build a web2 style application that relies on a central (usually government entity) for trust and maintenance presents challenges. Building a QR code driven weighing and receipt system that rides on Android and stores its data using DataLayer makes it much easier to aggregate data to check for systemic counting errors and creates a trustless way to be sure that the buyer or financier of a warehouse receipt isn't dealing with a forgery (and much less likely that it is based on fudged data).

## Identity: Digital Identification and Credentialing 

Blockchains, especially those that use the UTXO or Coin model, are perfect infrastructure for the W3C Decentralized Identifiers (Digital Identity) infrastructure. DIDs, and a decentralized blockchain, can be the best form of privacy protecting identity and attestations we’ve ever had. End users can obtain credentials through their DID which allows them access to something or may certify something about them like a passport, a trade license, being an accredited investor, or being the author of this art NFT. Once identity is available then things like login with your Chia DID can add up to both a strong addition to, or replacement of, web2 logins or even your enterprise email. By removing the need for trusted third parties, DID may be the most secure method of identity and single sign-on ever.

## Custody: Security and Control 

Custody can be a bit harder to understand, as most people’s experience is rooted within the technological limitations of current Bitcoin and Ethereum. With their context, it’s harder to envision, and reason, about how custody and control could work with a chain that can enforce sophisticated custody rules. This is one of those few places where making the technology more complicated will actually allow developers and deployers to make the human use of the technology much simpler.

As an example, today the best practice is to back up a hardware wallet with a restoration key of 24 words on paper or metal (for those worried about fire). This process just isn’t very user friendly and is quite brittle because anyone who steals that paper or metal collection now has complete control over all your assets – and your identity too!

We believe a better system is a slow paper wallet. This uses the same piece of hardware, but what you backup is actually a smart coin with certain limited powers that allow you to mitigate and even avoid the unauthorized transfer of your money. If you lose or break your hardware, you can use those 24 words to move any coins in your now “lost” wallet to a new wallet after a set time period. Optionally, you can have that coin require X% of the then value in that wallet to be able to recover it too. With a slow paper wallet, if someone is able to steal your paper wallet, and you still have your hardware wallet, your hardware wallet is superior to the paper and you can see someone submitted the recovery on chain and - as long as you see it in the recovery window - take your funds to a new third wallet and optionally have the X% surety put in your new wallet for your troubles. Now having a few copies of your backup paper wallet is more feasible, as you have to trust wherever or whoever has them a whole lot less.

In the enterprise use case, you can now put your existing controls on-chain and the composability of these custody primitives means you can likely build an even more secure control matrix while cutting down on the number of tools and steps your employees have to use to get things done securely. Being able to authorize domestic wires, send out issued assets, send international crypto payments and log into your email, all with the same credentials and various DID elements means you can train your employees to use something far simpler and use it for multiple purposes each day while being even more secure. We look forward to the death of passwords…

## Payments: Democratizing Remittances

The cost of simply moving money around during the year 2020 was about $915 Billion dollars. The act of moving payments - especially across borders - is at best arcane. The existing systems require counterparty trust. For example, a “simple” debit card transaction requires the end user to trust the seller, the card network, the seller’s bank, and the end user’s bank with a little bit of Fedwire and ACH trust thrown in to get towards final settlement.

Satoshi saw the opportunity to remove trust from payments and to make them a global, faster, trustless network. Advances in blockchains and smart coin capabilities mean payments can be totally trustless, or slightly trusted when using an oracle to finalize otherwise trustless on-chain escrow. These payments are available to anyone, anywhere, 24x7, and now will settle transparently with finality in just a few minutes. Raising notionally, for now, this capability starts to blur the line between asset types, as stock trading or commodities trading can start to look more like payments and less like the traditional concept of trading.

Regardless of the store of value and digital assets argument, Bitcoin has had a real impact. Competition from the use of Bitcoin in remittances has driven the traditional providers to be both faster and cheaper, yet Bitcoin usage in cross border transactions continues to grow in many countries and regions.

## Randomness and Gaming: Predictable Unpredictability

Blockchains turn out to be an excellent, and maybe the best, source of publicly verifiable random numbers - especially those chains featuring primitives like VDFs. This randomness means that things like sports drafts, lotteries, and on-chain games of skill can all be mathematically, provably safe and secure. When everyone can trust that the source of randomness could not be predicted, and can be applied fairly and equitably, corruption becomes decidedly more difficult. But this also means that things like on-chain poker playing between players with real money can be a high trust environment, and on-chain collectible games or trading card games in the style of the Magic: The Gathering or Dungeons and Dragons are provably fair as well. Your NFT avatar can have a fair fight to advance to the next round.

We do share some of the reservations around the current notion of the “Metaverse” but also understand we are early in the development and adoption of what the Metaverse will be, and are excited to see what the future holds. Coming out of the spirit of MMORPGs and Second Life, we believe the ability to bring your digital assets between virtual worlds has real value to build an entirely novel style of gaming and gaming business models.. It’s even cooler when your favorite digital sport coat might also be an intangible representation of the sportcoat you most recently had physically tailored using your digital measurements…

## The real world needs it all, and probably more

We are sure that there will be at least one more category like the above that none of us can see just yet. We are excited to build solid and trustworthy primitives and real-world deployments that serve as a foundation for the next breakthrough developer to break these categories.

Also, it is very important to note that many of the best use cases will actually touch on or take elements from more than one of these categories. NFTs hide in DataLayer, and DataLayer is going to be far easier to use every day in the business world if it has accessible custody and control.

We’ll continue to drive real-world applications as we are in the carbon markets, financial markets, and art markets today. Ultimately, the transformational components that are materially better on a blockchain are likely to touch on a very wide range of our human endeavors. Just like very few people are thinking about IPv6 when they order from DoorDash, long term we expect blockchains and cryptocurrencies to simply be a deeply ingrained part of what we call life.

Till then, we’re excited to see what we can build together.