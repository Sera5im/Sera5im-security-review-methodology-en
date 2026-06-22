# Security Review Methodology

This repository contains my personal methodology for reviewing bridge and cross-chain smart contract systems at the contract / application layer.

## Focus

My current review focus is:

- bridges
- L2 and L3 contract-layer systems
- cross-chain token paths
- flow analysis
- function-level reasoning
- invariant drafting and verification
- trust assumptions and system guarantees

## Scope

The main scope is the contract / application layer around user-facing bridge logic.

This methodology is not intended as a deep dive into lower-level messaging internals, proving systems, compression, or cryptographic components unless they directly affect the reviewed contract-layer path.

## Repository Structure

| File | Description |
| --- | --- |
| [METHODOLOGY.md](./METHODOLOGY.md) | Full methodology: review focus, scope boundary, workflow, review layers, and AI usage |

## What This Methodology Covers

- how I choose a concrete token path
- how I split a bridge system into deposit and withdrawal flows
- how I separate flow review, function-level review, out-of-flow review, and global guarantees
- how I draft candidate invariants and verify them against code
- how I use AI as a support tool while keeping final judgment manual

## Main Document

Read the full methodology here:

- [METHODOLOGY.md](./METHODOLOGY.md)
