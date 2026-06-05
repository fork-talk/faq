---
layout: home
---

<p align="center">
  <img src="logo.png" alt="Fork Talk" width="200">
</p>

# Bitcoin Forks FAQ

A beginner-friendly guide to understanding Bitcoin forks — what they are, what types exist, which ones have happened, and what's being discussed today.

---

## Basics

### What is a fork?

A fork is a change to Bitcoin's rules. Since Bitcoin is decentralized software running on thousands of nodes, any rule change requires coordination. When part of the network adopts new rules, the chain "forks" — there are now two sets of rules, and participants must choose which to follow.

The term covers everything from routine upgrades (where everyone agrees) to contentious splits (where they don't).

### What is a BIP?

A BIP (Bitcoin Improvement Proposal) is the standard process for proposing changes to Bitcoin. Inspired by Python's PEP system, BIPs provide a structured way to document, discuss, and review technical proposals before they are implemented.

Anyone can write a BIP. Having a BIP number does not mean the proposal is endorsed or will be adopted — it means the proposal has been formally documented for public review.

BIPs are catalogued at [github.com/bitcoin/bips](https://github.com/bitcoin/bips).

### What types of forks exist?

There are three main types:

**Soft fork** — Tightens the rules. Blocks valid under the new rules are also valid under the old rules. Nodes that don't upgrade still accept the chain, they just don't enforce the new restrictions. Soft forks are backward-compatible.

*Example*: SegWit (2017) added new transaction rules. Old nodes still accepted SegWit blocks — they just couldn't validate the new witness data.

**Hard fork** — Loosens or changes the rules. Blocks valid under the new rules may be invalid under the old rules. Nodes that don't upgrade will reject the new chain. Hard forks require all participants to upgrade or they split the network.

*Example*: Bitcoin Cash (2017) increased the block size limit. Nodes running the original rules rejected the larger blocks, creating a permanent chain split.

**Temporary soft fork** — A soft fork with a built-in expiry date. The tighter rules activate for a defined period, then automatically deactivate. If not renewed, the chain returns to its previous rules.

*Example*: BIP-110 (proposed) would activate data-reduction rules for approximately one year before auto-expiring.

### What is a UASF?

A User-Activated Soft Fork (UASF) is a soft fork activated by node operators and users rather than by miners. Instead of waiting for a miner signaling threshold, UASF sets a flag day — after a specific date, nodes running the new software enforce the new rules regardless of miner signaling.

The most notable UASF was BIP-148 in 2017, which pressured miners to signal for SegWit activation. The threat of a chain split where non-signaling miners would be forked off was sufficient to achieve miner compliance, and SegWit activated via BIP-91 shortly before the BIP-148 flag day.

UASFs demonstrate that Bitcoin's rules are ultimately enforced by the economic majority (nodes, exchanges, users), not just miners.

### What is a MASF?

A Miner-Activated Soft Fork (MASF) is the traditional activation method. Miners signal readiness for new rules in the blocks they produce. When a threshold of blocks signal support (historically 95%, more recently 90%), the new rules activate.

*Example*: BIP-34 (2012) required blocks to include their height in the coinbase transaction, activated when 750 of the last 1000 blocks signaled support.

### What is activation threshold?

The activation threshold is the percentage of blocks that must signal support before a fork's rules take effect. Different proposals use different thresholds:

- **95%** — Traditional BIP-9 threshold (used for SegWit initially)
- **90%** — BIP-8 LOT=true threshold (used for Taproot)
- **55%** — Proposed for BIP-110 (lower threshold, but temporary rules with auto-expiry)

The threshold reflects a tradeoff between broad consensus and the ability to activate. Higher thresholds are more conservative but can be blocked by a small minority. Lower thresholds activate more easily but risk more contention.

---

## Historical Forks

### What major soft forks have happened?

| Year | Fork | What it did |
|------|------|------------|
| 2012 | BIP-16 (P2SH) | Enabled pay-to-script-hash, allowing complex spending conditions |
| 2012 | BIP-34 | Required block height in coinbase transactions |
| 2015 | BIP-65 (CLTV) | Added absolute time locks for transactions |
| 2015 | BIP-66 | Enforced strict DER signature encoding |
| 2016 | BIP-68/112/113 (CSV) | Added relative time locks |
| 2017 | BIP-141/143/147 (SegWit) | Separated witness data, fixed malleability, increased effective block capacity |
| 2021 | BIP-340/341/342 (Taproot) | Added Schnorr signatures and MAST for better privacy and smart contracts |

Every previous soft fork tightened rules and maintained backward compatibility. The network converged in each case.

### What major hard forks / chain splits have happened?

| Year | Fork | What happened |
|------|------|--------------|
| 2017 | Bitcoin Cash (BCH) | Increased block size to 8 MB. Permanent chain split. |
| 2017 | Bitcoin Gold (BTG) | Changed proof-of-work algorithm to Equihash. Permanent split. |
| 2018 | Bitcoin SV (BSV) | Split from Bitcoin Cash, further increased block size to 128 MB. |

Hard forks that lack overwhelming consensus create permanent chain splits. Both chains continue, but market and community support typically concentrates on one.

### Has a soft fork ever caused a chain split?

No. Every soft fork in Bitcoin's history has resulted in network convergence. Because soft forks tighten rules (making them backward-compatible), non-upgraded nodes still follow the longest chain. Game theory and economic incentives (described in the Bitcoin white paper, section 6) have driven convergence every time.

---

## Current Proposals

### What is BIP-110?

BIP-110 is a proposed temporary soft fork that would reduce non-financial data in Bitcoin blocks. It introduces relay and consensus rules that filter transactions primarily used for data embedding (such as Ordinals inscriptions) rather than financial transfers.

Key features:
- **Temporary**: Auto-expires after approximately one year
- **Activation threshold**: 55% miner signaling
- **Grandfather clause**: All pre-activation UTXOs are exempt — no existing funds are affected
- **Goal**: Reduce non-financial block space usage, which currently accounts for approximately 41% of block space (source: Renaud Cuny, Bitcoin Block Space Weekly)

BIP-110 text: [github.com/bitcoin/bips/blob/master/bip-0110.mediawiki](https://github.com/bitcoin/bips/blob/master/bip-0110.mediawiki)

### What is eCash?

eCash (proposed at [ecash.com](https://ecash.com)) is a separate fork proposal. It approaches Bitcoin's scaling and feature set differently from BIP-110.

*(This section will be expanded as more details become available.)*

### Are there other active proposals?

The Bitcoin development community regularly discusses potential changes. Some areas of active discussion include:

- **OP_CTV** (BIP-119): Covenants enabling vaults and congestion control
- **OP_CAT** (BIP-347): Re-enabling concatenation for advanced scripting
- **Great Consensus Cleanup**: Fixing legacy protocol issues

The fork-talk community primarily tracks proposals related to block space policy and data filtering, but awareness of the broader landscape helps contextualize any individual proposal.

---

## Key Concepts

### What is Nakamoto consensus?

Nakamoto consensus is Bitcoin's mechanism for reaching agreement without a central authority. Described in the Bitcoin white paper (section 6), it relies on proof-of-work and the longest-chain rule: the chain with the most accumulated work is the valid chain.

This creates strong economic incentives for convergence. Miners who build on a minority chain waste energy and earn coins on a less valuable fork. The rational strategy is to follow the majority, which is why every soft fork in Bitcoin's history has resulted in convergence rather than a permanent split.

### What is the white paper?

The Bitcoin white paper, "Bitcoin: A Peer-to-Peer Electronic Cash System" by Satoshi Nakamoto (2008), is the founding document of Bitcoin. It describes the system's design, including proof-of-work, the longest-chain rule, and the economic incentives that keep the network secure.

Available at [bitcoin.org/bitcoin.pdf](https://bitcoin.org/bitcoin.pdf).

### What is Bitcoin Core?

Bitcoin Core is the most widely used Bitcoin node software. It is maintained by a group of open-source contributors and is the reference implementation of the Bitcoin protocol. While influential, Bitcoin Core does not "control" Bitcoin — any node operator can run alternative implementations.

Recent discussion around Core centers on the v30 release, which removed the 80-byte OP_RETURN limit (increasing it to ~100KB), a change that was opposed approximately 4:1 in public GitHub discussion (423 against, 105 for).

### What does "peer-to-peer electronic cash" mean?

This phrase, from the title of the Bitcoin white paper, defines Bitcoin's purpose: a system for sending value directly between people without intermediaries. It is the design goal against which protocol changes can be evaluated — does a given change serve or hinder Bitcoin's function as electronic cash?

---

## Getting Involved

### How can I contribute to fork-talk?

- **Join the discussion**: Open issues, comment on proposals, share data
- **Run a node**: The most direct way to participate in Bitcoin governance is to run a node that enforces the rules you support
- **Contribute data**: Empirical analysis (block space metrics, fee data, simulation results) is more valuable than opinion
- **Submit PRs**: Improve this FAQ, correct errors, add sources

### Where can I learn more?

- [Bitcoin white paper](https://bitcoin.org/bitcoin.pdf)
- [BIP repository](https://github.com/bitcoin/bips)
- [Bitcoin Block Space Weekly](https://blockspaceweekly.substack.com/) (Renaud Cuny) — empirical block space analysis
- [fork-talk GitHub org](https://github.com/fork-talk)

---

*This FAQ is a community effort. It does not represent any individual or organization. Corrections and contributions welcome via pull request.*
