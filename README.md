# Tride Contracts

Soroban workspace scaffold for Tride smart contracts.

## Prerequisites

Install the required toolchain before adding or building contracts:

```bash
rustup update stable
rustup target add wasm32v1-none
brew install stellar-cli
```

## Workspace Layout

- `Cargo.toml`: shared workspace and release profiles
- `contracts/`: place individual contract crates here
- `.cargo/config.toml`: shared cargo defaults for local development
- `rust-toolchain.toml`: stable Rust toolchain pin with the Soroban target

## Next Steps

To add the first contract later, either run:

```bash
stellar contract init contracts/escrow
```

or create a crate manually under `contracts/` and add the Soroban SDK dependency.
