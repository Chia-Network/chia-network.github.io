---
lang: en
layout: release
title:  "Chia Blockchain Testnet Alpha 1.1"
date: 2019-12-12
---

1. FullNode: A long running or low ulimit situation could cause an “out of files” issue which would stop new connection creation. Removed the underlying socket leak.
2. FullNode: Multiple SSH UI bugs fixed.
3. Timelord VDF submission and management logic upgraded.
4. Introducer now makes sure it only sends peer addresses to peers of peers that it can reach on port 8444 or their UPnP port.
5. Updated blspy requirement to address an issue in the underlying bls-signatures library.
6. Harvester: Farming  a plot of k = 30 or greater could lead to a segfault in the harvester.
7. Improperly in Alpha 1.0 Errata - was already fixed in 1.0:
    - Fixed - 4. FullNode: Ping pong messages and timeouts are not implemented yet.
    - Fixed - 7. FullNode: Certain loss of internet connectivity, like wifi dropping, can leave all connections zombied.
