---
lang: en
layout: post
title: "Divided We Fork"
date: 2022-03-04
author: "[Dan Perry](https://github.com/danieljperry)"
---

Chia version 1.3 (coming Soon™) will have [many new features](https://www.chia.net/2022/02/10/1.3-beta-release.en.html "New features in 1.3") and some significant upgrades. One change we’ve talked about a bit less is the upcoming soft fork to disallow negative division. This post will cover what you need to know about this change.

## Hard fork vs soft fork

Blockchains have two basic methods of changing their consensus: hard fork and soft fork. Fundamentally, a hard fork is a broadening of the rules, and a soft fork is a narrowing of them. The following table shows the differences:


| Fork type | Before the fork point, X is | After the fork point, X is | Forward compatible? | Farmer upgrade required? | Chain split possible? |
|:----------:|:----------------------------:|:---------------------------:|:-------------------:|:------------------------:|:---------------------:|
| Soft fork  | Allowed                      | Not allowed                 | Yes                 | No                       | Yes                   |
| Hard fork  | Not allowed                  | Allowed                     | No                  | Yes                      | Yes                   |


Chia Network Inc. has a policy of never creating a hard fork unless absolutely necessary. However, on rare occasions, we will narrow the scope of what is allowed on the blockchain by creating a soft fork.

## The issue

[Chialisp](https://chialisp.com/docs/ref/clvm/ "Chialisp/CLVM reference") has two division operators: _div_ (aka "/") and _divmod_. There is an issue with _div_, specifically when used with negative numbers, which can produce unexpected results. For example, -a/b is not always equal to -(a/b). On the other hand, _div_ with positive numbers (for example 3/2) works as expected, always returning the floored quotient.

## How is Chia fixing this?

Luckily, _divmod_ works as expected – it always returns the floored quotient, as well as the remainder. Because _divmod_ is a valid alternative to _div_, the decision was made (with consensus from the community) to disallow the _div_ operator for negative division, resulting in a soft fork. Positive division using _div_, as well as all division using _divmod_, will continue to work going forward.

Once Chia’s blockchain reaches a height of 2,300,000 (around July 22, 2022), all nodes running version 1.3 or greater will reject all spends which attempt to use the _div_ operator for negative division. This should give farmers plenty of time to upgrade to version 1.3. In the unlikely event that nodes containing the majority of the netspace have not been upgraded before this block is reached, the soft fork will have been rejected.

## How this affects you

### Smart coin owners
After polling the community and searching through previous blocks, we’ve concluded that nobody has ever spent a smart coin that uses negative division. It’s unlikely, though still possible, that someone has _created_ such a coin, but has yet to spend it. These coins – if they exist – will need to be spent before block 2,300,000. In order to accomplish this, the owners of these coins will either need to farm the block that includes their own coin spends, or rely on a farmer using a version earlier than 1.3 to farm the block. After block 2,300,000, these coins – if they exist and have yet to be spent – will no longer be valid.

To be clear, if you only use Chia’s wallet and haven’t created your own smart coins, you do not own any potentially invalid coins.

### Farmers
Chia’s farmers simply need to upgrade to version 1.3. What are the consequences of not upgrading? Let’s say you don’t upgrade before block 2,300,000. The next time you farm a block, if there is a coin spend in the mempool that uses negative division, your node will accept the invalid spend and add it to the block you are creating. Other farmers will reject your block, and you’ll lose your block reward. Please make sure to upgrade your farming nodes to version 1.3 or newer before July 22.

## Conclusion

All things considered, this is a minor change to Chia’s consensus. However, we wanted to ensure that coins that could yield unpredictable results were not allowed. After version 1.3 is released, we recommend that you upgrade all of your machines as soon as is convenient.
