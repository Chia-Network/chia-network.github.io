---
lang: en
layout: post
title:  "Chia VDF Competition Round 1 Results and Announcements"
date:   2019-01-17
author: "[Bill Blanke](https://github.com/wjblanke)"
---

Thank you to everyone who participated in the first round of Chia Network’s Verifiable Delay Function (VDF) competition. The round concluded on January 3rd, 2019 with many excellent submissions from the participants. The quality of the entries exceeded our expectations, and we’re happy that the competition format proved successful. The teams used a variety of approaches, contributed to interesting discussions on our Keybase channels, and massively improved upon our reference implementation. The entries are helping us learn a lot about how to create a better VDF.

We’re excited to announce the results of Track 1 for this first round of competition (**Track 2 will be announced after we review additional documentation submitted by the entrants**):

Track 1

1. bulaiden: 40.65 seconds
2. sundersoft: 46.13 seconds
3. akashnil: 53.25 seconds
4. pulledpork: 84.56 seconds
5. anonymous1: 88.58 seconds
6. pulmark: 112.89 seconds
7. psa: 128.80 seconds
8. anonymous2: 140.83 seconds

Reference implementation: 169 seconds

Passphrase for contest discriminants: chia until sweet pleasant full sleep

Two Track 1 teams were disqualified: cryptoslava (six discriminants did not finish, but the four discriminants which did work ran in an average of 34.69 seconds), and poanetwork (working entry was submitted after the deadline, with average run time of 132.16 seconds).

Because of all the hard work the teams put into the competition, in addition to the first and second place Track 1 prizes ($40,000 to first place and $20,000 to second place), we’ve decided to also award $2000 prize money to each of the other Track 1 teams who entered the contest.

All of the code from participating teams is open source and can be found at [https://github.com/Chia-Network/vdftrack1results](https://github.com/Chia-Network/vdftrack1results).

One of the most significant optimizations incorporated by several teams was the use of the NUDUPL algorithm, a squaring version of the more general composition algorithm NUCOMP, which was first introduced by Shanks in 1989 \[1\]. NUDUPL incorporates partial reduction during squaring, decreasing the complexity of the intermediary operands. Since Shank’s introduction of the algorithm, others have improved upon NUDUPL and demonstrated its efficiency over classical composition algorithms (see, for instance, \[2\], \[3\], \[4\]).

Other optimizations from the competition included using the Lehmer algorithm for gcd computation, MPIR as a faster fork of GMP, and SIMD instructions for fast integer operations. LibFlint, which depends upon MPIR, includes the NUDUPL and Lehmer algorithms and was used by some teams. Many other small optimizations were implemented as well. And while the majority of the submissions were in C or C++, one team submitted an entry in Rust.

We’ll iterate on the competition by incorporating the solutions from this first round into our next round of competition, the details and rules of which will be announced soon. Our second round will include another contest to find the fastest VDF implementation (Track 1), but for now we’re holding off on a second round of discriminant breaking (Track 2). The prize money that had been set aside for a second Track 2 round will be redistributed toward other portions of the competition.

Thanks again to all the teams who participated, and congratulations to the winners of round 1! We look forward to working with everyone in round 2.

\[1\] D. Shanks (1989). On Gauss and composition I and II. Proc. NATO ASI on Number Theory and Applications, pp. 163–204, R. Mollin (ed). Kluwer Academic Publishers, Dordrecht.

\[2\] M. J. Jacobson Jr., and A. J. van der Poorten (2002). Computational aspects of NUCOMP. Algorithmic Number Theory — ANTS-V, volume 2369 of Lecture Notes in Computer Science, pp. 120–133, C. Fieker and D.R. Kohel (eds). Springer-Verlag, Berlin.

\[3\] M. J. Jacobson Jr., R. Scheidler, H. C. Williams (2006). An improved real-quadratic-ﬁeld-based key exchange procedure. Journal of Cryptology, 19, pp. 211–239.

\[4\] A. J. van der Poorten (2003). A note on NUCOMP. Mathematics of Computation, 72, pp. 1935–1946.
