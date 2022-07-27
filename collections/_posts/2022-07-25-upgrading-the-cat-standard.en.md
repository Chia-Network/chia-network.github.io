---
lang: en
layout: post
title: "Upgrading the CAT Standard"
date: 2022-07-25
author: "[Chia Team](https://www.chia.net/team/)"
---

*Updated July 27, 2022 at 17:00 UTC* ‎
## Reissuance is Underway.

Following the end of life (EOL) of CAT1 at block height 2,311,760 (at approximately July 26, 2022 at 9:00am PDT), we're providing an update on the reissuance process and information on next steps for asset holders and asset issuers.  

### Asset Holders

If you have any CATs in your wallet, you will want to upgrade to 1.5.0 as soon as conveniently possible. CAT1 assets are no longer supported in the wallet as of today's 1.5.0 release.

<p style="text-align: center;"><a class="button primary-button" href="/download" target="_blank">Download Version 1.5.0</a></p>

#### How to see your old CAT1 balances 

We encourage you to visit the [CAT1 website](https://cat1.chia.net) that is also linked to from inside the 1.5.0 wallet. Using this tool, you may view the CAT1 balance of your wallet as of the EOL block height. If CAT issuers choose to reissue with CAT2 using the developer tools Chia provides, you'll soon start to see these CAT1 balances match the CAT2 assets in your 1.5.0 wallet.

This site will not dynamically update -- it only displays a snapshot of CAT1 balances as of the EOL. We expect the reissuance process could take up to a week to be fully completed. During this process, the CAT2 balance in your wallet may differ from the CAT1 website balance until reissuance is complete.

As an asset holder, there should be no further action on your part beyond upgrading to the 1.5.0 wallet. To ensure that the reissuance balance you are expecting is what will be airdropped to you, please do not transact with any CATs after the end-of-life block height 2,311,760 has been reached and until you have upgraded to version 1.5.0.

### Reissuers

We have provided documentation on the reissuance tool [here](https://docs.chia.net/docs/cat2/cat2-intro). We have 24/7 support in our [#cat2_support Keybase channel](http://keybase.io/team/chia_network.public#cat2_support) to support the developer ecosystem throughout the process.

## Now that we've patched it, what actually happened?

### The Risk

In May, we kicked off the engagement with security auditor [Trail of Bits](https://www.trailofbits.com/) to audit the security of the CAT1 standard coin. They expressed concern about a potential class of vulnerabilities that led us to uncover a security vulnerability with CAT1. Our team has confirmed this issue has never been exploited. The vulnerability offered a bad actor to take a CAT1 in their possession and print/inflate any arbitrary amount of coins, effectively flooding and devaluing the underlying asset. In non-technical terms, the vulnerability enables anyone to create a money printing machine to print as many counterfeit copies of the CAT as they want.

### Our Response: White Hat Solution

Within 24 hours of confirming the vulnerability, we built a tool to monitor the blockchain and alert us of any exploits. We also created a patched CAT2 upgrade in a private repository, but given the risk only applied to the CAT1 standard, not XCH, an immediate emergency fix could have caused pain for developers and users. We also found a related issue with our in-development NFT1 standard, and while harder to find and even harder to leverage, we took the time to harden the NFT1 standard against this prior to release. With monitoring in place, we chose to build out a full remediation kit to reduce friction for developers and exposure of end users to risk.

This approach allowed us to create tools that enable CAT developers to easily and securely re-issue their assets as CAT2 and gave us time to train our ecosystem teams to support reissuance efforts. 

### CAT1 Printer Go Brrrrr

We engaged in a white hat effort to materially reduce risk to the community. What was the risk? Here's an example: Post-EOL, Alice has offers she created that she forgot to cancel, in which she is offering either XCH or an NFT in exchange for some CAT1 tokens. Bob, a bad actor, runs the exploit to print enough CATs to take the other side of those offers, and accepts her offers.

The result? Bob now has Alice's XCH or NFT from her offer, and Alice is left with a CAT1 that won't be upgraded to CAT2 because it's after the EOL cutoff.

As our first step, we proactively contacted the main DEXs to ask them to take CAT1 offers offline and block new ones from being created – reducing the risk that Alice is cheated by Bob. This was completed during the day Monday, June 25, 2022.

Furthermore, we scraped outstanding CAT offers in the Chia ecosystem and ran these offers through a tool we built leveraging *this exact vulnerability and exploit*. Our tool ran the exploit to generate enough CAT value and accepted the offers we scraped, but instead of receiving the XCH or NFTs ourselves, we returned the XCH or NFT to the offer maker, all in the same block. Chia never custodied this XCH or NFT in the process. Once we accepted the offers, no one else could accept them. We believe our white hat efforts eliminated most of the risk to the ecosystem.

Lastly, we issued tools, produced developer tutorial [videos](https://www.youtube.com/watch?v=nofc5RMbzq4), and drafted full documentation to support CAT developers with reissuance. The first piece is a snapshot at the EOL of all the CAT coins, their values and owner's addresses. Developers are free to generate their own snapshot, as it's simply a CSV file output of any Chia blockchain node's database. We also built an airdrop tool that uses a technique called [Secure the Bag](https://bitcoinmagazine.com/technical/secure-the-bag-cutting-transactions-in-half-to-resolve-bitcoin-network-congestion), invented by [Jeremy Rubin](https://twitter.com/JeremyRubin), to simplify and speed up the airdrop process substantially.

### Timeline of This Issue

-   **2022-06-14** - Trail of Bits alerted us to look at some particular code and dive deeper
-   **2022-06-15** - We confirmed an issue on our side
-   **2022-06-18** - We completed the technical fixes on the CAT2 standard
-   **2022-06-20** - We completed verification that our fixes were solid
-   **2022-06-29** - We shipped the NFT1 standard, with an included silent fix related to this issue
-   **2022-07-25** - From 2022-06-20 to 2022-07-25 we completed the various development work needed to conduct the mitigation steps undertaken on the 25th and 26th, as well as the reissuance tools and supporting documentation
-   **2022-07-25** - The announcement was made and the various steps outlined in the above post took place


### What Now?  

CAT1 coins will continue to exist, but our wallet will no longer acknowledge them. The system on which these coins are traded is now safe, wallets are secure, and no one has access to, nor can steal, your old or new coins. Moving forward, if a bad actor is able to find the vulnerability, they can print as many CAT1 coins as they have a copy of and would like, but their actions will have no effect on the network or your assets since any created CAT1 coins will be ignored.

We'll provide an in-depth case study on the vulnerability, the changes we made, the process updates on our side, and how we're maintaining the future of the network Soon™.

Thank you for being a part of our community. If you need any help with the CAT2 reissuance process, read the FAQ below or visit our [Keybase CAT2 support channel](https://keybase.io/team/chia_network.public#cat2_support).

<br />
<hr />
<br />

As part of our ongoing commitment to maintaining a secure and safe environment, we regularly bring in third-party security auditors to test, analyze, and attempt to break Chia blockchain technology.

In our most recent audit, [Trail of Bits](https://www.trailofbits.com) raised a potential class of vulnerabilities that led us to uncover a security vulnerability with CAT1, the standard we released earlier this year for asset tokens on Chia. Our team confirmed this issue has not been exploited as of this announcement, and we are continuing to monitor the chain. However, we have determined that the vulnerability is serious enough to warrant upgrading CAT1 to CAT2. This upgrade will patch the vulnerability, end-of-life CAT1, and support the reissuance of CAT1 coins as CAT2. We will publish the Trail of Bits report soon after CAT1 is EOL.

The Chia team is committed to making the upgrade as secure and seamless as possible to asset holders and CAT issuers alike. Here's what is coming:

## CAT1 is End of Life and Release 1.5.0 Implements CAT2

On Tuesday, July 26 around 10am PDT (after block height 2,311,760), CAT1 will be officially EOL and replaced with CAT2 – Version 1.5.0 will be available for download, including the upgraded wallet to support CAT2.

### What does this mean? 

The EOL milestone will serve as a point of reference for CAT issuers to reissue their CATs to holders. For example, if a holder has 1000 USDS in their wallet at the EOL block height, the issuer, Stably USD, will reissue the same 1000 USDS value to the holder as a CAT2 asset. Each CAT1 coin a user has at the time of the EOL block will be replaced with a CAT2 coin of the same type that is identical in value. Following the EOL milestone, if this same user traded some of their 1000 CAT1 USDS for another asset, that user will still only receive the 1000 USDS in CAT2 value.

All users holding CATs (including USDS) are encouraged to download release 1.5.0, as your CAT1 balances will no longer be displayed in the wallet.

We strongly advise you not to make or accept Chia Offers of XCH for CAT1, or trade NFTs for CATs, until after upgrading to version 1.5.0, as any CAT1 transactions after EOL will not be considered valid for reissuance. If you make or take an offer to trade XCH for CAT1 coins after the block height EOL, your XCH funds will be lost and the CAT1 assets you received will not be upgraded to CAT2.

It is important to note -- this is not a fork, the chain has not slowed nor stalled. This is an upgrade to the CAT standard to patch a vulnerability which only affects CAT1 tokens. The blockchain, XCH, and NFTs remain unaffected.

### What should I expect as an asset holder?

As CAT issuers re-issue with CAT2, your balances will begin to update over the coming week. This is a process and will take some time, we ask that you please be patient while reissuers get through all CAT1 coins.

We've created [a website](https://cat1.chia.net) for you to view your historical CAT1 balances, directly accessible through a link in the 1.5.0 wallet. You can use this site to compare your CAT1 balances with your CAT2 balances in the new wallet.

This site will not dynamically update. It is a static snapshot of your CAT1 Balances at the CAT1 EOL and is meant to serve as a reference.

### What Steps You Need to Take

- If you plan to continue using CATs (Including USDS), you must update to the 1.5.0 release. Please head to our site <em>after 10am PT Tuesday July 26</em>, to [download](/download) the 1.5.0 wallet. Once you've downloaded the new wallet, you should be good to go and can simply wait for reissuance. We understand that this is a big change on a quick timeline, and we are working diligently to ensure there's minimal impact to you and your experience in the ecosystem.

- Cancel your offers: If you've made any Chia offers, selling XCH for CATs, you should cancel them in your wallet immediately. If someone accepts your offers post-EOL, you would be trading your XCH for CAT1 assets. Since these assets would be traded post-EOL, you won't likely be airdropped a CAT2 equivalent.

- For CAT issuers, we are releasing tools, [developer docs](https://docs.chia.net/docs/cat2/cat2-intro), and providing real time support for reissuance.

Chia is committed to supporting our community through the upgrade process. If any challenges or issues arise, the Chia Network support team is available 24/7 in our [Keybase support](https://keybase.io/team/chia_network.public) channel.

---

## FAQ

### End Users

#### General Questions

**What is a CAT?**

A CAT is a Chia Asset Token. CATs are fungible tokens that are issued on the chia blockchain. The CAT1 standard was finalized in January 2022. The standard can be found at [chialisp.com/docs/puzzles/cats/](https://chialisp.com/docs/puzzles/cats/). Some examples of CATs include Stably USD (USDS), Spacebucks (SBX), and Marmot (MRMT).

**Why is this change happening with Chia asset tokens?**

The CAT standard was upgraded to CAT2 based on a security vulnerability found by an outside security audit. This resulted in an upgrade to the latest Chia wallet app as well as updates that will require all original issuers of CAT1 tokens to reissue their tokens on the CAT2 standard and end-of-life support for CAT1s. Chia is working with community members to make this process as seamless as possible.

**Does this change impact Chia Network's security?**

No. There is no threat to the security of Chia Network technology or the Chia Blockchain. The update patched the vulnerability to CAT1. 

**When does the end-of-life of CAT1 happen?**

CAT1 is end-of-life after block height 2,311,760 which is approximately around 17:00 UTC. This is when the snapshot is taken.

**How can I check my CAT1 balance at the time of the snapshot?**

Go to [cat1.chia.net](https://cat1.chia.net) and provide your pubkey to see the CAT balances that will be airdropped to you when they get re-issued.

**Does everyone have to upgrade?**

We recommend that all CAT (including USDS) holders upgrade to 1.5 as soon as is convenient. The CAT1s that are visible on 1.4 and earlier versions will no longer be supported after the end-of-life block (2,311,760). If you do not own any CATs (for example, if you are a farmer who does not exchange XCH for USDS or any other CAT), then you don't need to upgrade.

**Do I need to upgrade my harvesters?**

This update only affects the wallet software, so you don't need to update your harvesters.

**Are my NFTs or XCH at risk?**

No. NFTs and XCH are not affected by the vulnerability, so no changes are required for them.

**Is there any risk that I'll lose money or my balance will be incorrect during the transition? If so, what do I do?**

If you have any CATs in your wallet, you will want to upgrade to 1.5 as soon as conveniently possible and be sure not to transact with any CATs after the end-of-life block height (2,311,760) has been reached and until you have upgraded to 1.5. This will help ensure that the balance you are expecting is what will be airdropped to you when the CATs are reissued. The [CAT1 website](https://cat1.chia.net) accurately reflects the CAT1 balance of your wallet as of the end-of-life announcement. It will not dynamically update, but we expect the reissuance process to take approximately a week to fully complete, so the CAT2 balance in your wallet may differ from the CAT1 website balance until the process is done.

**Between the announcement and the end-of-life block height, what should I be doing as a user?**

It is recommended that you:

1.  Cancel any open CAT offers on-chain in your wallet

2.  Do not accept any CAT offers in your 1.4 or lower wallet

3.  Make note of your current CAT1 balances

4.  Upgrade to the latest Chia wallet app (1.5.0 or higher) when it becomes available

**How can I be sure that I've canceled all my open offers?**

Most importantly, you will want to make sure there are no outstanding offers to trade your XCH for someone else's CATs. In addition to canceling the offers in your wallet, you can also send your total balance of XCH to yourself. Due to the chia coinset model, this will ensure that all XCH coins will no longer be available should a rogue or forgotten offer be accepted.

**I may have lost money by transacting, what should I do now?**

Unfortunately, any CAT1 transactions that happen after the end-of-life block height won't be recoverable. For further confirmation, please contact our support team so they can help with checking when the transactions occurred and can help determine if the money is lost or not.

**Do I need to cancel my XCH-for-NFT offers?**

No. Only CAT1 tokens are affected. No changes are being made to NFTs. However, if you have an open CAT-for-NFT offer, then you should cancel it.

**How can I trust that all of my currency will be transferred appropriately? **

You can check your CAT1 balance as of the snapshot through our [website](https://cat1.chia.net) using your pub key.

We are providing tools and support to the community developers to help ensure that they can reissue the new CATs in a timely manner. All CAT reissuers will be going by token balances at the same end-of-life block height.

**What happens to my CAT1s?**

Your existing CAT1 tokens still exist on the blockchain, but they are of no more use as everyone upgrades to CAT2s. You will be airdropped CAT2 to replace your CAT1 based on your balance as of block height of 2,311,760. Once you upgrade to 1.5, you will no longer see any balances for your original CATs.

**How long will it take for me to get all my tokens airdropped to me?**

This will depend on when the original issuers re-issue their tokens based on the new CAT2 standard. We hope that it is soon after the CAT1 EOL date. It is recommended to follow any social media, or discord for the CAT token projects so you can hear first hand when to expect the airdrop.

**What happens if I have a transaction with a CAT1 token after the block height snapshot?**

You will only be airdropped the balance of the tokens at the time the snapshot is taken. Any transactions that occur after the snapshot will not be accounted for in the airdrop provided to you.

**How can I trust that all of my currency will be transferred appropriately? Is there any risk that I'll lose money or my balance will be incorrect during the transition? If so, what do I do?**

Your CAT1 tokens won't be transferred. Instead, you will be given an identical (in value) set of CAT2 tokens. The blockchain already contains a complete record of all coins in the coinset. We have developed a tool that will use the blockchain to calculate a complete snapshot of CAT1 tokens. This snapshot will be accurate as of CAT1's end-of-life block.

However, the CAT1 issuers do need to perform a complete airdrop of CAT2 tokens. If the airdrop is not completed, or even started, then there is a risk that you will not receive your upgraded CAT2 tokens. In this case, you should ask the issuer to make the upgrade.

**I am the issuer of a CAT1 token. What should I do?**

[Follow this document](https://docs.chia.net/docs/cat2/cat2-intro), which will guide you through the process of reissuing your token as a CAT2.

#### Chia App Questions

**I upgraded to 1.5, but I don't see any of my tokens yet. Did I do something wrong?**

No, you didn't do anything wrong. The Chia Wallet app, as of 1.5, only shows you your XCH, and CAT2 balances. As not all CATs will be re-issued immediately, when your CAT2s show up in your wallet is dependent on when original issuers issue their updated CAT2s.

**The balance of my airdrop in my wallet doesn't match the balance that the website shows me, what should I do?**

First, please consult the CAT1 balance [website](https://cat1.chia.net) to view your historical CAT1 balances. We expect the full reissuance process to take approximately a week to complete.

If your CAT2 balances in the 1.5.0 wallet do not match the CAT1 historical reference, then check what your wallet derivation index is at and compare it to the derivation index. The derivation index is shown in the balance on the Tokens screen.

<p align="center"><img src="/assets/blog/cat2-01.png" alt="Chia client" width="75%"></p>

If the derivation index in your wallet is less than the highest derivation index found on the website, you will want to update the derivation index in the wallet. To do so, go to *Settings* > *Derivation* index and type in the number that you get from the [cat1.chia.net](cat1.chia.net) website.

<p align="center"><img src="/assets/blog/cat2-02.png" alt="Chia client" width="75%"></p>

**I've tried all the recommendations, but the reissuer didn't get my wallet balance correct. What should I do?**

After trying all the above steps and at least a week has passed since the announcement and your CAT2 airdropped balance still doesn't match, then we recommend reaching out directly to the reissue of the relevant CAT1 token.

**How do I cancel my open offers to exchange CATs?**

From the Chia Wallet user interface:

1.  Go to the Offers tab in the left hand navigation

2.  Find all Offers you created that show a status of "Pending Accept"

3.  Click on the three dots under "Actions"

4.  Click on "Cancel Offer"

5.  Ensure "Cancel on blockchain" option is selected

6.  Enter a fee (optional, but recommended)

7.  Click on "Cancel Offer"

From the Chia Wallet command line:

1.  Run `chia wallet cancel_offer` along with the parameters needed to cancel any open offers. See [here](https://docs.chia.net/docs/13cli/nft_cli) for documentation on how to use the command line arguments.

**After upgrading to 1.5, I've lost all of my wallet transaction history. How do I access my previous transaction history with CATs or XCH?**

After upgrading to 1.5, a new wallet database is created to preserve any previous copies of wallet DBs. You can install a previous version of the Chia wallet app, and that older client will look for your previous wallet db and display the transaction history for XCH, CATs, and NFTs that occurred in that wallet before upgrading to 1.5

**How do I know when the updated tokens have been airdropped to my wallet?**

You should follow the projects for the tokens that you own so you can be notified when they have begun running the airdrops. You can also monitor your Chia wallet app, and look under the "Manage token list" to see if a new CAT2 has been airdropped to you.

**Why doesn't the balance in my wallet match the balance reported on the website?**

Get the Derivation index from the website and update the derivation index in the Chia wallet app. This will ensure the balance reported on the website matches up with the balance in your wallet.

**What is a "Derivation Index"?**

The derivation index is a numeric value that is used to track how many wallet addresses have been used based on the most recent transaction. This helps establish a window for which wallet addresses to scan for on the blockchain to find all possible coins owned by a specific wallet.

**Why do I see multiple tokens with the same value in my 1.5 wallet?**

It is possible that you have received multiple identical airdrops from different parties. Only one of them will be the real CAT2 token. To determine which one is real, click "MANAGE TOKEN LIST" and click "Search on Tail Database". Only the original CAT1 issuer will be allowed to register their CAT2 equivalent on Tail Database, so you should use it as the source of truth for naming your CAT2 tokens.

**Who can I contact if I have any problems or questions?**

The Chia Network Support Team is available to answer questions and provide assistance through this process in the official [Keybase support](https://keybase.io/team/chia_network.public) channel.

#### [cat1.chia.net](https://cat1.chia.net/) Website Questions

**How do I find the pubkey to enter into the website?**

From the Chia Wallet user interface:
1.  Go to "Select Key" screen and click on the "See private key"
2.  Copy the "public key" from the list of keys available
<p align="center"><img src="/assets/blog/cat2-03.png" alt="Chia client" width="1rem"></p>



From the Chia wallet command line:

1.  Run `chia keys show`

2.  Copy the "master public key" from the list of keys available

**I checked the website (cat1.chia.net) and I don't see any tokens for my wallet, but there should be. What can I do?**

Confirm the pubkey you entered into the website is correct and had a CAT1 token balance, and is for an unhardened key

Click on the "Search next 1000" to see if your balance has been updated

**The balance that the website is reporting doesn't match what I expect. What should I do?**

The website scans the first 1000 wallet receive addresses, and if the balance doesn't reflect what you expect, then you should hit the "search next 1000" for the website to scan and update the balance found. We expect most users to get their correct balance from the initial search, but some users might need an expanded search.

**My CH21 balance is reported incorrectly on the website. What should I do?**

CH21 tokens were issued to non-observer keys, so they won't show up in the website unless they've been transferred at some point using a wallet without forcing the non-observer key support. The CAT standard was released at the same time as support for observer keys, so generally most CATs and wallets will be supported by the website. Even if your CH21 tokens are not displayed on the website, a CAT2 version will still be airdropped into your 1.5 wallet.

**I am running 1.5 and when I view an offer, instead of the CAT token, I see XCH. What's going on?**

You are likely viewing an offer for a CAT1 which will be an invalid offer starting with version 1.5. The reason for this is because tail ids for CAT1s are no longer recognized by the wallet.

<p align="center"><img src="/assets/blog/cat2-04.png" alt="Chia client" width="10px"></p>

### Wallet Developer Questions

**I am developing a Chia wallet. What changes do I need to make to my code?**

CAT2 inner puzzles do not enforce prepended announcements. If you preprend a coin announcement with `0xca` (which was a requirement for CAT1), then the announcement will fail with `ANNOUNCE_CONSUMED_FAILED`. Instead, do not prepend inner puzzle announcements with anything.

 Note that announcements coming from the CAT layer still need to be prepended with `0xcb`. This has not changed in CAT2.
