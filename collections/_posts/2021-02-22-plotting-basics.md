---
lang: en
layout: post
title:  "Chia plotting basics"
date:   2021-02-22
author: "[Gene Hoffman](https://twitter.com/hoffmang)"
---


## Introduction

First it is important to know that there are two very different parts of being a Chia farmer. There is creating the plots or plotting and then there is farming the plots. In this post we are going to focus on the process of creating your plots. The types of machines and storage space are very different than the types of hardware you ultimately want to use to farm. You can see some [example farming rigs](https://github.com/Chia-Network/chia-blockchain/wiki/Reference-Farming-Hardware) on our very useful [repository wiki](https://github.com/Chia-Network/chia-blockchain/wiki).

**We initially recommend that you try plotting with what you have around**. The only caution about that is that you want to limit the amount of plots you create that use your internal/consumer grade SSD as the temporary space. SSDs have very different wear lives and we have detailed information on [SSD endurance](https://github.com/Chia-Network/chia-blockchain/wiki/SSD-Endurance).

You really never need to plot a plot with a [k size](https://github.com/Chia-Network/chia-blockchain/wiki/FAQ#how-big-are-plot-sizes-k) larger than 32. Those who do plot larger are either doing them to show off (and we encourage this for fun) or to [optimally fill the open space](https://plot-plan.chia.foxypool.io/) on a specific drive. A k32 will take up 101.3 GiB of space once completed but will need a total of 239 GiB of temporary space as it is being created. A single k32 plotting process never needs more than 239 GiB of space. One needs to be careful here as 239 gibibytes uses 1024 as its divisor where GB or gigabytes uses 1000 as the divisor. That means you will need 256.6 GB of temporary space and the final plot file will take 108.8 GB. A k32 plot can be done by one expert we know in just under 4 hours, but most experts are creating plots in 5 hours and most folks average around 9-12 hours.

Creating a plot is a process that will take RAM, CPU cycles, IO to your disks and it will use them differently in each of the four phases of plotting. Everyone wants a magic "right" answer or to use AI to figure out the optimal plotting strategy for their machine. However almost every machine is different along one of these parameters so you just have to try. Longer term we will be able query your machine and make some recommendations but that is not today. You really will have to test. And no, the experts in the various Keybase channels don't know your best settings either.

## Getting going

The first phase generates all of your proofs of space by creating seven tables of cryptographic hashes and saving them to your temporary directory. Phase 2 back-propagates through the hashes, phase 3 sorts and algorithmically compress these hashes in the temporary directory while starting to build the final file and phase 4 completes the file and moves it into your final plot destination.

One of the major bottlenecks is usually the total sustained write speed of the disk underneath your temporary directory. [We recommend](https://github.com/Chia-Network/chia-blockchain/wiki/FAQ#what-is-recommended-for-plotting) used datacenter SSD if you really want to go fast and not sacrifice consumer SSDs making plots. NVMe is faster than SAS and SAS is faster than SATA. This PC World [overview of storage technologies](https://www.pcworld.com/article/2899351/everything-you-need-to-know-about-nvme.html) can explain these acronyms and the differences. TBW, or terabytes written, is generally how SSD drive life is measured. One k32 writes 1.8TiB in non-bitfield mode and 1.6 TiB with bitfield enabled. More on bitfield in a moment.

Making the single fastest plot isn't generally the best plotting strategy however. Often you're getting amazing speed because you're using the turbo core of that multi core processor. The folks who plot the most have shown that you should measure in TB (TiB if you're old school like us) per day. The way to get the maximum TB/day is to plot lots of plots in parallel. Some of the top plotters use datacenter SSDs. Some use SAS drives. [Raid 0](https://en.wikipedia.org/wiki/Standard_RAID_levels#RAID_0) is often very handy to tie together a couple of small fast drives into one say 2TB partition so you could fit 5 k32 temporary spaces on that one virtual RAID drive.

All of that said, for my personal plotting I use a 2017 iMac and a [12TB Western Digital external drive](https://www.amazon.com/gp/product/B07X4V2M3B/) on USB 3.0 for both temporary and final directory, and I get a k32 about every 10 hours.

## Good assumptions

There are some good rules of thumb for now. These can change as we will be returning to making some plotting speed improvements after launch. First we need to explain bitfield versus no bitfield plotting. Originally, the plotter did not use bitfield back sorting. The bitfield back sort is theoretically faster than not using the bitfield and we already know that it saves 12% of total writes but requires more RAM. We have a hunch we can speed bitfield up 10% and make it work on more processors but that's not in there yet. What we do know is that, as long as you're ok with the 12% more total writes, no bitfield will work faster when SSD or fast SAS is your temporary directory. If your temporary directory is on a regular HDD, like mine is, bitfield is 20% faster than no bitfield. Older CPUs may not see the speed increase as much as noted above.

Returning to the rules, here are a few. Never touch the stripe size of 65536. No one has found a speed up over that value and we are likely removing it from the options list. (Update: as of 3/11/21 stripe size has been removed as an option.) You almost never want to use any bucket values other than 128. Less buckets requires more RAM for each plotting process. 64 buckets requires twice the RAM.

As far as number of threads are concerned you are generally going to want 2 to 4. More than 4 seems to have diminishing returns and 2 threads is a lot better than 1. More threads also require a bit more memory to successfully complete a plot. The threading is only used in phase 1 currently.

As of Chia 1.0.4, RAM requirements are almost identical between bitfield and no bitfield. This is a chart of the various RAM choices assuming a k32 with 128 buckets and 2 to 4 threads:

<!---
Updated RAM numbers provided by @pyl
-->

<center>
<style type="text/css">
.tg  {border-collapse:collapse;border-color:#ccc;border-spacing:0;}
.tg td{background-color:#fff;border-color:#ccc;border-style:solid;border-width:0px;color:#333;
  font-family:Arial, sans-serif;font-size:14px;overflow:hidden;padding:16px 8px;word-break:normal;}
.tg th{background-color:#f0f0f0;border-color:#ccc;border-style:solid;border-width:0px;color:#333;
  font-family:Arial, sans-serif;font-size:14px;font-weight:normal;overflow:hidden;padding:16px 8px;word-break:normal;}
.tg .tg-xxdm{border-color:inherit;font-family:Tahoma, Geneva, sans-serif !important;;font-size:16px;text-align:right;
  vertical-align:top}
.tg .tg-102i{background-color:#f9f9f9;border-color:inherit;font-family:Tahoma, Geneva, sans-serif !important;;font-size:16px;
  text-align:left;vertical-align:top}
.tg .tg-ui9f{border-color:inherit;font-family:Tahoma, Geneva, sans-serif !important;;font-size:16px;text-align:center;
  vertical-align:top}
.tg .tg-3k1g{background-color:#f9f9f9;border-color:inherit;font-family:Tahoma, Geneva, sans-serif !important;;font-size:16px;
  text-align:center;vertical-align:top}
</style>
<table class="tg">
<thead>
  <tr>
    <th class="tg-xxdm">RAM MiB:</th>
    <th class="tg-ui9f">Minimum</th>
    <th class="tg-ui9f">Medium</th>
    <th class="tg-ui9f">Maximum</th>
  </tr>
</thead>
<tbody>
  <tr>
    <td class="tg-102i">Bitfield</td>
    <td class="tg-3k1g">900</td>
    <td class="tg-3k1g">2640</td>
    <td class="tg-3k1g">3400</td>
  </tr>
  <tr>
    <td class="tg-ui9f">No Bitfield</td>
    <td class="tg-ui9f">900</td>
    <td class="tg-ui9f">2640</td>
    <td class="tg-ui9f">3400</td>
  </tr>
</tbody>
</table>
</center>
<br>

Below minimum your plot will fail. Medium is enough RAM that you'll get most speed improvements, but not all. This is useful when you're trying to get more plotting processes parallel and have limited RAM. Using anything over the maximum is wasting RAM as you will not plot any faster. We are pretty certain of the minimums and maximums but there is community debate about the medium values. We'll update this chart accordingly as we have better data. 

## Mastering plotting

Most people start plotting from the GUI. You can successfully complete a couple of plots in parallel from there to get the hang of things. As people choose to get more serious they migrate to the [command line](https://github.com/Chia-Network/chia-blockchain/wiki/CLI-Commands-Reference). It is worth noting that Windows suffers 5-10% slower plot times versus MacOS or Linux for now.

Once you get some experience you will probably want to know how to create more and more plots in parallel. Luckily we have a replay on YouTube of our [cocktails with plotting experts](https://youtu.be/wDVsZMDlQYw). They had much to share about their various approaches. Some used servers and datacenter SSD, some bought used servers and SAS drives for temporary directories, some expand their consumer/gaming machines, and some focused on lots of smaller used machines. Many of them have compiled a spreadsheet of [reference plotting hardware](https://github.com/Chia-Network/chia-blockchain/wiki/Reference-Plotting-Hardware) with plot speeds to help get you thinking about any hardware you might want to change or acquire and see how your plotting results measure up.

As you start parallel plotting you need to be careful to not over allocate memory when you are plotting. If you cause your operating system to swap, you are not going to be happy with your outcome. You don't have to be as careful with thread count.

It is also a very common plotting strategy to plot on say your gaming machine and then [move your plots](https://github.com/Chia-Network/chia-blockchain/wiki/Moving-plots) to a Raspberry Pi 4 with a lot of USB ports. All you need is your same 24 word mnemonic on both machines. Alternatively you can just run a [remote harvester](https://github.com/Chia-Network/chia-blockchain/wiki/Farming-on-many-machines) on your Pi and have it connect to your gaming machine where you are running node and farmer and only have your private keys on one machine.

## Learning more

Everyone trying to create plots should read through our [repository FAQ](https://github.com/Chia-Network/chia-blockchain/wiki/FAQ). It really does answer 90% of the questions you might have about plotting (and farming.)

Once you have read the FAQ, you'll find a supportive community in these channels on our [public Keybase channels](https://keybase.io/team/chia_network.public).

<center>
<style type="text/css">
.tg  {border-collapse:collapse;border-color:#ccc;border-spacing:0;}
.tg td{background-color:#fff;border-color:#ccc;border-style:solid;border-width:1px;color:#333;
  font-family:Arial, sans-serif;font-size:14px;overflow:hidden;padding:10px 5px;word-break:normal;}
.tg th{background-color:#f0f0f0;border-color:#ccc;border-style:solid;border-width:1px;color:#333;
  font-family:Arial, sans-serif;font-size:14px;font-weight:normal;overflow:hidden;padding:10px 5px;word-break:normal;}
.tg .tg-dshi{background-color:#f9f9f9;border-color:inherit;font-family:Tahoma, Geneva, sans-serif !important;;text-align:left;
  vertical-align:middle}
.tg .tg-bpho{border-color:inherit;font-family:Tahoma, Geneva, sans-serif !important;;font-weight:bold;text-align:center;
  vertical-align:middle}
.tg .tg-0ft5{border-color:inherit;font-family:Tahoma, Geneva, sans-serif !important;;text-align:left;vertical-align:middle}
</style>
<table class="tg">
<thead>
  <tr>
    <th class="tg-bpho">Keybase Channel</th>
    <th class="tg-bpho">Topic</th>
  </tr>
</thead>
<tbody>
  <tr>
    <td class="tg-dshi">#beginner</td>
    <td class="tg-dshi">For those questions you are afraid to ask</td>
  </tr>
  <tr>
    <td class="tg-0ft5">#testnet</td>
    <td class="tg-0ft5">For all things testnet - an intermediate skill level</td>
  </tr>
  <tr>
    <td class="tg-dshi">#plotting-hardware</td>
    <td class="tg-dshi">The expert plotters are here. Hardware, software and plotting strategy</td>
  </tr>
</tbody>
</table>
</center>

## Thanks

@pyl, @kiwihaitch, @psydafke, and @storage_jm all helped out on this post. The mistakes are mine. Should something need to be updated I will edit and post the errata down here.

## Updates

As of Chia version 1.0.4, RAM min/med/max values have been updated.
