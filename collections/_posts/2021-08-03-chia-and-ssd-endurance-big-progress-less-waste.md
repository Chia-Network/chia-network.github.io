---
lang: en
layout: post
title:  "Chia and SSD Endurance - Big Progress, Less Waste"
date:   2021-08-03
author: "[Jonmichael Hands](https://twitter.com/LebanonJon)"
---

Earlier this year, I wrote a blog post about [Chia and SSD endurance](https://www.chia.net/2021/05/24/SSD-endurance.html). The [Chia proof of space construction](https://www.chia.net/assets/Chia_Proof_of_Space_Construction_v1.1.pdf) requires a lot of sorting on temporary storage space to make the plot format secure and efficient for quick verification later in farming. The Chia plotting workload is only required to be performed once per plot during the initial creation, where the final plot file lives on a low power storage device for the remainder of the years of farming. The summary of the post was to use high-endurance data center or enterprise SSDs for Chia plotting (used is great!) and avoid using mainstream consumer SSDs because they are not designed for sustained write or high endurance workloads. It seems like the mainstream press has been fixated on Chia wearing out SSDs and thus causing e-waste. This is something we take seriously, as we have initiatives to make Chia a sustainable cryptocurrency. I have some updates I would like to share in the advancements in plotting, the current progress on sustainability for Chia, and the plotting power analysis I did for the latest [Chiapower.org](https://chiapower.org/) update.

A lot has happened in the short time since I wrote that post!


## New plotters that use DRAM to reduce or eliminate SSD writes

There have been two major independent rewrites of the Chia plotter by community members that can use DRAM to help reduce or eliminate the SSD writes entirely. The [madMAx plotter ](https://github.com/madMAx43v3r/chia-plotter)has been very popular, and 128GB of DRAM can reduce the writes to the SSD by 75%, while 256GB can eliminate it.

[Bladebit](https://github.com/harold-b/bladebit), by Harold Brenes, is a complete rewrite of the Chia plotting software to perform the entire plot creation process in memory only. This is much faster and more efficient and requires only enough storage to write the final plot file. This plotter is not geared towards mainstream consumers as it requires a larger amount of DRAM found only on higher-end servers but delivers much faster and more efficient performance.

Now that the highly requested [pooling ](https://www.chia.net/2021/07/07/official-pooling-launched.en.html)feature is out (and very well received), we did want to reward community members working to make plotting more efficient by holding a community plotting competition. More details to come!


## New Chia optimized SSDs for plotting

We saw a few surprise announcements of SSDs optimized for Chia plotting, so I got on a call with Phison, one of the largest SSD controller manufacturers, to figure out the enhancements they did to support this effort.

[Watch: Chia Optimized Plotting SSD - Interview with Phison](https://youtu.be/fl-gXnNhz6k)

Enterprise SSDs have had high endurance and can last over a decade. The capability for high endurance on SSDs has always been a tradeoff of cost, as storing fewer bits per cell significantly increases the NAND cell’s endurance and uses higher-grade NAND and levels of error correction. I was surprised by some of the additional firmware, error correction, and AI capabilities they were able to utilize to get even more endurance out of a current SSD design. The 2TB version of the “maker” SSD optimized for Chia plotting has 54 PBW (that is Petabytes written or 54,000 TBW), which can plot between 4-6PB of plots before wearing out. Safe to say, this is a huge win for serious farmers and desktop enthusiasts who wanted to use their current high-end desktops for sustained plotting, where they can resell their drive to another farmer safely after use because it has so much surplus endurance!


<p align="center">
<img src="/assets/SMART-jm-screenshot.png" alt="screenshot of SMART results">
</p>


Yes...the sample they sent me has done 1.44 PB of writes and *only 1% used* (the NVMe SMART percent used indicator only moves 1% at a time).

PNY, who is using this SSD technology in their new SSDs, [PNY LX2030 and LX3030 M.2 NVMe Gen3](https://www.pny.com.tw/en/news-detail/PNY-Chia-mining-SSD/), worked with Chia to create a Chia optimized plotting badge, indicating these drives have high endurance and sustained bandwidth for plotting.


<p align="center">
<img src="/assets/PNY-plotripper-01.png" alt="PNY Plotripper SSD product photo with Chia optimized badge" width="75%">
</p>


We have seen additional announcements of the [Sabrent Plotripper](https://www.sabrent.com/plotripper/) and [Adata Prospector 970 and 950 PCIe M. 2](https://www.storagenewsletter.com/2021/07/27/adata-prospector-970-and-950-pcie-m-2-up-to-2tb-ssd-with-high-tbw/). We are hoping with the advancements in plotting software that even lower capacity and high endurance SSDs will be brought to market with a lower entry cost point for smaller farmers, who can share the drives and help each other out plotting.

Speaking of other creative solutions for Chia plotting,[ NGD Systems](https://www.ngdsystems.com/), who is one of the leaders in computational Storage SSDs, released an [SSD that can plot itself](https://www.ngdsystems.com/Auto-Plotting-SSDs-Provide-Increased-Plots-at-No-Cost)!

Prior to Chia, I spent 10 years at Intel in the Non-Volatile Memory Solutions Group. I was there for the development and launch of 3D XPoint memory in 2015, which Intel now calls Optane in their products. This was the first fundamentally [new memory technology](https://www.intel.com/content/www/us/en/architecture-and-technology/intel-optane-technology/benefits-and-history-documentary.html) in decades, which some call “storage-class memory,” designed to be fast like DRAM but also persistent and write in place using resistive cells. This tech powers [persistent memory](https://www.intel.com/content/www/us/en/products/docs/memory-storage/optane-persistent-memory/optane-persistent-memory-200-series-brief.html) as well as the fastest NVMe SSD in the world, the [Optane P5800X](https://www.intel.com/content/www/us/en/products/docs/memory-storage/solid-state-drives/data-center-ssds/optane-ssd-p5800x-p5801x-brief.html). Of course, when I finally got my sample, the first thing I was going to test was [Chia plotting](https://youtu.be/PCViU6vhdcs).

After lots of back and forth with a few of my old colleagues at Intel that were testing Chia, we basically broke all the records on plotting with the new Ice Lake Servers and Optane. I worked with Allison Goodman, who is one of the most senior women technical leaders at Intel and a good friend, to publish some data on why [Optane is a great fit for Chia plotting](https://medium.com/intel-tech/intel-optane-ssd-is-the-magic-key-to-unlocking-the-latest-cryptocurrency-chia-a7b921410579 ).


## Is Chia wearing out a lot of SSDs?

I work very closely with the major storage vendors. In May I asked them to let me know if they started seeing accelerated returns or consumers trying to return drives out of warranty that had been worn out. I’m still asking...and still, a wave of broken SSDs hasn’t hit. Why is this? I have a few theories.


### 1) Many SSDs incorrectly report endurance in SMART percentage used

In the plotting channel in [Keybase](https://keybase.io/team/chia_network.public), I have the luxury of seeing tons of screenshots of people’s SSD SMART output. SMART percentage used should track NAND program erase cycles to accurately gauge the SSD wear. The TBW on the box is supposed to be dictated by the [JEDEC JESD219](https://www.jedec.org/) client spec so that users can compare drives against one another.

<p align="center">
<img src="/assets/JESD219-client-spec.png" alt="PNY Plotripper SSD product photo with Chia optimized badge" width="75%">
</p>
<p align="center" style="color:#808080;font-size:12px;">
Source: <a href="https://www.snia.org/forums/cmsi/ssd-endurance" >SNIA SSD Endurance</a>, JEDEC
</p>

Some choose not to use this spec, some don’t disclose, and some just pick the worst-case Write Amplification Factor (WAF) to set their TBW. In Chia plotting, with TRIM enabled, the WAF will actually be low, about 1.5-2, when the drive is close to full, closer to 1 if the drive has a lot of spare area, unused space, overprovisioning.

The firmware in some drive models are tracking percentage used on host writes alone compared to the TBW on the box (which is estimated with a specific WAF, somewhere between 2-5) and NOT NAND P/E cycles. What does this mean? You can go well past 100% percentage used endurance on the drive before the drive stops functioning, as many users have reported screenshots where drives just stop at 255% (per NVMe spec)

Enterprise drives, and vendors that support data center and consumer SSDs (Samsung, Intel, WD, Micron, etc.) report SMART percentage used correctly.

Even a low-end consumer drive can plot a few hundred TB before wearing out if the WAF is low – most people are finding this out. Plotting while the drive is over 100% percentage used is like driving without a speedometer. You will know when the drive fails, but there are some SMART indicators like error log and reserved spares that should trigger when a drive is actually failing (I did a long overview of [How SSDs Fail](https://youtu.be/ISK9U1FP1j0) last year!). Different model drives behave differently, especially in the enterprise space where silent data corruption will get a vendor immediately disqualified from any hyperscale or large server OEM qualification.

To summarize, looking at the [SSD Endurance Wiki spreadsheet](https://docs.google.com/spreadsheets/d/1mNUYRWeJUaijEZXupwP5k6IuATZGj1FB/edit#gid=1857251151), you can see that many used data center SSDs can plot for many years and PBs of plots before wearing out, and even low-end consumer drives can plot a few hundred TB before wearing out.


### 2) Many users took Chia’s advice and bought used enterprise SSDs to do their plotting.

I estimate about 50% of Chia plotters are using enterprise or data center SSDs...maybe more. Most of them are either still plotting and have used only a fraction of the endurance or happily plotted their drives and resold the equipment to other farmers or someone else on Craigslist or eBay.


### 3) Consumers are not dumb!

As I found out through a lot of discussion in [Keybase](https://keybase.io/team/chia_network.public), consumers are doing a ton of research on SSDs before buying them for dedicated plotting. The other thing that people are doing, which is smart (no pun intended), is using their SSD until it gets to about 70-80% used, then putting it into their gaming machine. This gets the best use out of the drive since typical consumer workloads like gaming don’t require many writes over the lifetime of the drive.


### 4) Direct to HDD Plotting

Although it is slower, a lot of Chia plotters have indicated that they are plotting directly to their hard drives or reusing old 10k or 15k SAS HDDs (that go for as low as $15 on eBay) in servers. It is hard to estimate the percentage of Chia users using the method, but it is a non-zero percentage.


### 5) The number of failed drives is in the noise

Like everything, I busted out Excel and I made a model.


<p align="center">
<img src="/assets/forward-insights-ssd-report-q1-21.png" alt="bar graph of Forward Insights SSD Report Q1’21" width="75%">
</p>
<p align="center" style="color:#808080;font-size:12px;">
Source: Forward Insights SSD Report Q1’21
</p>

[Forward Insights](https://www.forward-insights.com/index.html) has the total SSD market at 435 Million units for 2021. Let me pause for you to think about that for a second...If the typical consumer drive has 1.5 million hour MTBF (this is the same as 0.584% annual failure rate) and enterprise drives have 2M hr (0.44% afr), my math suggests that an estimated **2.6 million** newly purchased SSDs will fail in 2021 alone.

Suppose I use the Chia SSD Endurance wiki to estimate the total amount of plots each class of drive can deliver before wearing out and take my percentage of the Netspace that I think each class of plotting drives a user is using. In that case, I can estimate the total SSDs worth of endurance consumed. Remember, this isn’t the same as actual SSD failures due to Chia because we don’t know how many drives were purchased for the sole purpose of plotting in Chia. I assume people are actively trying not to completely wear out the SSD to continue to use them after. Still, we will calculate this in the number of drives worth of endurance for ease of calculation.

At 32EiB of Netspace, I estimate that Chia has contributed between a 1-2% increase on the failures observed of total number of newly purchased drives in 2021, and over the last three years of drives that are running, a total of ~0.5%.


## Summary

A lot has happened since the Chia mainnet launch. New plotters have emerged that significantly reduce or eliminate any SSD wear, new plotting SSDs for consumers optimized for Chia with high sustained bandwidth and high endurance, and the exploration of using computational storage from NGD and storage-class memory with insanely high endurance, such as Intel Optane, for plotting.

Chia is monitoring the storage industry closely, working with our partners on the Chia plotting and farming workloads, market analysis, sustainability programs, recycling, e-waste, and power consumption improvements so that Chia can grow sustainably. We have a lot more exciting news on this front coming this year with some major partners.
