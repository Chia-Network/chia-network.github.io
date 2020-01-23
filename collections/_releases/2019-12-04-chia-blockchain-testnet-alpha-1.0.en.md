---
lang: en
layout: release
title:  "Chia Blockchain Testnet Alpha 1.0"
date: 2019-12-04
---

1. We will move to DNS style peer discovery like Bitcoin. The introducer server is a stop gap solution.
2. Block validation is currently done in python. The C implementation should be ~3x faster.
3. Gossip protocol is not implemented yet.
4. Intentionally omitted.
5. There will not yet be transactions on the blockchain, and the Chialisp reference transaction wallets work in ledgersim only. Later we will add mempool for nodes, wallet protocol, cost calculations, and transactions to blocks.
6. A MacOS Catalina compiler bug means we de-optimize the compile of VDFs on Catalina due to clang issues, e.g. https://www.mail-archive.com/gmp-bugs@gmplib.org/msg00788.html We suggest you use the Timelords that are already on testnet anyway, as running a VDF on a workstation or laptop isn’t fun.
7. Intentionally omitted.
8. Plotting is slow and we expect to accelerate it. (e.g. memory mapped file I/O from the Chia proof of space contest has not been integrated yet, and that should speed things up by 15%). Example plot k values for an iMac (Retina 4K, 21.5-inch, 2017) - 3.4 GHz Quad-Core Intel Core i5 - 16 GB 2400 MHz DDR4 plotting on a USB 3.0 attached  4Tb RAID 1:

    | k  | plot time minutes | plot size Gb | working Gb |
    |---:|------------------:|-------------:|-----------:|
    | 26 | 27                | 1.3          |            |
    | 27 | 81                | 2.7          |            |
    | 28 | 260               | 5.6          | 30.3       |
    | 29 | 787               | 11.5         | 61         |

9. Once a timelord sends the first batch of iters, it might not continue to send the late ones (we need to keep the polling alive from the VDF process to the timelord.)
Timelords start a random discriminant with the maximum height (but should always prefer one that requires the least iterations, if that exists).
10. Work difficulty reset epochs will be shorter than mainnet to compensate for the expected dynamics of testnet.
