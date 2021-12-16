---
lang: en
layout: post
title: "How do hard drives fail?"
date: 2021-12-16
author: "[Jonmichael Hands](https://twitter.com/lebanonjon)"
---

### Summary / TL:DR
HDDs (hard disk drives) have moving parts and are subject to failure from mechanical wear and tear through regular use, and external environmental factors like temperature. Use SMART to monitor the drive’s health to look for uncorrectable errors and reallocated sectors for indications of predictive failure.
### Chia farming workload is unique
When new interns came into our group at Intel over the years, I would grab a whiteboard and explain to them some basic concepts of how SSDs work, the difference between bandwidth and latency with some fancy analogies, and always end with an overview of RAID and storage durability. Keeping user data safe is job one when developing products that store user data. There are always arguments about which layer of the storage system hierarchy to put redundancy in, but whatever the method, there is always overhead for data protection. For storage veterans learning Chia this can be jarring at first. Chia does not store any user data... all the plot files are fungible and the farming workload is extremely light compared to a typical consumer or enterprise workload. In a series of posts, I will explain why Chia has such a unique storage workload that will inevitably lead to increased second use and circularity for storage. I hypothesize that even older drives with a few errors are perfectly suitable for farming Chia, even if ineligible for critical data storage. Understanding how storage devices report errors and perform self-monitoring is fundamental and, unfortunately, generally not well understood. Today I’m going to start with the bread and butter for Chia farming - hard drives.
### Hard Drives fail very differently than SSDs

Hard drives and [SSDs fail](https://youtu.be/ISK9U1FP1j0) in very different ways. SSDs are much more likely to fail due to firmware versus hardware issues. My background is in SSDs, and we spent a lot of time arguing that because HDDs have moving parts - they are intrinsically less reliable. This is true, and actually the root of how HDDs fail, but I think what is less understood is WHY these mechanical failures happen and what users can do to ensure the longevity of their HDD. Modern HDDs are made up of the physical disk, with high capacity HDDs using up to 9 platters in 16, 18, and 20TB models. An actuator is tied to the magnet assembly that hosts the heads that perform the read and write operations. When the heads are not in use, they are “parked” in a load/unload event. All these tiny operations over many years increase the chance of small particles being released internally to the drive, which is generally sealed with air or helium gas. When these particles are loose in the drive, there is a chance a head bumps into one while doing a read or write that will cause tiny damage to the platter, which the HDD firmware will now have to reallocate that data to somewhere else safe on the disk. This event is called a “reallocated sector,” and we will explore how to view these in SMART. A few of these are fine, and the disk can recover, but too many or reallocated sectors that are rapidly increasing is a good indication that a disk will fail.
### A quick note on how reliability is measured
Quality and reliability are different metrics. Quality is the goal of reducing time zero failures. Some lower-end drive models are not tested as robustly as high-end drive models in the factory prior to shipping, although they may have a higher chance of being DOA (dead on arrival). These are not to be confused with reliability issues, which are caused by extended use of the device. Enterprise HDDs are rated at 2M or 2.5M hours MTBF (Mean Time Between Failure), which equates to 0.44% and 0.35% AFR (Annual Failure Rate), respectively. MTBF and AFR are the same metrics expressed in different ways. Mean Time Between Failure is the total amount of drive hours before a failure is expected. This does not mean a single drive can last for 2 million hours; it means if you have a collection of drives running, you should expect one failure every 2M total drive power-on hours (the sum of all the drives). Annual Failure Rate is expressing that the individual drive has a 0.44% chance every year to fail, based on the data from a large population of drives. [Backblaze blog](https://www.backblaze.com/blog/backblaze-drive-stats-for-q3-2021/) has some nice measured info on a few different drive models, which is just one case study for HDD reliability in the field, and they show the [SMART attributes they monitor](https://www.backblaze.com/blog/what-smart-stats-indicate-hard-drive-failures/), which I found to be close to what I heard recommended from the manufacturers themselves.
### HDDs are SMART!
Self-Monitoring, Analysis, and Reporting Technology (SMART) feature set is defined in SATA, in the ATA Command Set specification. SMART is the way the drive has of telling the host system the status of the drive. The goal is to protect user data and minimize the amount of downtime by monitoring the device (SSD or HDD) for predictive failure and degradation. SMART and accompanying device statistics logs are a way for the drive to maintain a record of the state of the drive, the temperature, errors, and much more!
### Drives have moving parts
Because HDDs have moving parts, they are subject to higher impact from the physical environment which can include temperature, humidity, and external vibration. The internal parts are rated for a certain amount of movement in their lifetime. If these are exceeded, it is not a guarantee that there are failures, but statistically increases the likelihood.

#### Temperature
If you have seen a hard drive, you will know the disks are housed in a large enclosure with a top plate to keep the critical components, like the disks, isolated from the outside world. This also means that HDDs conduct heat extremely well and require airflow to keep them cool when operating. People spend their entire careers in device thermals, but I’ll try to summarize my recommendations here without offending anyone. A device manufacturer will often just say it is ok to run the drive up to the rated temperature on the specification sheet, which is the temperature at which quality and reliability are tested, but the truth is keeping the drive cool will increase the longevity.

| Temp Range | Description |
| :-: | :-: |
| 25-30°C | Optimal |
| 30-40°C | Perfectly fine! |
| 40-50°C | Warmer side, but still not highly impacting reliability |
| 50-60°C | Warning temps, try to find better drive cooling |
| >60°C | Will cause damage to the drive |

#### Shock and Vibration
As hard drives get bigger (in the industry, we call this areal density), the tracks per inch need to increase on the physical hard drive disks. The ability for the HDD to filter out external vibrations becomes even more challenging - with modern HDDs at 500,000 Tracks per Inch (50nm per track, or about [half the size of a virus](https://youtu.be/CMD7r4TKN3c)). Vibrations can come from drive-to-drive interactions or nearby equipment, fans, or other system components. It is critical to mount the drive properly! The carriers for servers are carefully designed to attenuate the rotational vibration of nearby disks. If you are venturing out into DIY for HDDs, monitor the SMART attributes `Raw_Read_Error_Rate and Seek_Error_Rate` to ensure that the drive is not experiencing errors due to excess external vibrations.
#### Things that impact HDD reliability over time
Most people over-analyze time as the main indicator of when an HDD will fail, but how and where the drive was used plays a major role in reliability. There isn’t a one- size fits all approach but understanding if one of these areas is way out of the rated specification will be a good indication of “why” an HDD is failing.

| Metric | Measurement | SMART attribute |
| :-: | :-: | :-: |
| Time | Power-on hours | 9 Power_On_Hours |
| Temperature |Degrees C | 194 Temperature_Celsius, Device Statistics Log - Temperature Statistics |
| Humidity | % non-condensing | N/A |
| Workload | TB read and writes |Device Statistics Log - Logical Sectors Written, Logical Sectors Read |
| Power savings | Load/Unload cycle | 192 Power-Off_Retract_Count<br /> 193 Load_Cycle_Count |
| Shock and vibration | Read errors on the head |1 Raw_Read_Error_Rate<br /> 7 Seek_Error_Rate |



#### SMART attributes to look for predictive failure
When there is physical damage to the HDD platters, the drive firmware has to physically reallocate data in a sector to a new sector, and retain that information of where that data is now located. It does this to prevent user data loss. This event is called a:`Reallocated_Event_Count`, which is triggered when a host writes new data to the LBA (logical block address) that needs to be reallocated. The drive firmware will keep a count of all the sectors that need to be reallocated in `Current_Pending_Sector`, and when those sectors are written to the firmware will reallocate the sectors and increment the attribute `Reallocated_Sector_Ct` for each sector and `Reallocated_Event_Count` for every time this happens. If your drive is full of plots for Chia farming, and you have mounted in read-only mode, you will likely not see any `Reallocated_Sector_Ct` because of this! If there are sectors that are physically damaged, check for `Current_Pending_Sector` incrementing higher. If you see either attribute 5 or 197 incrementing quickly, that could be an indication that a large number of particles are loose in the drive wreaking havoc, and an early indicator of failure. At some point, when these attributes reach the pre-set SMART limit, the drive will trip the SMART predictive fail flag.

| Attribute | Description | What it means |
| :-: | :-: | :-: |
| 5 Reallocated_Sector_Ct | Amount of sectors the drive firmware has needed to move/reallocate | If this is rising rapidly, that may mean particles are in the drive|
| 196 Reallocated_Event_Count | Number of times the drive firmware reallocated sectors (can do multiple at once) | Should track the moves from 197 > 5 |
| 197 Current_Pending_Sector | A sector that needs to be reallocated will show up here until the host writes to it, then will be moved to attribute 5 | If this is rising  rapidly, that may mean particles are in the drive |
| 198 Offline_Uncorrectable | Uncorrectable errors found by the drive during background scrubs | A high amount of uncorrectable errors means potential drive failure |



### SMART Self-Test
There are two types of SMART self-tests that can test a drive for failures. There is a short self-test that is supposed to be just a few minutes. There isn’t much that the drive can test in just a few minutes, but if a drive fails a short-test it is most certainly broken. The extended self-test does a full read of all the data on the drive, and will report any uncorrectable errors in `Offline_Uncorrectable` SMART attribute. The extended test does not, however, write any data, so it will not force any reallocation of sectors. One would have to do a full overwrite of zeros over the disk LBA span, which may not be a bad idea if an older drive is being used. The idea of the SMART self-test is for a system to run it periodically and have a result of just “good” or “bad” to make it easier for a data center operator. Personally, I find it more interesting to actually just look at the SMART data, as each individual metric has a threshold and normalized values.

### How to monitor SMART
I recommend using [smartctl](https://www.smartmontools.org/) to monitor SMART in Windows or Linux, but there is a myriad of tools available since the actual SMART logs are standardized in SATA.

```
sudo apt install smartmontools
sudo smartctl -a /dev/sda
```

In [Windows](https://sourceforge.net/projects/smartmontools/files/smartmontools/)
```C:\Program Files\smartmontools\bin> .\smartctl.exe -a /dev/sda```

On Mac 'brew install smartmontools'

To see the full logs, you can run a -x as well. If you want a deep dive on running smartctl and setting up smartd to monitor drives in the background, check out the video I did here.
[Chia farming - How Hard Drives fail!](https://youtu.be/SN6REW1VuPc)

#### Vendor Tools
While I prefer smartmontools (smartctl) for monitoring SMART, vendors do make their own tools that can be useful for things like firmware updates and parsing all the vendor-specific logs. Some people noticed on Seagate drives some higher numbers on `Raw_Read_Error_Rate` and `Seek_Error_Rate`.  Don’t freak out! They report the total bytes read and errors that needs to be parsed. I talked to Seagate about it and they plan to work with smartmontools to get that parsing fixed, but for now it works with their own tool called [SeaChest](https://www.seagate.com/support/software/seachest/)

```
sudo ./SeaChest_SMART_x86_64-redhat-linux  -d /dev/sg0 --smartAttributes analyzed
```
#### SAS Drives
SAS HDDs come in a few flavors, one of which is the 2.5in 10k or 15k RPM (which used to be the “performance” hard drive). You can imagine that SSDs have mostly killed these off, but some Chia farmers are using them for some temporary storage for plotting. For Chia farming, a higher capacity 3.5in HDD can be used. Generally, these tend to be slightly more expensive than SATA HDDs for a few reasons: they have dual ports for high availability or multi-host configurations, they operate at higher burst speeds (12Gbps vs 6Gbps), and have more configuration options including security and data protection information. The mechanical HDD underneath is still exactly the same though, so the same principles that we learned above apply to SAS HDDs, they just report them differently. In SAS, everything is a log page. When you do smartctl on a SAS drive it is just dumping and reporting the log pages. The log pages to look for in the parsed output of smartctl for predictive failure are `Elements in grown defect list` and `Error counter log`. Grown defects, which is also the terminology used in SSD as well for NAND defects and retired blocks, are similar to reallocated sectors for SATA HDDs discussed above.

SAS HDD predictive fail attributes
```
Grown Defect List
Read Errors Corrected by ReReads/ReWrites
Read Total Uncorrected Errors
Write Errors Corrected by ReReads/ReWrites
Write Total Uncorrected Errors
```
### NVMe SSDs (not the focus of this article)
If you are looking to monitor SMART on NVMe, I have written extensively about this topic as well! I was part of the NVM Express organization and we worked very hard to standardize as much of the SMART as possible so that all vendors report it in the same format.
[NVMe CLI](https://nvmexpress.org/open-source-nvme-management-utility-nvme-command-line-interface-nvme-cli/)
[Reading NVMe SMART in Windows and Linux](https://youtu.be/HTFWWPWRX6A)

### Summary
Anyone who is seriously farming in Chia will have come across some questionable drives on eBay or Craigslist, and encountered a drive failure or had to return a drive to a manufacturer. I like that smartmontools (smartctl) has made it reasonably easy to run a single command on Linux, Windows, or Mac and get a parsed version of the SMART logs across different storage interfaces, and I’m hoping everyone gets very familiar with monitoring SMART on hard drives.
