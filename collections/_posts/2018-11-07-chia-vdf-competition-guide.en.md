---
lang: en
layout: post
title:  "Chia VDF Competition Guide"
date:   2018-11-07
author: "[Lipa Long](https://github.com/lipalong) and [Bram Cohen](https://twitter.com/bramcohen)"
---

Chia Network recently launched a three month long competition to create faster implementations of our proofs of time and get a better handle on its security requirements. The Verifiable Delay Function Competition (VDF, aka proof of time) is open to anyone, has $100,000 in total prize money, and is running until January 3rd, 2019.

In the interests of making it as easy as possible to join the competition, this post gives an overview of the different tracks, as well as step-by-step instructions one how to submit an entry. The full details of the competition are available on our [Github page](https://github.com/Chia-Network/vdf-competition).

### Purpose and Explanation

The Chia consensus algorithm uses proof of space as its key resource. In order to create a secure consensus algorithm, however, proof of space is not enough. Attackers can grind on many possible solutions, or create a longer alternate blockchain, especially if they have a lot of computational power. To protect against these attacks, [Verifiable Delay Functions](https://eprint.iacr.org/2018/601.pdf) are used to enforce real time between blocks. VDFs are deterministic functions which are non-parallelizable, and for which it’s possible to efficiently calculate short, easy to verify proofs. As long as an attacker can’t compute the VDF much faster than honest parties, the above attacks will not be practical.

The VDF that Chia is using is repeated squarings (likely verified with a Wesolowski proof, but that isn’t part of this competition). This must be done in a group, for which we’re using ideal class groups, which are explained in the [class group document](https://github.com/Chia-Network/vdf-competition/blob/master/classgroups.pdf). Class groups are mathematical [groups](https://en.wikipedia.org/wiki/Group_%28mathematics%29) defined by their discriminant D, and they have a group operation (composition), and an element representation that consists of three integers (A, B, C). The repeated squarings VDF takes an generator g = (A, B, C), and performs the composition operation on itself for the required number of iterations.

So if the VDF requires 1,000,000 iterations, the algorithm would square/compose the input 1,000,000 times.

g = (A, B, C)

g² = (A, B, C) compose (A, B,C)

(g²)² = (A’, B’, C’) compose (A’, B’, C’)

…

…

… (1,000,000 iterations)

…

…

y = (Af, Bf, Cf)

Since the order of the group is not known, the squaring operation is believed to require all the squarings, as explained [here](https://github.com/Chia-Network/vdf-competition/blob/master/classgroups.pdf). A verifiable delay function also needs to provide a short proof, so that verifiers can quickly check that it was performed correctly without running the intensive computation themselves. However, for the purposes of this competition, we only care about the output of the VDF, not the proof.

### Track 1: Fastest VDF Implementation

Track 1 requires the competitor to efficiently evaluate N VDF iterations, given the discriminant D. The generator element g should be computed as:

g = (2, 1, (1-D)/8).

Then, g should be squared repeatedly, N times, and the output, y, in reduced form, should be printed to stdout. The competitor that can output the correct element the fastest wins.

The discriminants used for Track 1 will be of size 2048 bits, so the numbers used in the composition algorithm will be large, and thus reduction is necessary. The discriminants are generated using the create_discriminant algorithm, which hashes to a random prime with certain properties, and then takes the negation. The discriminant can be assumed the negation of a prime p, where p % 8 == 7.

See [sample entry 1](https://github.com/Chia-Network/vdf-competition/tree/master/sample-entry-1) for an example of what an entry for Track 1 should look like. On the benchmark machine squaring a number the required 2097152 times (that’s 2²¹) in a group with a 2048 bit discriminant takes about 169 seconds. Presumably the winning entries will improve on that substantially.

The discriminants used for judging will be released at the end of the competition. The commitment to these discriminants is “2fe1e53289900911495b570a6ef9bed17b90a7eb02922631563fca641b83b8ef”

The discriminants can be generated, and the commitment verified, using [the verification script](https://github.com/Chia-Network/vdf-competition/blob/master/tools/create_competition_discriminants.py). The number of iterations N will be 2²¹ = 2097152. The first place winner will receive $40,000, and the second place winner $20,000.

### Track 2: Best Discriminant Break

The second track is about breaking the largest possible class groups. If one can find the order of an element in the class group, it might make the class group insecure. The order of the element is the smallest integer m such that e^m = identity. Track 2 requires competitors to find the order of any element in the class group other than the identity.

This should be easy to do for very small groups (small discriminant), but more and more difficult the larger the discriminant gets. 2048 bits (for Track 1) is likely an overly conservative choice allowing for more optimizations and higher cost of making custom hardware than necessary. The purpose of this track is to get a sense of the how large of class groups can be broken.

The competition requires the submission of 3 different seeds for create_discriminant(), and for each of those an element (A, B, C) and order (an integer specifying the order of that class group element). The smallest absolute value of the three discriminants is the final score. The exact specification is judge_entry.py.

See [sample entry 2](https://github.com/Chia-Network/vdf-competition/tree/master/sample-entry-2) for an example of what an entry for Track 2 should look like. The first place winner will receive $27,000, and the second place winner $13,000. New sample entries can be made using baby_giant_step.py, but there are much better known algorithms.

### Steps for Participating

1. Both submissions and communications with the Chia team are done via Keybase (https://keybase.io/). After you install the Keybase application, we have two channels available in **chia_network.public**: #VDF_contest (for discussions related to the competition) and #general (for general discussions about Chia). To join, type in your terminal: keybase team request-access chia_network.public
2. Complete the [Entry Form](https://www.dropbox.com/s/odsglm1eu9z6g8v/CHIA%20NETWORK%20APPLICATION%20FORM%204812-8893-1439%20v.1.pdf?dl=0) together with the signed version of [VDF Competition Rules and Disclosures Agreement](https://www.dropbox.com/s/3hmxe7717x5a0pp/Chia%20Network%20-%20VDF%20Contest%20Rules%20and%20Disclosures%20%286%29.pdf?dl=0). In the case of team participation, each team member must complete both forms and all members must choose the same point of contact. The forms should be sent to Ali Shadle, either via Keybase (@ashadle) or via email ([ali@chia.net](mailto:ali@chia.net)).
3. After we check the registration forms, a private channel will be created for you or your team (chia_network.TEAM_NAME) with engineers from our Chia development team as participants. You can ask us questions regarding the competition there.
4. Each team can create shared Keybase Git repositories where code can be submitted. Here (https://keybase.io/blog/encrypted-git-for-everyone) are some instructions about using Keybase Git repositories.
5. Check out the vdf-competition [Github repo](https://github.com/Chia-Network/vdf-competition) to see explanations and sample code for class groups, as well as a sample submission for each track.
6. To participate in **Track 1: Fastest VDF Implementation** track, upload your files to a shared git repository under chia_network.TEAM_NAME. A sample entry can be found [here](https://github.com/Chia-Network/vdf-competition/tree/master/sample-entry-1). The folder must contain two files: **install.sh** and **run.sh**, which must both be executable, and start with “#!/bin/sh”. We’ll first run **install.sh** on our ubuntu test machine (specs below), which should resolve any dependencies, and compile the code. Then we’ll run **run.sh**, passing it two parameters: the discriminant in hex and the number of iterations, in decimal. The score of the entry will be the time used by run.sh to output the correct answer on our reference hardware. An incorrect answer will not be scored at all. The entry folder must also include a README file which describes the approach used.
7. In order to participate in **Track 2: Best Discriminant Break** track, upload your files to a shared git repository under chia_network.TEAM_NAME. The folder must contain a file called **entry.txt**, which should contain three lines, one line for each discriminant provided. Each line must contain six numbers, separated by a space: seed (in hex), length, a, b, c, and order. For scoring, the script **judge_entry.py** from the tools folder is used. The entry folder must also contain a file README which explains the approach used.
8. Only the last entry will be judged. At the end of the competition (after January 3rd), we’ll judge all entries from all the shared Keybase Github repositories and we’ll announce the winners.
9. For **Track 1: Fastest VDF Implementation**, we have deployed a system to run your entry on the reference machine and give feedback on how well it performed. You can use the VDF chat bot to run KeyBase git repo submissions on our reference hardware. You can test your results by sending the bolded message below to vdf_bot in your KeyBase private channel. vdf_bot will then report back to you the timing results or any errors that occur: `/vdf judge_speed keybase://team/chia_network.TEAM_NAME/entry`
10. For **Track 2: Best Discriminant Break**, you can use the VDF chat bot to test your KeyBase git repo entry.txt format by sending the bolded message below to vdf_bot in your KeyBase private channel. vdf_bot will then report back to you whether it was evaluated successfully or any errors that occur: `/vdf judge_discriminant keybase://team/chia_network.TEAM_NAME/track2`.

### Benchmark machine specs

Dell Inspiron 3670 64bit

i5 -8400 @ 2.8GHz

8GB ram

GPU: Geforce GTX 1060 3GB

For any questions, join us on Keybase: keybase team request-access chia_network.public, and join the #VDF_contest channel. We hope you participate!
