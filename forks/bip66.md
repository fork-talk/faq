---
layout: page
title: "BIP-66"
---

[← Back to FAQ](../index.md)

# BIP-66 - Strict DER Signatures

| | |
|---|---|
| **Year** | 2015 |
| **Type** | Soft fork (MASF) |
| **BIP** | [BIP-66](https://github.com/bitcoin/bips/blob/master/bip-0066.mediawiki) |
| **Status** | Active |

## What it does

Requires all signatures in Bitcoin transactions to use strict DER (Distinguished Encoding Rules) encoding. Previously, OpenSSL accepted multiple encoding formats for the same signature, creating inconsistencies between nodes.

## Why it mattered

- Eliminated a source of consensus divergence between nodes running different OpenSSL versions
- Made signature validation deterministic across all implementations
- Removed Bitcoin's dependency on OpenSSL's quirks
- Prerequisite for later security improvements

## How it activated

Miner-activated soft fork. Required 950 of the last 1000 blocks (95%). Activated in July 2015.

Notable: a brief accidental fork occurred when some miners signaled support without actually enforcing the rules, producing invalid blocks. The network recovered quickly.

## Outcome

Successfully activated. The brief fork during activation became a lesson in the importance of miners actually running the code they signal for.

## Links

- [BIP-66 full text](https://github.com/bitcoin/bips/blob/master/bip-0066.mediawiki)
