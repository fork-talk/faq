---
layout: page
title: "CLTV (BIP-65)"
---

[← Back to FAQ](../index.md)

# CLTV - CheckLockTimeVerify (BIP-65)

| | |
|---|---|
| **Year** | 2015 |
| **Type** | Soft fork (MASF) |
| **BIP** | [BIP-65](https://github.com/bitcoin/bips/blob/master/bip-0065.mediawiki) |
| **Status** | Active |

## What it does

Adds the OP_CHECKLOCKTIMEVERIFY opcode, which allows a transaction output to be made unspendable until a specific block height or time. This enables absolute time locks at the script level.

## Why it mattered

- Enabled trustless payment channels (predecessor to Lightning)
- Made escrow and time-locked contracts possible without third parties
- Critical building block for layer-2 protocols

## How it activated

Miner-activated soft fork using BIP-34-style version bits. Required 750 of the last 1000 blocks. Activated in December 2015.

## Outcome

Smooth activation, no chain split. CLTV is now fundamental to Lightning Network and other time-locked constructs.

## Links

- [BIP-65 full text](https://github.com/bitcoin/bips/blob/master/bip-0065.mediawiki)
