---
layout: page
title: "P2SH (BIP-16)"
---

[← Back to FAQ](../index.md)

# P2SH - Pay to Script Hash (BIP-16)

| | |
|---|---|
| **Year** | 2012 |
| **Type** | Soft fork (MASF) |
| **BIP** | [BIP-16](https://github.com/bitcoin/bips/blob/master/bip-0016.mediawiki) |
| **Status** | Active |

## What it does

P2SH allows the sender to pay to a hash of a script rather than to a specific public key. The spending conditions (multisig, time locks, etc.) are revealed only when the funds are spent, not when they are received.

Before P2SH, complex spending conditions had to be specified by the sender. This made multisig transactions cumbersome and required senders to understand the recipient's script.

## Why it mattered

- Enabled practical multisig wallets
- Moved script complexity from sender to recipient
- Made Bitcoin addresses uniform regardless of spending conditions
- Foundation for later innovations like SegWit (which uses P2SH-wrapped addresses)

## How it activated

Miner-activated soft fork. Required 550 of the last 1000 blocks to signal support (55% threshold). Activated on April 1, 2012.

## Outcome

Smooth activation, no chain split. P2SH became the standard for multisig and is still widely used today.

## Links

- [BIP-16 full text](https://github.com/bitcoin/bips/blob/master/bip-0016.mediawiki)
- [Bitcoin Wiki: P2SH](https://en.bitcoin.it/wiki/Pay_to_script_hash)
