---
lang: en
layout: post
title:  "Aggregated signatures, Taproot, Graftroot, and standard transactions"
date:   2021-05-27
author: "[Bram Cohen](https://twitter.com/bramcohen)"
---

In Chia we're using BLS signatures which enable noninteractive signature aggregation. In this post I'll explain how that fits into the system as a whole, what practical benefits it provides, and how our 'standard' transaction format works, and what taproot and graftroot really are.

Explaining the motivation and background on taproot and graftroot is outside the scope of this post, so if you don’t already know how taproot and graftroot work in Bitcoin, you can read this [explanation for motivation and background on taproot](https://lists.linuxfoundation.org/pipermail/bitcoin-dev/2018-January/015614.html), this one for [more technical details](https://github.com/bitcoin/bips/blob/master/bip-0341.mediawiki), and this [explanation of graftroot](https://lists.linuxfoundation.org/pipermail/bitcoin-dev/2018-February/015700.html).

Our ‘standard’ format transaction, which this post explains, is [implemented here](https://github.com/Chia-Network/chia-blockchain/blob/main/chia/wallet/puzzles/p2_delegated_puzzle_or_hidden_puzzle.clvm). That code snippet is written in [chialisp](https://chialisp.com).

First a high level view of what's going on (some background on [how transactions work in Bitcoin](https://en.bitcoin.it/wiki/Transaction)). In Bitcoin the persistent state is called the [UTXO](https://river.com/learn/terms/u/unspent-transaction-output-utxo/) set, which in Chia is called the coin set. Other naming conventions in Bitcoin are a bit esoteric, so in Chia we chose more descriptive names.  A Bitcoin "scriptpubkey" is called a "puzzle" in Chia.   A Bitcoin "scriptsig" is called a "solution" in Chia.  Both concepts are more powerful in Chia.  A puzzle must be passed a solution, and the puzzle then returns "conditions" which are the Chia equivalent of the information contained in a transaction, but they're generated dynamically and aren't hashed into the identities of future coins. Because of signature aggregation solutions somewhat counterintuitively don’t contain signatures. Typically a solution contains the list of conditions to be asserted, and the puzzle adds to that list an assertion of them being signed which must be included in the aggregate signature. Aggregate signatures are dangling pieces of information which are included with transactions passed in the mempool and transaction blocks. When a transaction block is created all the aggregate signatures of transactions within it are re-aggregated into a single aggregate signature thanks to the magic of BLS signatures being non-interactively aggregatable.

![Bitcoin with Segwit compared to Chia](/assets/blog/Bitcoin-with-segwit.png "Bitcoin with Segwit compared to Chia")

One of the big differences from Bitcoin is that each coin has its own separate solution, which raises the question of how several different spends and coin creations are forced to come as a bundle. The direct way is for them to declare that the other coins must be spent as part of their transactions in their conditions. A more elegant and basic trick is to only release the aggregate of all their signatures. BLS has the property that the signatures of any number of (key, value) pairs can be expressed as a single aggregated signature. It isn't possible given the aggregated signature to pull out any of the individual signatures. It's completely normal to make a transaction where one of the inputs, possibly even the smallest one, makes all the outputs and the others simply burn themselves doing nothing. As long as the sum of the sizes of the outputs is equal to the sum of the sizes of the inputs this works fine. As long as only the aggregate signature was published there's no way for anyone else to pull off just the coin solutions which burn the large ones and pocket that money for themselves. If someone wants to safely spend a single input in a different way then any deviation from what they originally signed will provide safety. It’s also possible for coin spends to explicitly communicate with and depend on each other, but not required. With BLS it is possible to non interactively aggregate any number of aggregates, which is used to make every Chia transaction block contain exactly one aggregated signature, regardless of the number of transactions from the mempool which went into it.

While features like taproot and graftroot are in no way directly built into Chia, the necessary hooks to implement them are in there and we're using a 'standard' transaction format which we recommend most vanilla transactions stick with. It turns out that much of the cryptographic magic in taproot and graftroot has to do with trying to compress them using what amounts to ad hoc signature aggregation. When aggregation is already built into the system, and always used, the underlying logic of these features becomes much more direct.

The simplest bit of smart functionality to describe is [MAST](https://bitcoinops.org/en/topics/mast/). The underlying language of the chia on-chain programming environment is CLVM, (Chia Lisp Virtual Machine or more generically Common Language Virtual Machine), but here’s what MAST looks like paraphrased in more pythonic pseudocode:

    def my_mast_puzzle(solution):
	    metapuzzle, metasolution = solution
	    assert hash(metapuzzle) in [‘hashA’, ‘hashB’]
	    return metapuzzle(metasolution)

In addition to being very simple and clean, this recursive approach to merkleization has the privacy benefit of giving no hint as to the depth of the tree or what’s at the leaves along the way. You can make it deeper by using a similar program which taxes a metameta puzzle and a metametasolution, followed by a metametametapuzzle, etc.

You might notice the egregious use of eval of simply calling a piece of data passed in as code. In this particular case the hash was checked beforehand so it would be safe even in an unsafe language, but this sort of eval is common in clvm programs even for untrusted code and is allowed by the CLVM’s strict adherence to there being no side effects and no global data, resulting in every call being strictly sandboxed.

Both taproot and graftroot are motivated by the desire to short circuit the logic of a smart transaction. Most of the time everyone participating in a group transaction cooperates, or at least acknowledges that they'll be forced to cooperate, so you can use an N-of-N key for the visible one on your coin and all N parties to your transaction sign off on it in the clean case, with a trapdoor for the unclean case.

Graftroot at its core is simple delegation. The simplest approach to signed transactions would be to treat the solution passed in as a list of conditions, prepend a requirement that that list must be signed by your key in the aggregated signature, and return that.

    def my_simple_puzzle(solution):
	    return [(‘aggregate signature’, ‘my_public_key’, hash(solution)] + solution

Graftroot makes this just slightly more complicated by its solution containing two things, a metapuzzle and a metasolution. It calls the metapuzzle passing it the metasolution, getting a list of conditions in response. It then prepends an assertion that the metapuzzle signed by the coin's key is in the aggregate, and returns that.

    def my_graftroot_puzzle(solution):
	    metapuzzle, metasolution = solution
	    Return [(‘aggregate signature’, ‘my_public_key’, hash(metapuzzle)] +
                  metapuzzle(metasolution)

If several participants want to participate in a smart transaction, they can all collectively sign the metapuzzles to be used in the unclean solutions, then go about their business and if everything is clean in the end sign a metapuzzle which just returns the conditions they all arrived at and ignores the metasolution.

Taproot is subtly different from graftroot. Its big advantage is that the trapdoor conditions can be committed to up front, without needing to coordinate with the other participants in a smart transaction to get their signatures in advance. It requires some extra hooks be built into the language to support it but we've added those and made support for taproot trapdoors part of our standard puzzle format.

![Taproot Pubkey Generation](/assets/blog/Taproot-Pub-Key-Generation.png "Taproot Pubkey Generation")

![Taproot Clean Path Generation](/assets/blog/Taproot-Clean-Path-Generation.png "Taproot Clean Path Generation")

In the normal path taproot appears to use a normal public key in the normal way. In the trapdoor case it reveals another puzzle which was hidden inside the public key, then provides a solution to that puzzle. The way a puzzle is hidden inside a public key is that an original public key is made from a private key which will never be revealed, then that public key and the puzzle are hashed together to generate a new private key. The corresponding public key to that private key is calculated and the aggregate of that with the original public key are what's used for the puzzle's open public key. In the normal case the signer (or signers) signs using the original key then aggregates that signature with one from the other derived key to make what looks like an ordinary signature. In the trap door case the signer reveals what their original public key and the trapdoor puzzle are and provides a solution to that puzzle. It wouldn’t be sufficient to have the public key be just derived from the trapdoor puzzle with no prior key because that wouldn’t allow the key to be an aggregate and if the trapdoor case was used that would allow someone else to front run the transaction using the revealed non-trapdoor private key.

It is of course possible to nest these: The hidden puzzles can also be standard format which then also support taproot and graftroot. A similar trick is useful for merkleizing whole sets of possible puzzles. The root puzzle states that it must be given a puzzle reveal whose hash is one of two values and a metasolution. It then verifies the hash of the puzzle reveal, passes it the metasolution, and returns that. These can be nested resulting in logarithmic depth to any number of possible alternative leaves with a minimum of information revealed when a coin is spent.
