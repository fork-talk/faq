---
layout: page
title: "SegWit (BIP-141)"
---

[← Back to FAQ](../index.md)

# SegWit - Segregated Witness (BIP-141/143/147)

| | |
|---|---|
| **Year** | 2017 |
| **Type** | Soft fork (UASF pressure + MASF activation) |
| **BIPs** | [BIP-141](https://github.com/bitcoin/bips/blob/master/bip-0141.mediawiki), [BIP-143](https://github.com/bitcoin/bips/blob/master/bip-0143.mediawiki), [BIP-147](https://github.com/bitcoin/bips/blob/master/bip-0147.mediawiki) |
| **Status** | Active |

## What it does

Separates ("segregates") signature data ("witness") from transaction data. The witness is moved to a new structure outside the traditional block size limit.

- **BIP-141**: Core SegWit structure and new witness program
- **BIP-143**: New transaction digest algorithm for signature verification
- **BIP-147**: Fixes dummy stack element malleability in CHECKMULTISIG

## Why it mattered

- **Fixed transaction malleability** - enabled reliable transaction chaining (critical for Lightning)
- **Increased effective block capacity** - from ~1 MB to ~2-4 MB via the weight system
- **Enabled Lightning Network** - malleability fix was the final prerequisite
- **Script versioning** - created a clean upgrade path for future soft forks (used by Taproot)
- **Reduced fees** - witness data is discounted (1 weight unit vs 4 for non-witness)

## How it activated

The most contentious activation in Bitcoin's history:

1. **BIP-9 signaling** stalled - miners blocked activation for political reasons (tied to the block size debate)
2. **BIP-148 (UASF)** - community-driven flag day (August 1, 2017) threatening to reject non-signaling blocks
3. **BIP-91** - miners capitulated and signaled through BIP-91, activating SegWit via BIP-9 before the UASF flag day
4. **SegWit locked in** July 2017, **activated** August 24, 2017

The UASF demonstrated that economic nodes, not just miners, determine Bitcoin's rules.

## Outcome

Network converged. No chain split on Bitcoin itself (Bitcoin Cash forked separately the same month over the block size debate, not SegWit specifically). SegWit adoption has grown steadily and now accounts for the majority of transactions.

## Links

- [BIP-141 full text](https://github.com/bitcoin/bips/blob/master/bip-0141.mediawiki)
- [BIP-143 full text](https://github.com/bitcoin/bips/blob/master/bip-0143.mediawiki)
- [BIP-147 full text](https://github.com/bitcoin/bips/blob/master/bip-0147.mediawiki)
