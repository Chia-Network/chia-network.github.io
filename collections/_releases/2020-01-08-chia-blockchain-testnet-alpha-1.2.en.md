---
lang: en
layout: release
title:  "Chia Blockchain Testnet Alpha 1.2"
date: 2020-01-08
---

1. Performance improvements:
    - Removes database access from blockchain, and handles headers instead of blocks
    - Avoid processing blocks and unfinished blocks that we have already seen.
    - Also adds test for load.
2. Improvements to plotting via lookup table - as much as 15% faster
3. Fixed a blockchain initialization bug
