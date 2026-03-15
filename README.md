# Tride Contracts

Tride is an intercity carpooling platform that uses Soroban smart contracts on Stellar to enforce escrow, refund, and payout rules without platform custody. This repository is the contract workspace for that settlement layer.

The contracts repo is responsible for the logic that must be deterministic and verifiable on-chain.

## What Tride Is About

Tride is built around one core product idea: riders and drivers should know in advance how money moves when a trip is booked, canceled, boarded, completed, or abandoned.

That means the contract layer must eventually support rules for:

- seat-based booking escrow,
- cancellation windows,
- no-show handling,
- driver payout,
- platform fee collection,
- timeout-based completion finalization.

## What This Repo Covers

This repo contains the Soroban workspace setup for Tride smart contracts. It is intended to hold:

- escrow contract crates,
- shared contract utilities,
- contract test suites,
- deployment and build conventions.

At the moment, this is a prepared workspace and does not yet include a concrete contract implementation.

## Prerequisites

Install the required toolchain before adding or building contracts:

```bash
rustup update stable
rustup target add wasm32v1-none
brew install stellar-cli
```

## Workspace Layout

- `Cargo.toml`: shared workspace configuration and release profiles
- `contracts/`: place individual contract crates here
- `.cargo/config.toml`: shared cargo defaults for local development
- `rust-toolchain.toml`: stable Rust toolchain pin with the Soroban target

## Getting Started

After installing Rust and Stellar CLI, you can create the first contract crate with:

```bash
stellar contract init contracts/escrow
```

or create a crate manually under `contracts/` and add `soroban-sdk` through the workspace dependency.

## Contribution Guide

Useful contribution areas include:

- escrow state machine design,
- payout and refund logic,
- contract event modeling,
- Soroban unit and integration tests,
- security review of settlement paths,
- deployment and upgrade safety.

When contributing:

1. Favor explicit state transitions over clever abstractions.
2. Document every money-moving rule in code and tests.
3. Treat edge cases such as timeout, cancellation, and no-show behavior as first-class.
4. Keep the contract surface minimal and auditable.

## Important Note

This repo should evolve from the product rules, not the other way around. Contract complexity should only be introduced when it directly supports the Tride booking and settlement model.
