---
lang: en
layout: post
title:  "30 hours to 30 minutes, Chia’s release automation story"
date:   2021-10-05
author: "[Justin England](hhttps://github.com/justinengland)"
---

On March 17th, 2021, the roughly 15 chia engineers responsible for launching mainnet had just finished the “go, no go” checklist for launching Chia version 1.0.0. For the past several weeks the entire Chia team had been on high alert, working long hours, ironing out the final details that would allow the blockchain to finally launch from testnet to mainnet. It was an exciting and hectic time for the team, and this moment was the culmination of years of hard work and dedication. After weeks of practice, with every detail documented, at 6:00 am mountain time on the 17th they began the work in earnest. 

Step one of the release was a new git tag on the chia-blockchain repo to create Chia version 1.0.0. The checklist after step one, was some one hundred items long, and almost every one of those one hundred steps was handled by a senior engineering team member, by hand, while on zoom to coordinate with about a dozen other moving parts. Pages long google documents were referenced. This process from start to finish took about 3 hours real time, with almost a month of practice on testnet. At any given time the team had up to 10 people coordinating feature rollouts and upgrades. Thirty hours of cumulative engineering work later and et voila, one Chia mainnet.

Once the glow of the day had finally worn off. The team came to terms with the fact that they would have to do this __ALL__ over again for 1.0.1 and for __EVERY__ release after. Needless to say, this was not ideal. 

The couture approach was an effective one when releasing pre-mainnet with the expectation of an ad hoc approach to the release. Chia as an enterprise was still identifying what the operational pillars were; among many other shifting patterns. So of course the process had defaulted to the experts of each domain ensuring that the portions they owned were released effectively. This approach was not scalable, and required a lot of commitment and focus by the team to land things reliably, release after release. As time marched into the future these senior engineers found themselves only tackling these tasks during the release cycle and referencing notes each time. It was a recipe for low repeatability and scalability, and a process that made it easy to make a mistake. The launch process often felt cumbersome in the following iterations as what had initially been a cause for massive celebration settled into dissatisfaction. This process no longer fit the company Chia had become.

Enter the Devops team. Let us first acknowledge that, having a separate team handling operations, ci and all things cd, is not what you would traditionally call a true devops org. However this is a pattern that has worked well for Chia as it grows from a small tight knit team to a larger enterprise. It was this separation of responsibilities that allowed the team to continue doing the more cumbersome releases while working diligently to improve the process around releases, with better automation and stronger, more repeatable patterns. The goals were “simple”, replacing fragility with stability. Replacing manual work with automation. Making every critical task of delivering Chia software repeatable, secure, and stable. 

Flash forward to the release of Chia version 1.2.5 on August 27th, 2021, the release pipeline took just 30 minutes from start to finish and all the work was accomplished by one engineer, whose only task was creating a git tag on the chia-blockchain repository. It was the first, bug free, 100% automated Chia release. The culmination of nearly 6 months of efforts from our devops team, including Chris Marslender, Niraj Pathak, and Patrick Maslana. Needless to say, we at Chia view this as a massive accomplishment, especially considering how relatively little time it took to build, and how cumbersome the release workflow was when the Devops team began improving it in earnest.

So how did releases go from 30 hours of labor to 30 minutes? What lessons can you, dear reader, take away from the success of this endeavor? 

At the outset of this “automate releases” task, the devops team knew it was important to define goals and core principles. This allowed the team to rank task priority and give themselves a set of guidelines to fall back on when faced with open ended problems. The team decided to organize around these core principles;

- Small batches of iterative deployments
- Fail fast 
- Full CI/CD automation using github actions
- All new patterns would be secure, repeatable, and human free


It is my humble opinion that these core tenants are the single biggest improvements any software team can make that will increase velocity, and lend adopting teams a clear sense of purpose and priority. It is often better to have a working bad solution than a perfect half written one. Movement and action are superior to over-thinking, the faster you can get an idea working and failing; the sooner you can make it better; and the quicker you will hit the mark on solving the actual problems at play. Nothing against good planning and thoughtful development, but on the Chia Devops team we err toward doing. If you keep putting one foot in front of the other so to speak, you will be surprised how far that can take you. 

The Devops team finds failure to be instructive. Many startups claim the famous mantra of “move fast break things”, which is a fun thing to say. In practice, it can often feel very hectic for the end users of the products that are being broken. The Chia devops team takes a more measured approach in failing fast. When things do fail, they are put under a microscope and analyzed. The team even holds post mortems about their biggest failures, to invite the community into the fold for this process. The end goal is that something should only need to fail once for that problem to be fixed and never rear its head again. 

Once the Devops team had north stars to align their work to, they had to then find the best patterns for moving the needle with their efforts. Where was their effort needed the most?  

The devops team needed to be strategic force multipliers. Focused on adding automation and process improvements, where those improvements would have the most benefit in labor savings for the larger Chia ecosystem. Many of these tasks were not easily automated and required some creativity to get right. Coupled with the fact that some tasks were only truly testable end to end during an actual release created unique engineering challenges and frankly some unsophisticated solutions. Its only stupid if it doesn’t work. Creative solutions, and a fanatical approach to fixing the places where those systems fall flat, allowed the Devops team to move very quickly improving every piece of the release ecosystem.

It might seem too simple, but this is the big secret of the automation transformation. Clear guide posts for what the team wanted to do, clear goals on how that work would be accomplished in the broad sense. Clear direction on what tasks to prioritize and which to push off. Along with a strict adherence to the agreed upon practice of small batches and failing fast. When you find yourself clear of the gory details, (that will likely change again before release) and focus on solving the problems in front of you, it's incredible how much improvement even small changes can garner. If you work to apply any of the information from this blog post to your workflows, let it be this. 

All that being said, it is important to acknowledge exactly what was improved during this 6 month stretch of work. The following is a brief summary of the larger items the Devops team was able to accomplish. 

- Improved github security, using vault for credentials. Replacing the less secure default pattern github provides for secrets. 
- Improved repeatability by creating the release manager process. 
- Improved reliability by waiting until all the installers had finished and checked in with the release manager to do the actual release work.
- Tied all the accessory portions of the ecosystem like docker containers and testnet instances into downstream events on every release. 
- Added sha256 checksums
- Automated updating of the installer release page.
- Testnet now releases every 12 hours from head of main.
- Automated releasing new chia software versions to our deployed nodes, introducers, and timelords.
- Created an A/B system for mission critical instances so a bad release cannot break the network with an automated release.
- The official Chia docker image was improved.
- Testnet and mainnet telemetry was added. 
- The devops team is still working on composite actions, better and easier to understand preflight tests, and automating announcements of a release. 

Since the 27th of August the team has had several more releases, all of which ran within the 30 minute time frame. Chia is now able to release without the former release experts even recognizing a release has been cut. Several times an engineer who used to do a critical portion by hand has been on vacation during a release and been thrilled upon their return. 

This sort of real human impact of removing the stress of a release day for the engineers who were laser focused on delivering every single time, has been one of the best things to come out of the last year and is the reason we do all this fancy automation and high concept devops work. There is no better endorsement of the Devops team's work, than, “You have made my job far simpler”. Cheers to that. 
