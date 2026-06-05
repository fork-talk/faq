---
layout: page
title: "CSV (BIP-68/112/113)"
---

[← Back to FAQ](../index.md)

# CSV - CheckSequenceVerify (BIP-68/112/113)

| | |
|---|---|
| **Year** | 2016 |
| **Type** | Soft fork (MASF) |
| **BIPs** | [BIP-68](https://github.com/bitcoin/bips/blob/master/bip-0068.mediawiki), [BIP-112](https://github.com/bitcoin/bips/blob/master/bip-0112.mediawiki), [BIP-113](https://github.com/bitcoin/bips/blob/master/bip-0113.mediawiki) |
| **Status** | Active |

## What it does

Three related BIPs that enable relative time locks:

- **BIP-68**: Redefines the sequence number field to encode relative lock-time constraints
- **BIP-112**: Adds OP_CHECKSEQUENCEVERIFY opcode for script-level relative time locks
- **BIP-113**: Uses median-time-past for time-lock calculations (more robust than block timestamps)

## Why it mattered

- Enabled bidirectional payment channels (critical for Lightning Network)
- Allowed contracts that say "this output can't be spent until N blocks after it was confirmed"
- Complemented CLTV's absolute time locks with relative ones
- Direct prerequisite for Lightning Network deployment

## How it activated

Miner-activated soft fork using BIP-9 versionbits signaling. Required 95% of blocks in a retarget period. Activated in July 2016.

## Outcome

Smooth activation, no chain split. Together with CLTV, CSV completed the time-lock infrastructure needed for the Lightning Network.

## Links

- [BIP-68 full text](https://github.com/bitcoin/bips/blob/master/bip-0068.mediawiki)
- [BIP-112 full text](https://github.com/bitcoin/bips/blob/master/bip-0112.mediawiki)
- [BIP-113 full text](https://github.com/bitcoin/bips/blob/master/bip-0113.mediawiki)
