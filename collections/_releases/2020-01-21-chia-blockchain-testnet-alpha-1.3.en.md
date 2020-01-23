---
lang: en
layout: release
title:  "Chia Blockchain Testnet Alpha 1.3"
date: 2020-01-21
---

1. FullNode performance improvements - Syncing up to the blockchain by importing all blocks is faster due to improvements in VDF verification speed and multithreading block verification. Also fixed a bug where the node may not sync if it restarts close to a tip.
2. VDF improvements - VDF verification and generation speed has increased and dependence on flint2 has been removed. We wish to thank Dr. William Hart (@wbhart) for dual licensing parts of his contributions in [FLINT](http://www.flintlib.org/) and [Antic](https://github.com/wbhart/antic) for inclusion in the Chia blockchain.
3. Implemented an RPC interface with JSON serialization for streamables - currently on port 8555 - and moved the ssh UI to use RPC.
4. Mongodb deprecated. Moved to [SQLite](https://www.sqlite.org/) for the blockchain database. This will require nodes to re-sync with the network. Luckily this is now faster.
5. Changed the displayed process names for harvester, farmer, fullnode, timelords, and VDFs to to chia_full node, chia_harvester, etc. Fixed a bug that could cause inadvertent shutdown of other processes like an ongoing plotting session when new chia services were started.
6. Added details on how to contribute in CONTRIBUTING.md. Thanks @RichardLitt. Also moved documentation from inside the repository to the [wiki](https://github.com/Chia-Network/chia-blockchain/wiki).
7. Added color logging and now chia_harvester will periodically announce which plots it is currently farming and their k sizes.
8. Fixed a typo in the UI. Hat tip to @lvcivs for the pr.
9. Clarified the minimum version of boost required to build timelord/VDFs. Hat tip @AdrianScott
10. Lots of smaller bug and documentation fixes.