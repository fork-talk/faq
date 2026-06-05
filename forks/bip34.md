---
layout: page
title: "BIP-34"
---

[← Back to FAQ](../index.md)

# BIP-34 - Block Height in Coinbase

| | |
|---|---|
| **Year** | 2012 |
| **Type** | Soft fork (MASF) |
| **BIP** | [BIP-34](https://github.com/bitcoin/bips/blob/master/bip-0034.mediawiki) |
| **Status** | Active |

## What it does

Requires miners to include the block height as the first item in the coinbase transaction's scriptSig. This ensures every coinbase transaction has a unique transaction ID.

## Why it mattered

- Prevented duplicate coinbase transaction IDs (which had occurred in blocks 91,842 and 91,880)
- Made each block's coinbase provably unique
- Introduced the version-bits signaling mechanism later refined in BIP-9

## How it activated

Miner-activated soft fork. Required 750 of the last 1000 blocks to signal support (75%). Activated on March 24, 2012.

## Outcome

Smooth activation, no chain split. Became the model for subsequent miner-signaled soft forks.

## Links

- [BIP-34 full text](https://github.com/bitcoin/bips/blob/master/bip-0034.mediawiki)
