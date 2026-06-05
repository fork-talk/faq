---
layout: page
title: "Taproot (BIP-340/341/342)"
---

[← Back to FAQ](../index.md)

# Taproot (BIP-340/341/342)

| | |
|---|---|
| **Year** | 2021 |
| **Type** | Soft fork (MASF via Speedy Trial) |
| **BIPs** | [BIP-340](https://github.com/bitcoin/bips/blob/master/bip-0340.mediawiki), [BIP-341](https://github.com/bitcoin/bips/blob/master/bip-0341.mediawiki), [BIP-342](https://github.com/bitcoin/bips/blob/master/bip-0342.mediawiki) |
| **Status** | Active |

## What it does

- **BIP-340 (Schnorr signatures)**: Replaces ECDSA with Schnorr for key-path spends. Enables signature aggregation and simpler multisig.
- **BIP-341 (Taproot)**: Combines pay-to-pubkey and pay-to-script into a single output type. Simple spends look identical to complex ones on-chain.
- **BIP-342 (Tapscript)**: Updated script rules for Taproot outputs, including new opcodes and limits.

## Why it mattered

- **Privacy** - Multisig, timelocks, and simple payments all look identical on-chain
- **Efficiency** - Schnorr signatures are smaller and allow batch validation
- **Flexibility** - MAST (Merkelized Alternative Script Trees) enables complex contracts where only the executed branch is revealed
- **Future-proofing** - Clean upgrade path for new opcodes via Tapscript versioning

## How it activated

Used "Speedy Trial" (BIP-8 variant): miners had a 3-month window to signal at a 90% threshold. If reached, rules would lock in and activate after a delay. If not, the community would consider alternative activation.

Miners reached 90% signaling in June 2021. Taproot activated at block 709,632 on November 14, 2021.

## Outcome

Smooth activation, no chain split. Adoption is growing as wallets add Taproot support. The activation debate (around LOT=true vs LOT=false and Speedy Trial) was more contentious than the fork itself.

## Links

- [BIP-340 full text](https://github.com/bitcoin/bips/blob/master/bip-0340.mediawiki)
- [BIP-341 full text](https://github.com/bitcoin/bips/blob/master/bip-0341.mediawiki)
- [BIP-342 full text](https://github.com/bitcoin/bips/blob/master/bip-0342.mediawiki)
