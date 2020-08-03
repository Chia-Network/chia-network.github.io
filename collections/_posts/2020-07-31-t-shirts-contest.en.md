---
lang: en
layout: post
title:  "A T-shirt contest for Space Farmers"
date:   2020-07-31
author: "[Gene Hoffman](https://twitter.com/hoffmang)"
---

Now that the finalized plot format is out in Beta 1.8 and Beta 1.9, it's time for some fun.

Starting at block *7200* on the Beta 1.8/1.9 chain we're going to have a farming rewards race to block *9200*. The top 5 farmers by blocks won will get their choice of two rare T-shirts. We will count the winners by counting blocks rewarded to either Pool Public Key or Coibase Puzzle Hash as they are currently the same in Beta 1.9. You can get a proxy of who is [leading](https://www.chiaexplorer.com/charts/puzzlehashes) over the last 1000 blocks from the community created [Chia Explorer](https://www.chiaexplorer.com/).

<p align="center">
  <img src="/assets/chia-t-shirts-2020-07-31.jpg" alt="Green and Dark Gray Chia T-Shirts" />
</p>

There are two shirt styles to choose from - green and dark gray. These shirts are from a limited run that we gave to employees, advisors, investors and their families in 2017. As such we can guarantee that we have 5 XL's in dark gray, 3 XL's in green, and 2 L's in green. We probably have more dark gray L's but pandemic makes double checking more complicated than usual. We'll give the top 5 winners their first choice in descending order.

To win, you'll need to use the `chia keys sign/verify` command line tool that's new in beta 1.9. We will ask you to sign a message with the corresponding secret key so that we can be sure we're sending the T-shirt to the actual winner. If any of the top 5 farmers don't get in contact with Chia by block 9600 or choose to remain fully anonymous, we will move on to, for example, the number 6 farmer for another 400 blocks and repeat until we have 5 winners. Chia company owned farms/plots and Chia employees and contractors are not eligible to win and any of these plots will be removed from the final count. You will contact either hello@chia.net or [@hoffmang on Keybase](https://keybase.io/hoffmang) to provide a method of contact (Keybase, Twitter or email) and a name and shipping address to claim your prize T-shirt. We will also want to know a name or pseudonym that we can use to identify each winner in the contest results. In the very unlikely case of a tie between any two farmers, we will flip a coin in [Chia's #testnet Keybase](https://keybase.io/team/chia_network.public) chat to determine which farmer will be considered higher ranked.

There are a few more things to note. While we are planning for plots created with 1.8 and newer to work on mainnet, we can't guarantee that any plot with a [k](https://github.com/Chia-Network/chia-blockchain/wiki/k-sizes) less than 32 will be eligible. For plots with k's of 30 or 31 - these may not make the minimum plots size requirement for mainnet. We expect to speed the plotting process up 2x to 5x. The actual results of those optimization will drive the final minimum k size on mainnet. Any plot k less than 30 is definitely not going to work on mainnet. However, for this contest, all k's and all plots are eligible to compete and win.

Anyone can participate except Chia employees, Chia Network Inc, and residents of Cuba, the Crimea territory, Iran, <s>Italy</s>, North Korea, Syria; residents of any country or state where participation is illegal, prohibited, restricted or subject to tax or registration under applicable local laws; and any person who is subject to sanctions, blocking or other denial lists under U.S. law, including, but not limited to, persons on the US Treasury Department’s list of Specially Designated Nationals and Blocked Persons.

With that bit of legal out of the way you can download Chia Beta 1.9 for [Windows](https://download.chia.net/beta-1.9-win64/ChiaSetup-0.1.9.exe) or [MacOS](https://download.chia.net/beta-1.9-macos/Chia-0.1.9.dmg). Check out the [Install Guide](https://github.com/Chia-Network/chia-blockchain/wiki/INSTALL) for help and information on how to install on additional platforms like Linux and Raspberry Pi. Then peruse the [Quick Start Guide](https://github.com/Chia-Network/chia-blockchain/wiki/Quick-Start-Guide). Join us in the #testnet channel of our [Keybase chat](https://keybase.io/team/chia_network.public) and talk trash^H^H^H^H^H - politely root on your competitors!

Update 1: Residents of Italy can in fact participate...

Update 2: We've posted a [leaderboard](https://leaderboard.chia.net/) of Farmers by pool public key.
