---
lang: en
layout: post
title:  "Chia Network Announces Proof of Space Competition with $100k in Total Prize Money"
date:   2019-07-07
author: "[Lipa Long](https://github.com/lipalong) and [Bram Cohen](https://twitter.com/bramcohen)"
---

We’re excited to announce Chia’s Proof of Space competition. In Chia’s Proof of Space, rewards are given to farmers that can prove that they are allocating a portion of their disk space to farming Chia. In order to be used as a consensus method, Proof of Space is tied to Proof of Time. An open source implementation in C++ is available, that can be used as a [starting point](https://github.com/Chia-Network/proofofspace).

“We’re making sure that the fundamental building blocks of our protocol are confidence inspiring and available to all,” said Bram Cohen, founder of Chia Network. “By having an open competition, we’re making sure that the absolute best implementation anyone has is available to all.”

Contestants participating in the three-month competition will create implementations of Chia's proof of space consensus algorithm. The proof of space competition will be split into 3 tracks for total awards of $100k in prize money. The 3 tracks are:

1. Implementation that creates the plot the fastest get a prize. The performance criteria is based on the amount of time to create plot file aka “wall clock time".  
2. Implementation that uses the least swap space gets a prize. The performance criteria is based on the maximum amount of swap space (disk space + memory) that is used during the plotting process aka “Swap space needed".  
3. Implementation with smallest size of plot at rest and can respond to challenges gets a prize. The performance criteria is the amount of memory + disk space being used once plot has been created in response to challenges as well as the amount of time it takes to do look-ups.  

In addition, each submission to each track must reach a minimum threshold of all 4 performance criteria (listed below) that is required for all other tracks. For example, if an entrant enters Track 1, fastest plot, he must also adhere to a minimum threshold of all other 3 performance criteria (smallest swap, smallest plot, time of look-ups).

The 4 performance criteria are:

1. Amount of time to create plot file “wall clock time"  
2. Maximum amount of swap space (disk space + memory) that is used during the plotting process. “Swap space needed"  
3. Amount of memory + disk space being used once plot has been created in response to challenges  
4. Amount of time it takes to do look-ups, as long as it beats 1 second per 1 lookup.   

We will be awarding a total of $100k in prize money. The prize money will be awarded as follows:  

1. The first prize winner of Track 1 (fastest plot) will receive $25k  
2. The first prize winner of Track 2 (smallest swap) will receive $25k  
3. The first prize winner of Track 3 (smallest plot) will receive $50k  

Individuals and teams are invited to join. Entrants will all have access to the specialized computers in Chia’s laboratory. Specifications of the reference hardware and further technical details are available on our [GitHub](https://github.com/Chia-Network/proofofspace). You can view our pre-commitment [here](https://github.com/Chia-Network/proofofspace/blob/master/contest_intro.md). Contestants will be able to communicate with Chia during the competition via a secure Keybase channel.

### Steps For Participating

1. Both submissions and communications with the Chia team are done via Keybase. After you install the Keybase application, we have two channels available in chia_network.public: #POS_contest (for discussions related to the competition) and #general (for general discussions about Chia). To join, type in your terminal: keybase team request-access chia_network.public  
2. Complete the [Entry Form](https://github.com/Chia-Network/proofofspace/blob/master/2019%20CHIA%20NETWORK%20CHALLENGE%20APPLICATION%20FORM.pdf) together with the signed version of [POS Competition Rules and Disclosures Agreement](https://github.com/Chia-Network/proofofspace/blob/master/Chia%20Network%20-%20POS%20Contest%20Rules%20and%20Disclosures.pdf). In the case of team participation, each team member must complete both forms and all members must choose the same point of contact. The forms should be sent to Ali Shadle, either via Keybase (@ashadle) or via email (ali@chia.net).  
3. After we check the registration forms, a private channel will be created for you or your team (chia_network.TEAM_NAME) with engineers from our Chia development team as participants. You can ask us questions regarding the competition there.  
4. Each team can create shared Keybase Git repositories where code can be submitted. Here (https://keybase.io/blog/encrypted-git-for-everyone) are some instructions about using Keybase Git repositories.  
5. Check out the pos-competition [Github repo](https://github.com/Chia-Network/proofofspace) to see explanations and sample code for proof of space, as well as a sample submission for each track.  
6. To participate in either track, upload your files to a shared git repository under chia_network.TEAM_NAME.The folder must contain three files: install.sh, plot.sh, and prove.sh, which must all be executable, and start with “#!/bin/sh”. We’ll first run install.sh on our Ubuntu test machine, which should resolve any dependencies, and compile the code. Then we’ll run plot.sh, passing in the ID of the plot in hex. Finally, we will run ./prove.sh <challenge>, for each challenge, and measure the time taken.  
7. Your entry folder must also include a README file which describes the approach used and specifies which track the submission is for.  
8. Only the last entry from your team will be judged. At the end of the competition, we’ll judge all entries from all the shared Keybase Github repositories and we’ll announce the winners.  
9. We have deployed a system to run your entry on the reference machine and give feedback on how well it performed. You can use the POS chat bot to run KeyBase git repo submissions on our reference hardware. You can test your results by sending the bolded message below to pos_bot in your KeyBase private channel. pos_bot will then report back to you the timing results or any errors that occur: /vdf judge_speed keybase://team/chia_network.TEAM_NAME/entry

To learn more or enter the competition, please visit [here](https://www.chia.net/) or join our [Keybase](https://keybase.io/team/chia_network.public) channel.

We hope you participate!
