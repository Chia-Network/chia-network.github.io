---
lang: en
layout: post
title: "Understanding the Changes in the New Light Wallet"
date: 2022-01-10
author: "[Dan Perry](https://github.com/danieljperry) and [Roy Natian](https://www.linkedin.com/in/roynatian)"
---

In the coming weeks, we’ll be making some major updates to the official Chia client with v1.3. One of the biggest will be bringing the light wallet out of Beta and including it and it’s observer addresses into the core software package. The light wallet will, on average, improve your wallet sync times from many hours to mere minutes. You’ll also be able to run a wallet without running a node. Observer addresses enable read-only wallets, which have several advantages, detailed below.

When will these changes happen? Soon™.

## What’s new?
### Faster sync with the new light client
Before version 1.3, Chia’s wallet had to sync from genesis. In other words, it had to download your wallet’s information for every block, starting from 0. The Chia blockchain is nearly 1.4 million blocks long at this point, so the sync process took a substantial amount of time to complete.

With the newest version (currently in Beta as of this writing), Chia uses a new [light client protocol](https://docs.chia.net/docs/03consensus/light_clients/), which only needs to download a small subset of blocks to validate your wallet’s status. New wallets will sync in minutes instead of taking hours or days. (Wallets with many historical transactions will take slightly longer to sync, but they will still sync _significantly_ faster than previous versions.)
### New wallet keys
Previous versions of the Chia client used non-observer wallet keys. These keys are secure, but they come with a drawback – a parent public key cannot be used to derive a child public key. This means that read-only wallets are not possible with Chia’s old keys.

The new version of the Chia client uses _observer keys_ by default. These keys _do_ allow for public derivation, and the main benefit to these keys is to support read-only wallets.
Why support read-only wallets? The main reason is to provide a way to view your wallet without the possibility of exposing your private keys. This will give extra peace of mind for those who simply want to view their wallet in a third-party developed application, without needing the ability to send money to another wallet, and therefore without exposing their private keys to the application.

Another potential use case for read-only wallets is tax preparation. In Chia, you can use a new address for each transaction, which provides pseudo-anonymity on the public blockchain. However, with the old keys, you would have to provide your accountant with every address you have ever used. With the new observer keys, you’ll be able to simply provide your master public key, and your accountant can use it to derive the public key from each address you used. This is possible without providing any private keys or any way to derive them.

## What this means for you, the user
*Please read this section carefully as these changes to the Chia client might cause some confusion.*
### Update all clients to v1.3 to properly see balances
_Older versions of the Chia client that use the older non-observer keys won’t be able to view some new transactions on the new wallets._ Don’t worry–you have not lost any chia! 

For example, if you have Chia running on two computers and only upgrade one of them to v1.3, your wallet running the older version might not be able to see any new coins added to your v1.3 new wallet. Your wallets may not show the same balance. We recommend that you upgrade all of your installations simultaneously to v1.3.
### Cold wallets
If you are using a cold wallet that uses different private keys, you can continue using it as is. If you do warm up your cold wallet to transfer XCH, we recommend you follow the steps below and move your XCH to a new wallet address in Chia client v1.3 or later. 
### Future wallet preparation
_You are not required to do this, and it will not have any impact on your current user experience. These steps can also be done in the future, at the 1.3 release, or anytime in between as you desire._

1. Update to v1.3 of the Chia client
2. Generate a new wallet address
3. Send your XCH from yourself to the new wallet address you created
The benefits of doing this sooner rather than later are:
Your wallet will be ready to work with any tools that use observable wallet keys

You will preserve more of your wallet transaction history
If you choose to move your wallet balance to an observable address at a later date, you will not be able to see the transaction history before that transfer to the new wallet address. Moving your XCH to a new wallet address sooner than later will increase the amount of available transaction history moving forward.
### More Information 
For more information, see our documentation website:
* [Observer and non-observer keys](https://docs.chia.net/docs/09keys/keys-and-signatures#non-observer-vs-observer-keys “Observer and non-observer keys”)
* [Technical details of the fast sync protocol](https://docs.chia.net/docs/10protocol/wallet_protocol/#fast-sync-protocol-recommended “Fast sync protocol technical details”)

And as always, if you have questions, come join us on [Keybase](https://keybase.io/team/chia_network.public). 
