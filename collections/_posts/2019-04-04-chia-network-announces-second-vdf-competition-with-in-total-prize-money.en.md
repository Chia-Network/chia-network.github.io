---
lang: en
layout: post
title:  "Chia Network Announces 2nd VDF Competition with $100,000 in Total Prize Money"
date:   2019-04-04
author: "[Matt Howard](https://github.com/matt-o-how) and [Bram Cohen](https://twitter.com/bramcohen)"
---

A few months ago we wrapped up our initial VDF implementation competition and were amazed by the excellent quality of the submissions. The top three contenders each came in at under one minute (the reference implementation was 169 seconds). Five other teams also submitted implementations which were faster than the reference. All of the submissions were open-source, and can be found [here](https://www.chia.net/2019/01/17/chia-vdf-competition-round-1-results-and-announcements.en.html). The award total was originally $100,000, but because of the hard work that all of the teams put into the competition, we decided to award $2,000 to each team who submitted an entry, bringing the total prize money awarded to $116,000.

We are proud to announce a second competition, challenging entrants to improve on our new reference implementation.

The second VDF competition will be split into two tracks:

1. SIMD and GPU optimizations allowed
2. SIMD and GPU optimizations not allowed

This is to help us separate the different kinds of optimizations. We expect that the entries which use the optimizations allowed in track 1 will be faster, however there is no requirement for a track 1 submission to use those techniques. This means that all track 2 submissions are also eligible for submission to track 1.

The winners of each track will receive $50,000.

Individuals and teams are invited to join. Entrants will all have access to the specialized computers in Chia’s laboratory.

Specifications of the reference hardware and further technical details are available on our [GitHub](https://github.com/Chia-Network/vdf-competition). You can view our pre-commitment [here](https://github.com/Chia-Network/vdf-competition/blob/master/tools/create_competition_discriminants.py).

Contestants will be able to communicate with Chia during the competition via a secure [Keybase](https://keybase.io/team/chia_network.public) channel.

### Steps For Participating
<br>
1. Both submissions and communications with the Chia team are done via [Keybase](https://keybase.io/team/chia_network.public). After you install the Keybase application, we have two channels available in chia_network.public: #VDF_contest (for discussions related to the competition) and #general (for general discussions about Chia). To join, type in your terminal: keybase team request-access chia_network.public

2. Complete the [Entry Form](https://github.com/Chia-Network/vdf-competition/blob/master/Application%20Form.pdf) together with the signed version of [VDF Competition Rules and Disclosures Agreement](https://github.com/Chia-Network/vdf-competition/blob/master/Rules%20and%20Disclosures.pdf). In the case of team participation, each team member must complete both forms and all members must choose the same point of contact. The forms should be sent to Ali Shadle, either via Keybase (@ashadle) or via email (ali@chia.net).

3. After we check the registration forms, a private channel will be created for you or your team (chia_network.TEAM_NAME) with engineers from our Chia development team as participants. You can ask us questions regarding the competition there.

4. Each team can create shared Keybase Git repositories where code can be submitted. Here (https://keybase.io/blog/encrypted-git-for-everyone) are some instructions about using Keybase Git repositories.

5. Check out the vdf-competition [Github repo](https://github.com/Chia-Network/vdf-competition) to see explanations and sample code for class groups, as well as a sample submission for each track.

6. To participate in either track, upload your files to a shared git repository under chia_network.TEAM_NAME.The folder must contain two files: install.sh and run.sh, which must both be executable, and start with “#!/bin/sh”. We’ll first run install.sh on our Ubuntu test machine, which should resolve any dependencies, and compile the code. Then we’ll run run.sh, passing it two parameters: the discriminant in hex and the number of iterations in decimal. The score of the entry will be the time taken by run.sh to output the correct answer on our reference hardware. An incorrect answer will not be scored at all.

7. Your entry folder must also include a README file which describes the approach used and specifies which track the submission is for.

8. Only the last entry from your team will be judged. At the end of the competition, we’ll judge all entries from all the shared Keybase Github repositories and we’ll announce the winners.

9. We have deployed a system to run your entry on the reference machine and give feedback on how well it performed. You can use the VDF chat bot to run KeyBase git repo submissions on our reference hardware. You can test your results by sending the bolded message below to vdf_bot in your KeyBase private channel. vdf_bot will then report back to you the timing results or any errors that occur: /vdf judge_speed keybase://team/chia_network.TEAM_NAME/entry


To learn more or enter the competition, please visit [here](https://www.chia.net/) or join our [Keybase](https://keybase.io/team/chia_network.public) channel.

We hope you participate!
