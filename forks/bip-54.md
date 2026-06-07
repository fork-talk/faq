---
layout: page
title: "BIP-54"
---

[← Back to FAQ](../index.md)

# BIP-54 - Great Consensus Cleanup

| | |
|---|---|
| **Year** | 2025-2026 (proposed) |
| **Type** | Soft fork |
| **BIP** | [BIP-54](https://github.com/bitcoin/bips/blob/master/bip-0054.md) |
| **Authors** | Antoine Poinsot, Matt Corallo |
| **Status** | Draft |
| **Origin** | Matt Corallo's 2019 "Great Consensus Cleanup" proposal |

## What it does

BIP-54 bundles four fixes for long-standing protocol vulnerabilities:

### Timewarp attack fix

Constrains block timestamps at difficulty adjustment boundaries. Without this fix, an attacking miner with sufficient hashrate could manipulate timestamps to artificially lower mining difficulty, potentially draining subsidy distribution or forcing heavy block data onto full nodes.

### 64-byte transaction ban

Invalidates transactions with exactly 64 bytes of non-witness serialized data. These transactions cannot be cryptographically secure, have never been standard, and pose a Merkle tree malleation risk that could trick SPV (lightweight) clients into accepting false transaction inclusion proofs.

### Worst-case validation constraints

Limits non-coinbase transactions to a maximum of 2,500 signature operations. This reduces worst-case block validation time by approximately 40x, mitigating vulnerabilities with the `FindAndDelete` function and `OP_CODESEPARATOR`. Without this, a malicious miner could craft a block that takes an extremely long time to validate, causing other nodes to fall behind.

### Coinbase uniqueness

Requires the coinbase `nLockTime` field to equal the block height minus one, and `nSequence` cannot be `0xffffffff`. This ensures every coinbase transaction is unique, preventing duplicate transaction issues without relying on the BIP-30 validation check.

## Why it matters

These are genuine bug fixes for known vulnerabilities. The timewarp attack and slow-validation attacks are real risks that depend on miner honesty to not exploit. The Merkle tree weakness affects SPV security. The duplicate coinbase issue is a legacy protocol quirk.

On their own merits, these fixes are relatively uncontroversial.

## Concerns

### Scope creep and bundling

The original proposal started narrowly scoped. There are signs that additional changes are being bundled in, such as `getblocktemplate` (GBT) modifications for the RPC interface. Bundling policy-level changes with consensus fixes expands the scope beyond what was originally agreed as uncontroversial.

When GBT additions were proposed for BIP-54 ([PR #2097](https://github.com/bitcoin/bips/pull/2097)), reviewers pushed back. One reviewer noted that pools already have the block height information needed for forward compatibility, making the additions redundant. Others argued these belong in a separate specification.

The risk is familiar: start with something uncontroversial, then attach additional items to ride through on the original goodwill. This is the same pattern that concerned the community with Core v30.

### Fast-tracking

There are concerns that BIP-54 is being fast-tracked without adequate community review, following a similar pattern to the OP_RETURN limit removal in Core v30. The fixes themselves may be good, but rushing consensus changes through without sufficient scrutiny has not served Bitcoin well in recent history.

None of the vulnerabilities BIP-54 addresses are new. They have existed for years. There is no urgent crisis requiring a rush. Thorough review and deliberate activation serve Bitcoin better than speed.

### Trust assumptions

The vulnerabilities BIP-54 fixes currently rely on miner honesty to not exploit. This is a legitimate concern - "verify, don't trust" is a core Bitcoin principle. But the urgency framing can be overstated. These vulnerabilities have existed since Bitcoin's early days without being exploited. Fixing them is good engineering practice, but it is not emergency surgery.

### Activation mechanism

BIP-54 does not yet specify an activation mechanism. How it activates matters as much as what it contains. The activation debate (miner signaling thresholds, flag days, UASF vs MASF) will determine whether it proceeds with broad support or becomes contentious.

### Authors' track record

BIP-54 is authored by Antoine Poinsot and builds on Matt Corallo's 2019 "Great Consensus Cleanup" proposal. Both are Bitcoin Core contributors. In the current environment where Core's governance and decision-making are under scrutiny (particularly after the OP_RETURN limit removal was merged despite 4:1 community opposition), proposals from Core contributors face heightened skepticism. That scrutiny is earned, not unfair.

## What to watch

- **Does the scope stay narrow?** If BIP-54 remains limited to the four original fixes, it is likely to be uncontroversial. If additional items are bundled in, that changes.
- **How is it activated?** The activation mechanism will determine community support.
- **Is there adequate review time?** Consensus changes deserve thorough, unhurried review.
- **Is community feedback incorporated?** Or is it merged over objections, as with the OP_RETURN change?

## The bottom line

The fixes in BIP-54 address real vulnerabilities and are good engineering on their merits. The concern is not what it contains today, but the process: whether it gets fast-tracked, whether scope expands, and whether community input is respected. Bitcoin's governance challenges are not about specific technical proposals - they are about how changes are made.

## Links

- [BIP-54 full text](https://github.com/bitcoin/bips/blob/master/bip-0054.md)
- [PR #2097 - GBT additions discussion](https://github.com/bitcoin/bips/pull/2097)
- [bitcoindev mailing list](https://groups.google.com/g/bitcoindev) - search "BIP 54" or "consensus cleanup"
- [Bitcoin Optech: Great Consensus Cleanup](https://bitcoinops.org/en/topics/consensus-cleanup-soft-fork/)
