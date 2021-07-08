---
lang: en
layout: post
title:  "Chia and SSD Endurance"
date:   2021-05-24
author: "[Jonmichael Hands](https://twitter.com/LebanonJon)"
---

## Overview of Chia plotting and farming

The [Chia ](https://www.chia.net/)project is based on [proofs of space and time](https://www.chia.net/faq/), a brand new Nakamoto consensus allowing for underutilized storage capacity to secure the blockchain. Proofs of space are stored in plot files, where a commonly used k=32 plot is 101.3GiB (108.8 GB, or Gigabytes). Generating plot files is a process called plotting, which requires temporary storage space, compute and memory to create, sort, and compress the data into the final file. This process takes an estimated 256.6GB of temporary space, very commonly stored on SSDs to speed up the process, and approximately 1.3TiB of writes during the creation. The community realized early on that guidance was needed for SSD endurance, and a [wiki ](https://github.com/Chia-Network/chia-blockchain/wiki/SSD-Endurance)was created to help users select the proper SSD for plotting.


## SSD Market and Endurance

The new Chia cryptocurrency has received some inquiries regarding accelerated wear-out on SSDs. Solid-state drives are the standard for storing user data in current laptops and desktops, overtaking HDDs due to lower latency, lower power, improved battery life, smaller form factors, and better reliability than hard disk drives. The worldwide SSD market reached $33.2B [1], with consumer SSDs reaching 338M units and $17.6B [2] in 2020 alone. SSDs come in a large variety. SSDs segmentation occurs with different segments (consumer, datacenter, enterprise), interfaces (PCIe/NVMe, SATA, SAS), performance, endurance, and media type (MLC, TLC, QLC) for the 3D NAND technologies. Mainstream SSDs use 3D NAND flash non-volatile memory in the floating gate and charge-trap / replacement gate technology (major NAND vendors include Micron, Intel, Samsung V-NAND, Kioxia & WD BiCS). 3D NAND has a limited amount of write endurance or the amount of data written to a drive before wearing out (device failure or inability to read or write additional user data). SSDs are rated in TBW (terabytes written) or DWPD (drive writes per day) to show how much data can be written before wearing out. [[3](https://www.snia.org/forums/cmsi/ssd-endurance)] SSD vendors use the JESD219 spec from the JEDEC organization [[5](https://www.jedec.org/)] for this rating with standardized tests and reporting. Endurance is very well understood and can be accurately modeled and predicted. [[7](http://intel.com/endurance)]


## Chia plotting process and SSD selection

Chia plotting creates the cryptographic data stored later for the proofs of space (retrieved later to validate the network in a process called farming). Plotting is only required once upon creating the data and requires compute, memory, and ephemeral storage. Plotting is a write-intensive process due to creating random data, sorting, and compression. The Chia team and community advocate using data center class SSDs or consumer drives meant for high-end desktops and workstations with a high TBW endurance rating for the plotting process. If a user selects a high-endurance data center SSD, they can plot for up to 10 years [[4](https://github.com/Chia-Network/chia-blockchain/wiki/SSD-Endurance)] before wearing out the device during the plotting process. Consumer SSDs have been optimized for light client workloads (web browsing, office work, gaming) and are not suitable for Chia plotting. With the endurance requirements being more significant than average consumer SSDs, the consensus in the community is to avoid using these if possible for Chia plotting. The Chia team realizes that consumer SSDs are the ones that are generally available, and there are some models that have enough endurance where users can plot all the farming capacity they have and still have a surplus of endurance. A comparison using a device not designed for such a workload would not be an accurate representation of what is being used to plot in Chia.

<center><blockquote class="twitter-tweet"><p lang="en" dir="ltr">Also don&#39;t clean nonstick pans with steel wool, don&#39;t clean vegetables with soap, and don&#39;t use your phone as a doorstop. These aren&#39;t arguments against steel wool, soap, or phones, they&#39;re basic guidelines about using your tools properly.</p>&mdash; Bram Cohen (@bramcohen) <a href="https://twitter.com/bramcohen/status/1393991791590838277?ref_src=twsrc%5Etfw">May 16, 2021</a></blockquote> <script async src="https://platform.twitter.com/widgets.js" charset="utf-8"></script></center>
<br>

## HDD Plotting

While most users are selecting SSDs [[8](https://github.com/Chia-Network/chia-blockchain/wiki/Reference-Plotting-Hardware)] for Chia plotting to create the data faster and gain a competitive advantage, the software itself does run fine plotting directly to HDD, albeit slower. Mainstream HDDs are rated at 200-550TB/year workload to meet the reliability metrics on the specification sheet. A new hard drive being plotted directly to will likely be right up against this limit in the first year, but Chia farming is a write-once / read-many workload where writing additional data overtime is unnecessary. The farming process is lightweight and slight wear and tear on the drive once the drive is full of the plots needed to participate in the network.


## Other case studies for selecting the wrong flash device based on endurance requirements.

Tesla performed a voluntary recall [[6](https://www.tesla.com/support/8gb-emmc-recall-frequently-asked-questions)] after users reported MCU (Media Control Unit) failures. The root cause was the eMMC flash storage onboard not having enough write endurance to handle the logging that was being performed on the device. Calculating endurance is a very common prerequisite for determining the right fit for SSDs in any application. Thus, this was a good case study on the negative outcome of not understanding NAND flash's endurance requirements.

Macbooks that use the new Apple M1 chip saw users reporting accelerated SSD wear out, [9] possibly due to the increased use of swapping in MacOS and Rosetta 2.

## Questions or concerns, and note for SSD vendors

Please reach out to Jonmichael Hands, VP of Storage Business Development, if you are an SSD vendor, partner, cloud provider, or have any Chia and storage use questions. Send and email to hello@chia.net to get connected.


```
[1] Worldwide Solid State Drive Market Shares, 2020: Pandemic Drives Strong Growth for Enterprise and Client SSDs
[2] Forward Insights, Q1'21
[3] https://www.snia.org/forums/cmsi/ssd-endurance
[4] https://github.com/Chia-Network/chia-blockchain/wiki/SSD-Endurance
[5] https://www.jedec.org/
[6] https://www.tesla.com/support/8gb-emmc-recall-frequently-asked-questions
[7] http://intel.com/endurance
[8] https://github.com/Chia-Network/chia-blockchain/wiki/Reference-Plotting-Hardware
[9] https://www.macworld.com/article/338844/how-worried-should-you-be-about-your-m1-macs-ssd-lifespan.html
```
