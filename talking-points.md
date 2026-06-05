---
layout: page
title: "Talking Points"
---

[← Back to FAQ](index.md)

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
