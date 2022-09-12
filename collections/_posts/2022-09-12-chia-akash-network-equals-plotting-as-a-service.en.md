---
lang: en
layout: post
title:  "Chia x Akash Network = Plotting as a Service"
date:   2022-09-09
author: "[Jonmichael Hands](/profiles/jonmichael-hands/), VP Storage"
---

<p align="center"><img src="/assets/blog/chiaxakash.png" alt="Chia and Akash graphic" width="300px"></p>

## How much does it cost to make a plot?

What should be an easy calculation has a bit of nuance. I started creating a [model ](https://docs.google.com/spreadsheets/d/19K1YSVuddoI5-PfTAAdUFu_pHD-4a7x17sfCXpfJ5ts/edit?usp=sharing)with a three-year total cost of ownership for the plotting hardware, but the tricky part was how to treat the hardware utilization and depreciation. The higher the utilization of the plotter, the better the cost per plot will be. This is intuitive. Because plotters are just computers, servers, or workstations with additional utility outside of plotting, it is best to ensure you have identified a second use for the hardware after the plotting is complete. For the calculations here, we will assume a farmer is investing in a dedicated plotter.

These are the general inputs we will need for the simple model

-   Cost of plotter

-   Time to make a plot

-   Power consumed by plotter

-   Local electricity cost

-   The total amount of capacity to plot

From this, we can calculate the energy efficiency of plotting in Joules or kWh per terabyte or per k=32 plot, and the amount of time it will take to complete the plotting.

The energy is very straightforward; you can take the energy efficiency metric and multiply it by the total amount of storage to plot. The capital expenditures (CapEx), which I've just called "plotter cost," need to be amortized over time. You can pick a period, say three years, but then you have to assume a specific utilization. I settled on using the total time the plotter is on until all the storage specified is full.

We can take an easy example for the average home plotter with a gaming desktop that costs $600 and can create a plot in 30 minutes at 120W of power.

<p align="center"><img src="/assets/blog/costperplotgraph.png" alt="Bar graph cost per plot vs terabytes" width="300px"></p>

You can see here we don't hit under 15 cents per plot until the total amount plotted is over 500TB! Akash launched a summer sale of 10 cents per plot with a few providers this July, and has had multiple providers consistently under 15 cents per plot. In a decentralized and free market, price is determined by supply and demand. The competitive marketplace is excellent for end users.

## Plotting as a service

There are a few plotting as service providers out there, but Chia has partnered with Akash. Akash Network is a Distributed Peer-to-Peer Marketplace for Cloud Compute. As a decentralized web3 platform, anyone with idle hardware can join as a provider, and anyone can use the service to download plots. Since Akash is peer-to-peer, there is no charge for egress (paying for the network to download the plots), which makes plotting a really exciting use case.

As we explored in the model above, plotting hardware gets cheaper the more it is used. Ideally, if someone gets very good efficiency and utilization out of a plotter, it can benefit the provider (earn money on idle hardware) and the end user/farmer (lower cost to plot drives). This is a huge win on both sides, as it creates a marketplace between the people with plotting hardware and the people that just need plots so they can farm.

You can find detailed instructions on how to get started with plotting on Akash [here](https://docs.akash.network/deploy/chia-on-akash). Currently, using the Akash service requires a farmer to obtain the AKT token, which is the native asset of the Akash Network. There is [Cloudmos](https://cloudmos.io/) which has a nice GUI and templates ready for plotting, but the Chia community has asked to make this process even easier.

## Evergreen

Evergreen, which makes low-power hardware that is ready to farm, has integrated the Akash plotting as a service onto their platform. This is a huge win for the Chia community, as now they can use either $USD or XCH to buy plots, and get a link in email to download. This is also a very easy way to get friends and family into Chia if they have a broadband internet connection.

The service will be going live soon at [https://www.evergreenminer.com/get-plotd](https://www.evergreenminer.com/get-plotd)

## Challenges

The only real prerequisite for downloading plots is fast and reliable internet service. While cable providers like Comcast may have fast download speeds, they sometimes issue bandwidth caps. This is not good for a large amount of data being transferred to download a plot. Ideally, the plotting as a service customer has > 1Gbps fiber internet connection with no bandwidth limitations or throttling. Plots can be downloaded at night while the internet is not being used. True 1Gbps would be a plot download in 15 minutes. In practice, among common fiber 1Gbps connections (like AT&T) we see downloads in the 20-40 minute range. The future increases in bandwidth will tremendously help this use case, as 1Gbps seems to be the sweet spot for a small farmer looking for some extra plots.

## Plotting at scale

Akash has demonstrated that the plotting as a service can scale with the demand. There are already a few providers that have hardware dedicated to Chia, like my own, BigTractorPlotting. We had a test run with a customer with a lot of underutilized space for storage they owned in their business, and downloading plots and farming was the best solution for them. Over a one-month period, we were able to scale to over 2500 plots per day by plotting across multiple providers. In the future, when demand for Chia goes up, Netspace will grow and people will be looking for cost-effective options to fill up space for farming.

The ability to download plots will help enable businesses that want to offer pre-plotted drives. It will be a key tool for future one-click farming solutions where a farmer has underutilized space in a NAS and wants to fill it up with plots. It is a perfect solution for businesses with underutilized storage space, who already have access to reliable and fast ISPs.

## Summary: Are buying plots cheaper than making them?

We discussed the math of how to calculate the actual cost of a plot, which has quite a few personal variables. One may already own the hardware, have access to cheap or free renewable energy, or have identified a second use for the plotting hardware. This is a tough question to answer. If someone already owns a desktop computer, they have to invest in a decent SSD to start plotting if they want to plot a few hundred terabytes effectively. At the exact cost of this SSD they could download the plots, likely in a shorter amount of time if they have access to 1Gbps internet. I view plotting as a service as an excellent tool in the plotting toolkit to further Chia farming adoption. There will be plenty of scenarios where it offers a lower cost and a win for both the provider and the farmer. This will only get easier as broadband internet speeds increase over time.