---
lang: en
layout: post
title: "Chia Improvement Proposals"
date: 2022-02-14
author: "[Dan Perry](https://github.com/danieljperry)"
---


<p align="center"><img src="/assets/blog/chips.png" alt="CHIPs workflow" width="75%"></p>

<p style="text-align: center;"><em>A flow chart for CHIPs not to be confused with <a href="https://www.youtube.com/watch?v=xMi6C819Ii0"> CHiPS</a></em></p>

Have you ever read through Chia's source code or protocols and thought, _I have an idea to improve that?_ Well, now's your chance!
A [CHia Improvement Proposal](https://github.com/Chia-Network/chips "CHIPs GitHub repository") (CHIP) is a formal document for improving Chia's protocols, procedures, tooling, design decisions, or really anything related to Chia. CHIPs come in all sizes, from small (such as semantic changes to our nomenclature), to giant (such as a new VDF implementation).

Anyone (including you!) can create a proposal. However, before you get started, you should know a few things about CHIPs:

* CHIPs are reserved for broad ideas that require standardization between multiple projects. Most ideas to improve Chia should _not_ be CHIPs. For more info, see the "[What is a CHIP?](https://github.com/Chia-Network/chips/blob/main/CHIPs/chip-0001.md#what-is-a-chip)" section of CHIP0001.
* A CHIP can only be finalized when there is broad acceptance from the community. Jokes and proposals that require hard forks are not likely to go anywhere.
* A CHIP is a _formal_ process. You'll need to put in a lot of hard work to see your idea through to the finish line.
* The bigger your proposal, the more difficult it will be to gain acceptance.

Keeping these points in mind, here are some questions you're likely asking, along with their answers:

### Why are CHIPs needed?

As an open source project, Chia has always welcomed GitHub Pull Requests that improve our code. However, before today there was no standardized template or procedure through which anyone's idea could gain consensus from within the community. By introducing CHIPs, we're giving Chia's community the best opportunity to allow their ideas to flourish.

### Who controls this process?

An Editor is in charge of overseeing each individual CHIP. At first, most of the Editors will be Chia Network employees. This is necessary because Editors need to be deeply familiar with our codebase in order to guide most proposals from _Idea_ to _Final_. However, we'll have at least one community-based Editor from the beginning, with plans to decentralize control of the CHIPs process as the ecosystem matures over the coming years. Additionally, Editors are not allowed to turn down your idea because of a personal disagreement.

### What does it mean for a CHIP to reach _Final_ status?

It means that the CHIP can no longer be modified, but it won't necessarily be added to Chia's codebase. For example, some CHIPs don't require code changes, and others might not get implemented by core developers. On top of that, Chia is a decentralized blockchain, which will always be farmer-driven. Farmers can choose which version of Chia to run, so there is no way to guarantee that a CHIP in _Final_ status will be broadly adopted.

### I have an idea! Where do I get started?

You can start by reading [our very first CHIP](https://github.com/Chia-Network/chips/blob/main/CHIPs/chip-0001.md "CHIP 1"), which lays out the ground rules for proposing a CHIP (how meta of us). Next you'll need to make sure your idea is viable by vetting it in the #dev channel of our [Keybase](https://keybase.io/team/chia_network.public "Chia's Keybase forum") forum. Once you are sure your idea has legs, you can fill out our standard [template](https://github.com/Chia-Network/chips/blob/main/chip-template.md "The template all CHIPs must follow"). Follow the instructions carefully and be as thorough as possible. If an Editor accepts your proposal, it'll be entered into our system as a _Draft_.

Be warned: at this point, your journey will have only begun. There will still be a long process for your CHIP to move along the track to _Final_ status.

<br/>

Everyone is free to choose which software to run on their own computers, and ultimately, it is up to all of us to decide what Chia itself is. We feel that CHIPs are a way to guide our nascent blockchain to its best possible future.