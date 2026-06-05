---
layout: page
title: "General FAQ"
---

[← Back to FAQ](index.md)

# General FAQ

Common questions about Bitcoin governance, terminology, and discussion norms.

---

## Why should the word "consensus" be avoided in Bitcoin discussions?

The word "consensus" is used in at least three incompatible ways in Bitcoin, which creates confusion and enables manipulation:

1. **Consensus rules** - The specific technical rules all full nodes enforce (e.g. 21 million cap, block size limit). These are concrete and objective.
2. **Near-unanimity** - Agreement with no significant objection from stakeholders. Historically required for hard forks.
3. **General agreement** - A weighted majority based on expertise and argument strength, common in open-source governance.

The problem is that using one word for three different concepts lets people slide between meanings. Someone can say "there is no consensus for this change" and it is unclear whether they mean the technical rules reject it, that important stakeholders object, or simply that not everyone agrees.

The Bitcoin Wiki [recommends](https://en.bitcoin.it/wiki/Consensus) replacing "consensus" with precise terms:
- Say **"consensus rules"** or **"hard rules"** for the technical meaning
- Say **"non-contentious"** when you mean near-unanimity
- Say **"general agreement"** when you mean weighted majority

Using "consensus" loosely is a common rhetorical tool for blocking changes without having to make a specific, falsifiable argument. If someone says "we don't have consensus," ask which kind they mean.

---

## Who decides Bitcoin's rules?

No single entity decides. Bitcoin's rules emerge from the interaction of:

- **Node operators** - Enforce the rules they choose to run
- **Miners** - Build blocks under the rules nodes enforce
- **Users and businesses** - Choose which chain to transact on
- **Developers** - Propose and implement changes, but cannot force adoption

This is Nakamoto consensus in practice. The chain with the most accumulated work, the most nodes, and the most economic activity is Bitcoin. No amount of developer authority or miner signaling can override the economic majority.

Bitcoin Core is the most widely used node software, but it is not Bitcoin. Node operators can run alternative implementations (Bitcoin Knots, btcd, Libbitcoin, etc.) that enforce different policies.

---

## What is the difference between relay policy and consensus rules?

**Consensus rules** are enforced by all nodes. A block that violates consensus rules is rejected by the network. Changing consensus rules requires a fork (soft or hard).

**Relay policy** is enforced by individual nodes when deciding which unconfirmed transactions to forward to peers. It does not affect block validity. A miner can include a transaction that violates relay policy in a block, and the block is still valid.

This distinction matters because:
- The 80-byte OP_RETURN limit was relay policy, not a consensus rule
- BIP-110 proposes both relay policy changes and consensus rule changes
- Critics often conflate the two to argue that relay policy is ineffective ("miners can just ignore it")

Relay policy is not useless just because miners can bypass it. It determines what 99%+ of nodes propagate, which directly affects what miners see in their mempools.

---

## Is Bitcoin outside the law?

No. Bitcoin is open-source software released under the MIT license. The MIT license is a legal instrument - a copyright license that grants specific permissions under copyright law. Every Bitcoin contributor, node operator, and user operates within legal jurisdictions.

Open source does not mean anarchy. It means the source code is freely available under terms defined by law. The license is enforceable in court. Contributors retain copyright. The entire system rests on the legal framework of intellectual property law.

Bitcoin transactions themselves may have legal implications depending on jurisdiction (tax obligations, money transmission, sanctions compliance, etc.). The protocol's decentralization does not place its participants outside legal systems.

---

## What does "peer-to-peer electronic cash" mean and why does it matter?

This phrase is the title of the Bitcoin white paper. It defines Bitcoin's purpose: a system for sending value directly between people without intermediaries.

It matters because it provides a design goal against which protocol changes can be evaluated. When 41% of block space is consumed by non-financial data (Renaud Cuny, Bitcoin Block Space Weekly), the question becomes: is the protocol serving its stated purpose?

This is not an appeal to authority or tradition. It is a practical engineering question. Systems that drift from their design goals tend to serve no one well.

---

## What is gaslighting in the context of Bitcoin governance?

Gaslighting in Bitcoin governance is when participants are told that what they can see with their own eyes is not real. Examples:

- Being told the OP_RETURN limit removal "didn't change anything" when it increased the limit 1,250x (80 bytes to 100 KB)
- Being told filters "don't work" when empirical data shows 99% effectiveness
- Being told a change had "broad support" when it was opposed 4:1 (423 vs 105)
- Being told "nothing can stop spam" when simulations show 99.95% accuracy with zero false positives on legitimate contracts

The antidote is data. When someone makes a claim, ask for the numbers. The empirical evidence on block space, filter effectiveness, and community sentiment is publicly available and independently verifiable.

---

*[Back to main FAQ](index.md)*
