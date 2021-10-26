---
lang: en
layout: post
title:  "Chia Releases Public AWS Image for Bluebox Timelords"
date:   2021-10-12
author: "[Patrick Maslana](https://keybase.io/pmaslana3), [Chris Marslender](https://keybase.io/cmmarslender), and [J. Eckert](https://twitter.com/sargonas)"
---

# Chia Blockchain - Bluebox Timelord AMI Release

We have released a publicly accessible AMI (Amazon Machine Image) for Amazon Web Services. AWS makes it very fast and
easy to deploy a Bluebox Timelord to an EC2 instance that you can control and manage in your own AWS environment. Once 
the image has been deployed, no additional work will be required by the user to get the Bluebox Timelord online. After 
boot, both a Full Node and Timelord will start, and synchronization of the blockchain database will commence.

Creating an EC2 image with AWS’ Spot pricing is an inexpensive way to contribute to the blockchain. Spot instances are 
available as spare compute capacity, offering customers these products at heavily discounted rates.

## Reasons to Deploy

As the fastest Timelord runs, it quickly creates Proofs of Time. However, these proofs are large and uncompacted, 
resulting in the total size of the blockchain database becoming too big. Deploying a 
Bluebox Timelord is beneficial in compacting those large, pre-existing blocks, thereby reducing the database file’s
overall size, leading to a reduction in time and CPU workload on synchronizing the database. Although only one Timelord 
is required for driving the progression of the blockchain, many Bluebox 
Timelords are needed to maintain it efficiently. For more information regarding Timelords and Bluebox Timelords, 
please visit our [Wiki](https://github.com/Chia-Network/chia-blockchain/wiki/Timelords) page. 

What is the benefit to you for running one or more Bluebox Timelords? Ultimately, you are contributing to improving the
efficiency of the blockchain. A smaller database will allow new full nodes, or nodes with out-of-date databases, to 
synchronize and verify the blockchain faster.

## Deploying an AWS EC2 Instance in AWS

High processing power is not required for the Bluebox Timelords to efficiently work at compacting blocks. This is why 
older or lower performance hardware can be used to run it sufficiently. In the case of using AWS EC2 instances, there
are many instance types to choose from. Some considerations to take into account when looking at the instance types 
are:

*Storage Space* - The current size of the blockchain database file, as of 10/12/21, is approximately 22GB and 
will continue to grow. Therefore, some evaluation is needed to determine the storage capacity, based on instance life 
expectancy and the database growth rate. We have tested using EBS-backed storage, allowing for greater flexibility, 
compared to the mounted SSDs or HDDs of some instance types.

*CPU usage* - In the lower-cost tiers of EC2 instances, the typical types found are General Purpose 
(T*.xxxxx and M*.xxxxx) and Compute Optimized (C*.xxxxx). The T*.xxxxx type instances allow for burst usage of the CPU 
by allocating “CPU credits”. Running the vdf_clients on this type of instance can exhaust the credits in a short 
amount of time. By default, the T*.xxxxx types have unlimited billing, which results in AWS charging for the 
additional usage once the credits run out. We decided to preferentially choose Compute Optimized instances over the
General Purpose types.

*Pricing* - AWS provides Spot Instances at a reduced cost, typically between a 70-90% savings over the On-Demand price.
Since these spot instances are provided from unused AWS capacity, there is the possibility of the availability being 
removed and causing interruptions or the price fluctuating. A maximum price can be set, ensuring that instances are 
terminated when the spot price rises to that value.


Here is an example of the pricing at the rates as of 9/30/2021:
A c5.large instance spot price is $0.036 per hour of usage, compared to
its on-demand price of $0.10 per hour. Therefore, running a Bluebox Timelord will cost approximately $0.86 per 
day to run.
** Please note that these prices can fluctuate and will differ between regions,
along with the availability for specific instance types.

The EC2 instance can be created with this image manually, using auto-scaling groups, or building the 
instances/auto-scaling groups using Terraform. Chia manages a [GitHub repository](https://github.com/Chia-Network/public_bluebox_image), containing the code for building the 
AMI and includes a README file with amplifying information for deploying.


## Q&A

###### *Is there any compensation provided for running a Bluebox Timelord?*

There is no mechanism established to provide any kind of “payout” for running a Bluebox. The only reward at this time 
is the satisfaction of helping to improve the blockchain.

###### *Is there a place to get questions answered and talk to the Chia team about Timelords?*

Yes! You can visit our Keybase channel, chia_network.public.

###### *I have old hardware available that I can use as a Bluebox Timelord. How do I configure this?*

Chia-blockchain will need to be installed on the system and then configured to run as a Timelord, with specific 
settings for a Bluebox. These settings are identified in the [Wiki](https://github.com/Chia-Network/chia-blockchain/wiki/Timelords) page, Installing a Timelord - Bluebox Timelords section.

###### *Would choosing to run a Spot Instance result in my Bluebox Timelord going offline regularly, forcing me to spend a significant amount of time resyncing each time?*

While we can’t predict the weather on AWS instance availability for a given region, in our own testing of this, we’ve
experienced a week or more at a time of Spot Instance availability without interruption. Obviously, as the needs of AWS customers grow and change against their inventory of available instances in a given region, disruption might happen, but we’ve not experienced enough of it ourselves to see this as a concern at this time.
