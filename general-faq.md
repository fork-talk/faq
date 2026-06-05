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

# Common Talking Points

Claims that come up repeatedly in Bitcoin fork discussions, with data-driven responses.

---

### "There is no way of stopping spam"

The framing is wrong. The concern is not just spam - it is malware, illegal content, and unaudited data sitting permanently on every full node in the world. That is the real problem, and dismissing it as "spam" minimises what node operators are being forced to store.

No security measure stops 100% of threats. We lock doors knowing locks can be picked. We set speed limits knowing they can be broken. We run firewalls knowing they can be bypassed. The standard for any defence is whether it reduces the problem to manageable levels - not whether it achieves perfection.

By that standard, the filters work. Chris Guida's data shows 99% reduction when filters are active. Renaud Cuny's BIP-110 simulation over 4.7 million transactions shows 99.95% accuracy with zero false positives on legitimate smart contracts. A measure that catches 99% of the problem has not "failed."

There is also a legal dimension. Knowingly removing safeguards against arbitrary data storage in a financial system creates liability exposure for node operators. Legal scholars including Nick Szabo have warned about the implications of data carrier content on a permanent ledger. Deliberately expanding capacity for such content (as Core v30 did with a 1,250x OP_RETURN increase) while removing existing protections could be viewed as negligence.

---

### "This is censorship"

Bitcoin was designed as peer-to-peer electronic cash. Filtering non-financial data to preserve that function is not censorship - it is the system working as designed.

Censorship means preventing someone from transacting. BIP-110 does not prevent anyone from sending or receiving bitcoin. It restricts the use of block space for purposes other than financial transactions - the same principle behind dust limits, standardness rules, and every other relay policy Bitcoin has always had.

If filtering non-financial data is "censorship," then dust limits are censorship, ancestor limits are censorship, and the original 80-byte OP_RETURN limit that operated for a decade was censorship. No one made that argument until it became useful for defending data embedding.

The word "censorship" is being repurposed to make spam filtering sound like an attack on freedom. It is not. Financial transactions are unaffected.

---

### "Miners should decide"

Miners secure the network. They do not govern it.

Bitcoin's rules are enforced by nodes, not miners. Miners build blocks within the rules that nodes enforce. If miners produce blocks that violate node rules, those blocks are rejected. This was demonstrated decisively in 2017 when the UASF forced miner compliance on SegWit activation.

The claim that "miners should decide" often surfaces when miner incentives conflict with user interests. Miners earn revenue from inscription fees. That does not mean the network's block space policy should be set by whoever profits most from the current arrangement.

Bitcoin's white paper (section 6) describes miners as honest participants who follow the rules because it is more profitable than attacking the system. It does not describe miners as the system's governors.

---

### "Dynamic fees already solve this"

If dynamic fees solved spam, 41% of block space would not be non-financial data.

Dynamic fees do not distinguish between financial and non-financial transactions. Spammers pay market fees. The result is that legitimate users compete with data embedders for the same block space, and both pay higher fees.

The inscription fee premium is 0.08% of block reward (Ocean vs SpiderPool comparison). Spammers get massive block space for negligible cost. Dynamic fees are not solving the problem - they are pricing in the externality and passing the cost to legitimate users.

This argument also contains a fatal contradiction when made by people who supported Core v30. You cannot argue "limited capacity is the solution to spam" while supporting a 1,250x expansion of data-embedding capacity (80 bytes to 100 KB). These positions are mutually exclusive.

---

### "It doesn't actually stop spam / BIP-110 does nothing"

Three falsifiable claims, all contradicted by data:

1. **"Does nothing to stop spam"** - Chris Guida data: 99% reduction when filters are active. Renaud Cuny simulation: 1,957,896 transactions (41.5%) filtered over 10 days.
2. **"Does nothing to make it harder"** - If 99% of non-financial transactions are filtered from mempools, it is empirically harder to embed data. Transactions don't propagate to compliant nodes and don't get mined by compliant miners.
3. **"Cost increase is less than 1%"** - This confuses miner revenue loss with spammer deterrence. The cost to spammers is not the fee differential - it is their transactions being rejected from mempools entirely.

The published data includes Chris Guida's filter analysis, Renaud Cuny's 13-issue Bitcoin Block Space Weekly series with 3.5 years of chain analysis, and the BIP-110 simulation results. Claiming "zero response" or "does nothing" requires ignoring all of it.

---

### "The OP_RETURN limit removal didn't change anything"

It changed the limit from 80 bytes to approximately 100,000 bytes. That is a 1,250x increase.

Framing a 1,250x expansion as "not changing anything" is the clearest example of gaslighting in the current debate. The change was proposed, opposed 4:1 by the community (423 against, 105 for), and merged anyway.

In the months following Core v30's release, Bitcoin Knots (which retains spam filtering) surged from 2-4% to 21% of reachable nodes. The community responded to the change precisely because it was a change.

---

### "You can't define spam / Who decides what's spam?"

BIP-110 does not require anyone to define "spam" in the abstract. It defines specific, measurable technical criteria for non-financial transactions. The simulation results speak for themselves:

- 99.95% of filtered transactions were Ordinals inscriptions
- Zero legitimate smart contracts were blocked
- 4.7 million transactions tested against the rules

The "who decides" framing implies that any filtering is subjective and therefore dangerous. In practice, the distinction between a financial transaction and a JPEG embedded in witness data is not ambiguous. The filter rules are public, auditable, and testable against real data.

---

### "This sets a dangerous precedent"

The instinct to think about precedent comes from a good place. Vigilance about scope creep in protocol changes is healthy.

But the comparison between a temporary data filter and a permanent monetary policy change does not hold. Every fork happens in a completely different environment - different technology, reward epoch, developers, hardware, economic conditions. The slope is not fixed.

A temporary soft fork that auto-expires after one year and a permanent change to the 21 million cap operate under fundamentally different incentive structures. The Bitcoin community would never accept inflation - it is the one rule that unites every participant. Miners hold BTC; inflating supply devalues their own holdings. The economic incentives are opposite.

Ideally no fork would be needed at all. If Core reverted v30's changes, BIP-110 would be unnecessary. It exists as a backstop in case they don't.

---

### "OP_RETURN is the lesser evil"

This is a false dilemma. The framing presents two options: unlimited OP_RETURN or data polluting the UTXO set. There is a third option: effective filtering.

The 80-byte OP_RETURN limit operated for approximately a decade. During that period, UTXO pollution from data embedding was not a significant problem. The surge in non-financial data began with Ordinals (2023) and Runes (2024), exploiting witness space and OP_RETURN respectively.

If filters achieve 99% reduction, the premise collapses. The choice is not between "data in OP_RETURN" and "data in spendable outputs." The choice is between "data on-chain" and "99% less data on-chain."

---

### "Filters are easily bypassed"

Some bypass tools (e.g. Libre Relay) were created *after* the limits existed, then cited as evidence that limits don't work. That is circular reasoning.

"Easily bypassed" does not mean "ineffective." The empirical data shows 99% reduction when filters are active. The bypasses exist and the filters still work at 99%. That is the answer.

If "easily bypassed" were grounds for removing a protection, we would remove dust limits, ancestor caps, and signature-operation checks - all of which can be bypassed in various ways. We retain them because they reduce the problem to manageable levels.

---

*[Back to main FAQ](index.md)*
