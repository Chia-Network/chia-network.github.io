---
lang: en
order: 4
title: "How does Proof of Space and Proof of Time work?"
---

Proof of space can be thought of as a way to prove that you are keeping some storage unused on your hard-disk drive. Users of the Chia blockchain will “seed” unused space on their hard-disk drive by installing software which stores a collection of cryptographic numbers on the disk into “plots.” These users are called “farmers.” When the blockchain broadcasts a challenge for the next block, farmers can scan their plots to see if they have the hash that is closest to the challenge. A farmer’s probability of winning a block is the percentage of the total space that a farmer has compared to the entire network.

Proof of time requires a small period of time to pass between blocks. Proof of time is implemented by a Verifiable Delay Function that takes a certain amount of time to compute, but is very fast to verify. The key idea of a VDF is that they require sequential computation, and since having many parallel machines does not yield any benefit, electricity waste is minimized. There will likely be relatively few VDF servers (“Timelords”), as the fastest one will always finish first and it takes only one fast and fair Timelord on the network to complete a block and move the chain forward.
