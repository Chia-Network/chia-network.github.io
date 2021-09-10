---
lang: en
layout: post
title:  "Important Version 1.2.6 Information"
date:   2021-09-10
author: "[J. Eckert](https://twitter.com/Sargonas)"
---

## Version 1.2.6 Released!

We’ve released [version 1.2.6](https://github.com/Chia-Network/chia-blockchain/releases/tag/1.2.6), which is to address a bug-fix with nodes. While this is technically a bug-fix version, we want to stress the importance of this update being applied to your own nodes, _and encourage you to update to it at the earliest convenience_.

Last week a bug was detected in the nodes that caused them to consume excessive amounts of memory when the queue of incoming compacted-blocks from Bluebox Timelords grew faster than the node was able to process them. As this queue increased, it could eventually grow to consume all available memory, resulting in node and system instability. (If you’re unfamiliar with Bluebox Timelords and what they do, I cover that down below!) While this bug has been around since the launch of mainnet, this fully came to light last week because Chia Network rolled out 100+ Bluebox Timelords temporarily to both bring down the ever growing blockchain DB size, as well as to put into production the new Bluebox Timelord code we made recent improvements to.

Unfortunately, this caused nodes all over to receive a large quantity of compressed blocks, and the work of swapping the increased volume of compressed blocks into the DB for the uncompressed versions caused some nodes to be unable to keep up, and experience higher-than-acceptable memory usage. As a result, we brought those Blueboxes offline and developed this update. To address this problem, this update contains better handling logic on the node side to manage that incoming data in a way that allows the node to maintain stability, which should prevent this from happening again.

As the chain is continuing to grow and the bloat still needs to be addressed, Chia still intends to ramp back up to this same number of temporary Bluebox Timelords to compress things down for you and streamline the db size, but this time we will do a gradual increase of them over several weeks starting next week. As a result, anyone who has not updated to [version 1.2.6](https://github.com/Chia-Network/chia-blockchain/releases/tag/1.2.6) will potentially experience issues with their node if it’s queuing is unable to handle the rate of updates… while we would rather you did not experience this pain at all, we feel there is a greater user pain in the size of the current DB and the time it takes to sync fresh, and we are motivated to deploy this temporary cluster to bring it down for you.

##So what _is_ a Bluebox Timelord?

As you may be aware, a [Timelord](https://github.com/Chia-Network/chia-blockchain/wiki/Timelords) is a server that generates the next block in the chain, with the fastest running one at any given moment being the authoritative server moving the chain forward. The Timelord infuses a winning proof of space into the blockchain, and then the process repeats. In order to do its job and do it well, a Timelord must be _fast_, at the expense of many other things including efficiency. This means the blocks it generates are uncompressed and ugly in the interest of speed. Enter the Bluebox… there can be any number of Blueboxes running, and their job is to scour the blockchain db and look for old blocks that are still uncompressed. They then clean up and compress a block, and then gossip it around to all of those nodes, who take this compressed block and perform a few confirmations, and then swap out the old bloated blocks in their DB for the new streamlined one. 

If you are a new node recently syncing, you will get all the already-compressed blocks from the start, but if you have an older node db that has been up and running for a long time, you may have a lot of uncompressed blocks that need to be manually swapped by your node. Unfortunately, the old setup had a bug with how it handled queueing these updates, and depending on your hardware it could push your node's memory to it's max as it struggled to keep up with the incoming queue.

This is why it's important you update to Version 1.2.6 as soon as feasable, as we plan to put some resources into bringing down the chain db over the coming weeks, and want to ensure you don't feel pain as we do it, and instead benefit from the cleanup!
