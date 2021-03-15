---
lang: en
layout: post
title:  "Chia Mainnet Update - March 15"
date:   2021-03-15
author: "[Gene Hoffman](https://twitter.com/hoffmang)"
---

We want to give you an update on mainnet timing and our general plans around the launch.

First, as I write this, GitHub Actions is [down hard](https://www.githubstatus.com/incidents/s654n76c1bwr) so these plans already have a potential snag to them and are our current best estimate. We want the Chia blockchain to be right and not necessarily right now.

With the RC6 green flag launch we found issues around the green flag process for some and weight proof issues effecting lower powered devices like the Pi 4. We shipped [RC7](https://github.com/Chia-Network/chia-blockchain/releases/tag/1.0rc7) over the weekend to fix the green flag issues and it mostly did but we recently identified an additional issue that we believe warrants a second attempt at the green flag process. Additionally, the weight proof fixes require a new chain to test. Finally some users on MacOS are having issues plotting from the GUI that we would really prefer to resolve before 1.0 is out. Those users can plot from the CLI fine however.

As such we are now planning to release an RC8 on a brand new testnet blockchain using the green flag process. The flag will be red until approximately 10AM PDST March 16, 2021 (note that it is now Daylight Savings Time in the US.)

Assuming that test launch and RC8 testnet blockchain goes well, we will plan to release our 1.0 version of Chia during the day on 3/17/2021 and will **target 7AM PDST (14:00 UTC) on Friday March 19, 2021 for the green flag drop**. This time is targeted to include as many time zones during waking hours as possible with apologies to Hawaii, the South Pacific, and eastern Australia. This may slide one day to the right such that the green flag would drop Saturday 3/20/2021 instead.

There remains a 10% chance that we will postpone into the week of March 22, 2021 if RC8 is not as smooth as it needs to be.

Once these plans finalize we will announce them through the #announcement channel on our [public Keybase](https://keybase.io/team/chia_network.public), here on the [blog](https://www.chia.net/blog/), and via our various [email update lists and social media accounts](https://www.chia.net/contact/).
