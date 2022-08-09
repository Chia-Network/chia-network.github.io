---
lang: en
layout: post
title:  "Announcing Bladebit 2.0"
date:   2022-08-08
author: "[Jonmichael Hands](mailto:jm@chia.net), VP Storage and [Harold Brenes](mailto:h.brenes@chia.net), Developer of Bladebit, eater of garlic and broccoli"
---

Chia is releasing new plotting software called Bladebit Disk, utilizing the high-performance code from the in-memory plotter Bladebit, with a new architecture optimized for mainstream storage devices (solid state drives, and hard disk drives). Major new features include DRAM caching to reduce writes and improve performance and brand new architecture for disk io that improves SSD endurance and takes advantage of high bandwidth SSDs, like PCIe 4.0. The plotter has broad compatibility across device types and operating systems as well as low minimum requirements for embedded and entry-level systems.

## Plotting History 

I love Chia plotting. I was absolutely fascinated with proofs of space and the connection with storage, building plotting rigs, and helping people learn about SSD technology. I've been trying for years to educate people about how SSDs and technology like PCIe and NVMe works, although storage was just never as popular as other desktop gaming components. I was very surprised early on that I was one of the only people in the storage industry closely tracking Chia, after all, a major new cryptocurrency based on storage...which ultimately led to me joining Chia in May 2021.

We were still in rapid exponential growth of the network, and I was a very popular guy with everyone who wanted in on the Chia madness. It's not shocking, Chia launched the mainnet about a month before the Bitcoin all-time high, and with the most revolutionary blockchain technology since Bitcoin and Ethereum, people were speculating on the price. We heard from folks in China that the farmers there around this time were indeed treating it like the next Bitcoin, and quickly hard drives sold out in China, then a few months later in the US.

Almost hard to imagine that a large chunk of the current Chia Netspace was plotted with the original Chiapos (Chia proof of space) code. A single plot took over 12 hours to create. My now barbaric scripts and very poorly filmed YouTube videos were the blueprint for tens of thousands of Chia farmers to learn how to select an SSD, and automate plotting.

Chia plotting is a write-intensive workload, which is extremely rare in a consumer use case. Most gaming and productivity workloads rarely write large amounts of data. I spent a lot of time early in the Keybase educating our community and the Chia team on what this meant, and why these magical devices called data center SSDs, which were designed for high sustained storage workloads and endurance made for enterprise databases, were a great fit for Chia plotting.

Early FUD pretty much focused on Chia plotting wearing out low-end consumer devices in a short amount of time, and spurred a lot of misinformation and confusion about Chia plotting and farming. For the majority of small farmers, they can plot hundreds of terabytes on even a cheap consumer SSD without wearing it out, but this did not stop the press from relentlessly coming after Chia. Reviewers never took the time to learn about the difference between plotting (which only has to be done once per file) and farming. They just thought Chia chewed up mountains of SSDs (which our community has reminded them, this is not in fact even after a year later and no piles of dead SSDs). I wrote extensively about it in [blogs](https://www.chia.net/2021/08/03/chia-and-ssd-endurance-big-progress-less-waste.html) and [interviews](https://www.backblaze.com/blog/next-steps-for-chia-in-their-own-words/), but the real magic happened in the summer of last year when Chia was introducing a little plotting competition. Bram and Gene had some ideas on how we could incentivize community development, as we knew there were much better solutions than the reference plotter that were possible. [madMAx Chia plotter](https://github.com/madMAx43v3r/chia-plotter) come out, which now could complete a plot in 15 minutes or more than 50x faster than the reference code. It seemed like the plotting competition was all but canceled before we started, and then I stumbled on [Bladebit](https://github.com/Chia-Network/bladebit) a new in-memory plotter being developed by Harold Brenes.

This was the holy grail. Creating a plot completely in-memory. No storage writes, plots in 5 minutes, extremely energy efficient. The plotting competition was really done before we officially announced it. We had a better idea...offer Harold a job at Chia.

Bladebit in-memory only has one downside, it requires a very high-end workstation or server with a ton of memory (416GB). We can make those systems available via plotting as a service ala [Akash](https://docs.akash.network/deploy/chia-on-akash), which is another great tool in the plotting tool kit. But we wanted to figure out a way to bring the Bladebit goodness to our standard Chia farmer with a desktop PC.

People still don't get it. Chia and proof of space and time are not a "niche" cryptocurrency platform and consensus mechanism. There will be a lot more plotting done in the future. Chia will rise and we will see a massive influx of new farmers. Chia plotting, which is arguably the hardest part of getting setup for Chia farming, needs to be even more accessible. We will eventually see hundreds of exabytes of storage on the Chia Netspace, which is still why we are investing resources in developing a completely in-house plotter with Bladebit disk.

## Introducing bladebit disk

Plotting is still too hard for average users, that are not tech enthusiasts. We wanted to create a plotter that is high-performance, but had low minimum requirements and compatibility across a broad set of system configurations. We have a lot of Chia farmers using a mainstream desktop for plotting. A high-end gaming machine is a great Chia plotter with the addition of an SSD with good sustained write performance and endurance. We wanted Bladebit Disk to have performance and endurance advantages on a broader set of systems with 16, 32, 64, and 128GB of DRAM, as well as a variety of consumer, enthusiast, data center, and enterprise SSDs.

## Why Bladebit matters


-   Still uses temporary storage to create plots, accessible to the majority of farmers

-   Very low minimum memory requirements (2-4G) for low resource plotting in embedded or entry-level systems

-   Cross-platform and OS compatibility

-   Sequential writes can better take advantage of SSD burst performance and reduce SSD wear by reducing write amplification factor.

-   Can use DRAM write cache to significantly reduce SSD writes and can take advantage of any extra increments (no minimum required)

-   Takes full advantage of increased disk bandwidth from PCIe 4.0

-   Pipelined performance to max out CPU

-   Plotting time reduction across the majority of system types [1]

-   2-4x faster plotting on high-end CPU and storage systems like high-end desktop, workstations and servers

## Proof Points

<iframe width="669" height="385" seamless frameborder="0" scrolling="no" src="https://docs.google.com/spreadsheets/d/e/2PACX-1vS0M0ta2x759DXMu9ATQ364T3p7Fb2Xadmb_LkyE7l8Qc-lYlKVB451a-CP1Y8cknSWqa-wlZOQe_4k/pubchart?oid=227095624&amp;format=interactive"></iframe>
[1] Plotting time (minutes) across desktop, workstation, and server systems

| System Name                           | Plotting time reduction |
| ------------------------------------- | ----------------------- |
| Cascade Lake mid-range server         | \-49.71%                |
| Threadripper Pro high-end workstation | \-16.35%                |
| budget build i7 desktop               | \-7.55%                 |
| Ice Lake high-end server              | \-74.04%                |

## Disk write table

Bladebit disk does sequential read and writes with a measured write amplification factor of 1. You can read more about endurance basics [here](https://www.snia.org/forums/cmsi/ssd-endurance), but the important thing to note about WAF=1 is that a user will generally observe between 2-6x the rated TBW limit of an SSD! This means a cheap consumer 1TB NVMe ($80) can plot 1-2 petabytes of plots before the drive wearing out! The Safe to say the average desktop plotter will not get close to wearing out an SSD with plotting.

|Plotter|Cache / Ramdisk|Writes per K=32|
|:----|:----|:----|
|Chiapos beta (2020)|0|1.8 TBW|
|Chiapos 2021|0|1.4 TBW|
|madMAx Chia_plot|0|1.43 TBW|
|madMAx Chia_plot|110G|0.396 TBW|
|Bladebit Disk|0|1.225 TBW|
|Bladebit Disk|64G|Need to measure|
|Bladebit Disk|>96G|0.381 TBW|

## Release Schedule for Bladebit Ddisk

The alpha2 release is available now for running on the command line. If you want to use the GUI, please [join the new beta program](/2022/08/08/help-test-bladebit-2-with-our-new-chia-beta-program.en.html)! Bladebit will be the first piece of software that goes through the Chia beta program, you can learn more about it here!

<p style="text-align: center;"><a class="button primary-button" href="https://github.com/Chia-Network/bladebit/releases" target="_blank">Download the Alpha</a></p>
---
## Footnotes

### System Configuration

|System Name|Cascade Lake|Threadripper Pro 5000|budget build i7|Ice Lake|
|:----|:----|:----|:----|:----|
|OS|5.15.0-40-generic|5.15.0-41-generic|5.15.0-40-generic|5.15.0-27-generic|
|Motherboard / Server|SYS-1029U-TN10RT|Lenovo Thinkstation P620|Z590-A PRO|Ultra SuperServer SYS-120U-TNR|
|CPU|Intel Xeon Gold 6226R CPU @ 2.90GHz (Turbo 3.9)|AMD Ryzen Threadripper PRO 5995WX 64-Cores|Intel i7-10700|Intel® Xeon® Gold 6338 Processor|
|DRAM (Size, Type, MHz, etc)|DDR4 @ 2933 12 x 16GB|64GB x8 DDR4 at 3200MT/s|2x 16GB @ 3200 MHz|32x 16GB DDR4 ECC RDIMM, 3200MT/s|
|SSD|2x P5510 at PCIe 3.0|1x P5510 at gen 3|Phison SLC|2x Kioxia CM6 3.2TB|
|Config|mdadm raid0, xfs|xfs|xfs|RAID0 mdadm, xfs|
|buckets|64|64|256|64|
|cache|0|300|0|300|
