---
lang: en
layout: post
title:  "Chia Joins the Open Compute Project"
date:   2021-08-30
author: "[Jonmichael Hands](https://twitter.com/LebanonJon)"
---

# Targeting a circular economy for storage

<p align="center">

<img src="/assets/blog/OCP.png" alt="Open Compute Project community member logo" width="50%">

</p>


Chia is excited to announce that we are joining the [Open Compute Project ](https://www.opencompute.org/)to contribute to sustainability in storage.

OCP is mainly known for open, modular, and vanity-free hardware that runs hyperscale data centers like Facebook and Microsoft, but [OCP 2.0 ](https://www.opencompute.org/blog/introducing-ocp-20)is laying out a new strategy to meet sustainability and circularity goals while ensuring it seeds future innovative technologies like open silicon and AI at scale.


## Why do we care?

The Chia Netspace during mainnet launch in March was just over 100 Petabytes (PB) and has grown to over 40 Exabytes (EB) today. We expect a large percentage of future growth to come from underutilized storage – [IDC ](https://idcdocserv.com/US47836321)believes there is an estimated 505 EB in consumer desktops and external storage alone. The next area we want to tackle is creating a more circular economy for hard drives. Chia farming is a perfect workload for used drives because the Chia network doesn't store any user data. It is common practice among hyperscale data centers and cloud service providers, who are the largest consumers of hard drives globally, to physically destroy hard drives (referred to in the industry as shredding or crushing) before they leave the data center. These same hyperscale data centers use advanced erasure coding and encryption prior to having customers' data on the disk - and then follow rigorous standards to securely erase the data on the drive before obtaining a certificate of sanitization.

"Typically, when a data center operator swaps out old drives for new ones — as they do every three to five years — the discarded drives are unceremoniously shredded." ([Source](https://grist.org/technology/can-you-recycle-a-hard-drive-google-is-quietly-trying-to-find-out/))

After all of this, the drive is destroyed instead of being recycled, recertified, and resold. We think this is a bad idea, and most of the folks we talked to agree but don't have the resources to tackle the many roadblocks to stop the practice. We would rather see these hard drives get reused for farming Chia than thrown into a landfill.

## Using fully recertified data center racks for farming Chia

Some companies are already doing a major part in turning the world of IT equipment into a circular economy, a few of which I have met in the past few months.

<p align="center">

<img src="/assets/blog/itrenew_horiz.jpg" alt="ITRenew logo" width="50%">

</p>

[ITRenew](https://www.itrenew.com/) is one of the leaders in sustainability for data centers and already partners with major hyperscale data centers for renewed and recertified IT equipment. They have flexible racks based on OCP open hardware, that happen to be the exact components that large vendors like Facebook use in production. This is fun for me since I worked on many of these projects in the past. I was Intel’s representative into the OCP Storage Workgroup and product manager for the data center SSDs - these racks are all too familiar.

ITRenew is the first company to offer a [fully recertified solution for farming Chia using open hardware](https://www.itrenew.com/sesame/chia-solution/) (over 99% of the components are sourced from recertified materials). They come at the rack level with a full 3-year warranty. Chia is all about storing the most amount of data in the smallest amount of space possible, at the lowest power consumption. The OCP JBOD, codename [Knox](https://github.com/facebookarchive/opencompute/blob/master/open_vault/spec/Open_Vault_Storage_Specification_v0.5.pdf), was literally one of the first OCP projects that housed many exabytes of storage to fuel the growth at Facebook and were designed to be dense, easy to service, and easy to scale. ITRenew now offers these in a dense rack filled with recertified hard drives, along with compute servers to do the plotting, in a full solution which they call “[Sesame](https://www.itrenew.com/sesame/)”.

<p align="center">

<img src="/assets/blog/knox.png" alt="Knox JBOD" width="70%">

</p>


## Data sanitization and risk management

I was trying to get to the root cause of why devices are being needlessly discarded instead of being safely reused. It all boils down to data security and risk management. Storage devices have this awesome feature that can instantly erase all the data on the drive, sometimes called secure erase, sanitize, or crypto erase. There is a lot of terminology like “SED” or Self Encrypting Drive that get thrown around and mean slightly different things to different vendors, but there is a formal document from NIST that is what most companies conform to. The [NIST 800-88](http://dx.doi.org/10.6028/NIST.SP.800-88r1) standard for Media Sanitization is what the industry conforms to when dealing with data on drives. I read it again after not having to do so in many years (hey...give me a break, I was surrounded by talented security experts at Intel). I found some nuances that I don’t believe are really well understood. What in this document is called “Cryptographic Erase” (CE) has been the best practice on SSDs for over a decade. It instantly securely erase all user data, changing the media encryption key and rendering the data unreadable. This is critical because consuming days of writing random data to a device is pretty useless if this cryptographic erase is done correctly. How do we know a vendor does it properly?

Here is what NIST has to say:

_“Federal agencies must use FIPS 140 validated encryption modules in order to have assurance that the conditions stated above have been verified for the SED”_

Ok...so if a device is certified to FIPS 140-2 or 140-3 we are ok to use CE to instantly sanitize the drive? FIPS is a collection of standards for how to correctly implement cryptographic modules (like SSDs and HDDs.) What about it leaving the organization? I don’t think ones and zeros care whether they are in an organization or not, either the data is purged or it is not.

---

2.6.1 When Not To Use CE To Purge Media - NIST SP 800-88 Rev. 1
* Do not use CE to purge media if the encryption was enabled after sensitive data was stored on the device without having been sanitized first.
* Do not use CE if it is unknown whether sensitive data was stored on the device without being sanitized prior to encryption.

<p align="center">

<img src="/assets/blog/nist80088.png" alt="NIST 800-88" width="70%">

</p>

Figure 4-1: Sanitization and Disposition Decision Flow

---

Many take the above recommendations as any device leaving organization control needs to be destroyed. This is downright dangerous and unintendedly causing a massive amount of e-waste.

I don’t believe that FIPS 140-2/3 full certification is required as long as you are working with a trusted vendor that has designed with the specifications in mind. Certification is a long and expensive process, but in the future, these specs are table stakes for most OEMs and hyperscalers. These same customers of devices already fully trust CE on the device, or otherwise they wouldn’t be qualified. I believe we can get to a point where the majority of drives can be instantly securely erased and then resold, reused, recycled to reduce a significant amount of e-waste.

You can find more information about SED from SSD and HDD vendors:

* [Seagate Instant Secure Erase](https://www.seagate.com/files/www-content/solutions-content/security-and-encryption/en-gb/docs/seagate-instant-secure-erase-deployment-options-tp627-2-1502gb.pdf)
* [Kioxia Security](https://business.kioxia.com/en-us/ssd/security.html)
* [IntelMAS CLI](https://www.intel.com/content/www/us/en/download/19520/intel-memory-and-storage-tool-cli-command-line-interface.html) and [GUI](https://www.intel.com/content/www/us/en/download/19543/intel-memory-and-storage-tool-gui.html?v=t)
* [NVMe format and Sanitize (open source tools)](https://nvmexpress.org/open-source-nvme-management-utility-nvme-command-line-interface-nvme-cli/)
* [WD Instant Secure Erase ](https://documents.westerndigital.com/content/dam/doc-library/en_us/assets/public/western-digital/collateral/tech-brief/tech-brief-instant-secure-erase-overview.pdf)

## What else can Chia do?

We already built a revolutionary consensus protocol called Proof of Space and Time that is much more energy-efficient and decentralized than cryptocurrencies today. Chia doesn’t sell any hardware so why do we care about contributing to OCP? Part of our mission isn’t just to be sustainable now, but to be able to grow and scale sustainably. I think the industry is headed in the right direction but Chia feels like having an outside view from the cryptocurrency and global financial markets that can help accelerate these positive trends. We also use a lot of storage and have in-house storage experts (ahem…). We are working on a larger initiative for a more circular economy for storage devices to promote hardware reuse and a significant reduction in carbon and e-waste with some of the biggest names in the field. We can’t wait to talk more about what we are doing, so stay tuned!