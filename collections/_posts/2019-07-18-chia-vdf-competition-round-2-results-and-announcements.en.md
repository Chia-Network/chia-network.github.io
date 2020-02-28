---
lang: en
layout: post
title:  "Chia VDF Competition Round 2 Results and Announcements"
date:   2019-07-18
author: "[Bill Blanke](https://github.com/wjblanke)"
---

Congratulations to Sundersoft for winning both tracks of the second Chia VDF competition and earning $100,000!  

We had four entries that all made large improvements in the speed of the VDF algorithm in both contest tracks compared to our in house reference implementation. Note that these timings are for 4x the iterations and on slightly slower hardware (no turboboost) than the first VDF contest.

Two of the entries had problems with certain discriminants. Since the final judging discriminants are unknown (aside from a hash) to the contest entrants, we recommend testing your entry against as many random discriminants as possible.  

The passphrase for the final judging discriminant generation (as given by the precommitment at contest start) is below:  

python3 create_competition_discriminants.py “armor drive digital shaft dash wide resemble guilt bubble push sniff grass asset vital version reward grid popular ketchup diary pen hurdle doctor lumber”  

Sundersoft's entry took advantage of a number of optimizations and you can read about his improvements [here](https://github.com/Chia-Network/vdfcontest2results/blob/master/sundersoft/entry/README.md). One of his ideas was to parallelize parts of the algorithm in order to take advantage of two cores, and that helped to push him to a 2x speedup over the reference implementation.  

Techniques from ALL contestants will likely be incorporated to further improve the VDF algorithm. Thus, additionally, Chia has decided to award $2000 each to the three teams that submitted an optimized entry but did not place first. Thank you for your hard work!

The source code for all entries for both tracks is included in this [repository](https://github.com/Chia-Network/vdfcontest2results).  

Please consider entering our [current competition](https://www.chia.net/2019/07/07/chia-network-announces-pos-competition.en.html) for improving the [Proof of Space](https://github.com/Chia-Network/proofofspace) algorithm. Proof of Space is heavily dependent on sorting and disk I/O and there should be many possibilities for improvement over the reference implementation. There is also a Hellman attack (time/memory tradeoff) example for those who would like to see how much space they can save by maxing out the computational power of the reference hardware.  

## Track 1 Results (SIMD/GPU) avg sec  

Sundersoft: 91.3    
nemo1369/Nil Foudation: 133 crash #4 hang #5    
PulledPork: 145.7 (late entry)    
pulmark: 161 hang #4    
Chia reference: 178    

## Track 2 Results (No SIMD/GPU) avg sec  

Sundersoft: 97.4    
nemo1369/Nil Foundation: 142 crash #4 hang #5    
PulledPork: 153 (late entry)    
pulmark: 164 hang #4    
Chia reference: 182.6    
