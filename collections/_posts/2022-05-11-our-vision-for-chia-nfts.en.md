---
lang: en
layout: post
title:  "Our Vision for Chia NFTs"
date:   2022-05-11
author: "[Richard Tsao (eFishCent)](https://www.chia.net/profiles/richard-tsao/)"
---

In October 2021, Chia began exploring the NFT space and the role that we can play in it. We believe the Chia blockchain provides differentiated value through true digital ownership and [Chia Offer Files](http://chia.net/offers) that enable true decentralized trading.

Coming from the video gaming industry, I innately understood the appeal of digital ownership, but I wasn't familiar with the Ethereum blockchain NFT world. It is important to understand the fundamentals of how NFTs work today and then build our solution with an eye toward both solving the challenges facing the ecosystem today and demonstrating real-world applicability.

### Challenges with the current state-of-the-art technology

-   Transaction fees (gas in Ethereum) can be prohibitively expensive.
-   Inconsistent provenance for creators and owners of NFTs. It is very difficult to prove the NFT was minted by the original creator. It is also hard to determine if previous buyers were real people or wash trading to artificially raise the floor price of NFTs.
-   The digital files associated with an NFT have only one source link without any associated cryptographic hash. If this link ever goes away or if the file is replaced, the owner may lose access to the original digital files.
-   Lack of confidence that royalties are always paid out to the creators. Rules, such as royalties, are not enforced on the blockchain but only through participating in centralized marketplaces. This means the promise of receiving royalties on every resale can not happen with private sales between individuals or with non-compliant marketplaces.

### Challenges facing the end-Users

-   For many creators, NFTs can be a good additional revenue stream, but the technology and process can be complicated and difficult to understand. 
-   There is a negative connotation of pyramid schemes, scams, and fraudulent behavior with which they may not want to be associated.
-   Many established creators are concerned about the environmental impacts of current mainstream blockchains. Some are drawn to Proof of Stake (PoS) blockchains which are often marketed as more green or cleaner. Many creators don't fully understand the risks of centralization with the PoS consensus.
-   Adding another layer of complexity, the current ecosystem has broadly adopted one generic NFT standard, ERC-721, which seeks to fit all use cases for NFTs. Because the standard is so generalized, many of the features that users assume exist in ERC-721 simply don't. Royalties enforced on-chain serve as a practical example of this missed opportunity and point of friction. While subsequent standards have been released, none have captured the market share of the ERC-721 standard.  
-   Seeking to outline the challenges of the technology and that of the user helped our team understand where we need to focus and what we need to build to address the issues and bring more efficiency to the NFT ecosystem.

## Our plan going forward

We intend to address one market vertical at a time and create a bespoke NFT standard catered to that market's specific needs rather than attempting to create a one-size-fits-all standard.

Our first vertical is the **fine art world**, where we feel we can provide the best platform for artists. Specifically, we are seeking to serve artists who are interested in creating their first drop but have held off because of concerns around sustainability, inclusivity, and complexity in the NFT space.

Our vision for NFTs aligns with the Chia core pillars of security, sustainability, and compliance. To truly address the challenges in the space and offer a product with unique value, we've built our NFT standard with three key differentiating factors in mind.

We are seeking to leverage our sustainable, inclusive, and compliant blockchain to enable and drive real-world applications of digital ownership through **true marketplace independence**, **consistent provenance**, and **digital permanence**.

**True marketplace independence** by enforcing all rules such as royalties on the blockchain; *Chia Offer Files* for non-custody trading with no counterparty risks; and right to exit from any centralized marketplaces into the greater Chia NFT ecosystem. In the future, we will also provide a *Chia DataLayer* that allows all marketplaces to store and retrieve digital identity and NFT metadata in federated databases secured by Chia's blockchain.

**Consistent provenance** by allowing creators and owners to prove their Digital Identifiers through their established social media presence. In the future, we will provide optional integration with 3rd party partners for paid Know Your Customer (KYC) verifiers and other types of verified credentials.

Better **digital permanence** by supporting multiple sources and cryptographic hash for the NFT digital files. In the future, provide integration with optional 3rd party partners for paid institutional-grade storage of NFTs.

### Our Phased Approach

As we codified our NFT product strategy and vision, we know just delivering the NFT1 standard isn't enough — we want to deliver an entire user experience that includes a major revision with the Chia client GUI and an NFT ecosystem to launch at the same time. To ensure we're maintaining clear sight lines on our approach and the ability for our tech to address the challenges we've outlined, we've brought some of the leading community developers in for a closed alpha to ensure a vibrant ecosystem and interoperability.

We have split our release into phases aligned with our NFT design strategy.

**Launching Today:**

*Phase 1*: **NFT0** - functionally equivalent NFT standard to ERC-721.

**Future Launch:**

*Phase 2*: **NFT1** - Based on community feedback, the intent is to update the standard to deliver on the promises of independence, provenance, and permanence.

We're excited to share our approach to the Chia NFT standard with you. We believe it is a meaningful step to address the challenges and pain we've found in the current NFT ecosystem and creates the foundation for the next generation of NFT products on the Chia blockchain.

Today, the Chia development community will get a chance to join the first phase of our project with NFT0 on testnet. We can't wait to see the exciting projects you build!

<p style="text-align:center;"><a class="button primary-button" href="https://docs.chia.net/docs/15resources/nft_dev_guide/" target="_blank">Get Started with NFT0</a></p>


---

## Q&A

**Q: Why are you launching a testnet version of NFTs?**

A: Back when we started writing the Chialisp code for NFTs, we intended to launch a release with a narrow focus. But it soon became clear that we needed a more modular approach. Our new design pattern gives us the flexibility to release NFT0 as-is today, then with NFT1, add new modules for royalties and DIDs. With each subsequent update, we'll be able to add new features without having to start from scratch.

**Q: Who can mint NFTs today?**

A: We have no restrictions for who is allowed to mint NFTs. However, for now you'll need some technical skills, such as the ability to run Chia's testnet from a command line (CLI).

**Q: Is there an NFT0 user guide?**

A: Yes — We have a [user guide for NFT0](https://docs.chia.net/docs/15resources/nft_dev_guide/), which will show you how to create and trade NFTs, as well as use the new [set of RPCs](https://docs.chia.net/docs/12rpcs/nft_rpcs).

**Q: Is it possible to mint an NFT on mainnet yet?**

A: NFT0 is for testnet use only. While it's theoretically possible to mint an NFT on mainnet today, you'll run the risk that it will not be compatible with NFT1 due to bug fixes and/or last minute enhancements. You are strongly recommended not to attempt this. We will offer no mainnet NFT support, nor will make any promises of compatibility with future releases.

**Q: Which branch do I need to use for testing NFT0?**

A: NFT (and DID) development is happening in the [main_dids](https://github.com/Chia-Network/chia-blockchain/tree/main_dids) branch of the chia-blockchain repository on GitHub. Details of how to access this branch can be found in the NFT0 user guide.

**Q: Have NFTs been enabled in the GUI yet?**

A: For now they have only been enabled on the CLI, but we will be adding more and more NFT functionality to the GUI over the coming weeks.

**Q: What is included in NFT0?**

A: NFT0 includes the basic building blocks of NFTs. You can mint NFTs from the command line, and you can buy and sell them using offers.

**Q: What are the differences between NFT0 and ERC-721?**

A: The [ERC-721 standard](https://eips.ethereum.org/EIPS/eip-721) provides a highly generalized interface for creating and transferring NFTs on Ethereum's blockchain. Chia's NFT0 standard contains all the functionality of ERC-721. In addition, NFT0 uses a list of content URIs, which allow minters to store their NFTs in multiple locations, adding to the NFT's permanence. By contrast, ERC-721 uses a metadata interface with a JSON schema that only provides one URI link.

**Q: What additional functionality will be included in NFT1 that are missing from NFT0?**

A: The three main pieces of functionality that will be added to NFT1 are DIDs, royalties and offers. These are rather large features, which is why NFT0 is for testnet only. Swapping is also not yet enabled — you can only buy and sell NFTs for TXCH. Finally, NFT1 will enable full GUI wallet support. Currently only the command line is supported.

These features will enable NFTs that are created according to the NFT1 standard to be truly decentralized. For the first time, your NFTs won't be locked to a centralized marketplace, or even to any marketplace at all! NFT1 will also bring Chia NFTs one step closer to true digital permanence and consistent provenance.

**Q: How will royalties work in NFT1?**

A: In NFT1, the minter of an NFT will decide the royalty structure. We realize that a wide spectrum of functionality is desired for royalties. Some minters may only create NFTs as a hobby; they likely won't require any royalties. Others may be professional artists whose livelihoods depend on collecting royalties for their artwork. NFT1 will have a flexible royalty structure that will accommodate both of these use cases. Whoever mints the NFT can decide what percentage of future sales will be paid as royalties, for the lifespan of the NFT.

**Q: What are DIDs?**

A: DIDs are **D**ecentralized **Id**entifiers. Think of them as a way for people, groups, computers, or even real-world objects to identify themselves online. Chia will release its DID1 standard along with NFT1. DID1 will allow minters, buyers, and owners to track an NFT's provenance, giving them confidence in the history and origin of their artwork. It will also be helpful in many ways beyond just NFTs. In fact, Chia DIDs eventually will give users complete control over who is allowed to access their personal information, and what information they're allowed to see.

**Q: Will DIDs be required with NFT1?**

A: No. Each minter will be able to decide whether their NFT will require a DID. Professional artists will likely want DIDs in order to preserve provenance. Hobbyists might not care about tracking ownership and will eschew DIDs in favor of the pseudonymity of regular XCH addresses.

**Q: Are Chia NFTs sustainable?**

A: On other blockchains, NFTs have gotten a lot of bad press lately for their high energy requirements. However, Chia's blockchain was designed from scratch to use significantly less energy than Proof of Work (PoW) chains, while maintaining the same level of security. Chia NFTs do not require more energy than the base XCH from which they are minted. Extensive analysis of Chia's energy usage is available at [chiapower.org](https://chiapower.org/).

**Q: When will NFTs be made available on mainnet?**

A: Soon™! We have completed the heavy lifting of creating the NFT1 standard. However, we still need to allow our community devs time to do extensive testing. We'll likely need to make some minor changes before releasing the NFT1 and DID1 standards.