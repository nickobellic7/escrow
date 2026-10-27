# Escrow

A USDC escrow app for Arc Testnet. A buyer locks USDC for a seller. The seller is paid automatically once a dispute window passes with no dispute. If the buyer disputes, the owner decides who is paid, and the buyer can take the money back if the owner doesn't decide in time. An optional small fee and an emergency pause are controlled by the owner.

Built with [Arc Studio](https://studio.arc.io)

Status: the contract design is written (see `contracts/Escrow-design.md`). The contract and the app are still being built.

## What it does

- Buyers create a deal for a seller and an amount of USDC.
- Sellers are paid automatically after the dispute window (3 days by default) unless the buyer disputes.
- Disputed deals are resolved by the owner, or refunded to the buyer after 14 days if unresolved.
- The owner can set a fee (up to 5%, off by default) and pause the contract in an emergency.

## Tech stack

- Solidity 0.8.28, Foundry, OpenZeppelin
- React, TypeScript, Vite, Tailwind CSS
- wagmi, viem, ConnectKit
- Target network: Arc Testnet (USDC)

## Development

Prerequisites: [Bun](https://bun.sh) and [Foundry](https://book.getfoundry.sh).

Install:

```bash
bun install
```

Environment variables (all optional for local development):

- `RPC_PROXY_BASE_URL`, `RPC_PROXY_TOKEN`, `RPC_PROXY_CHAINS`: RPC proxy settings provisioned by Arc Studio. Optional outside Arc Studio.
- `DEPLOYER_PRIVATE_KEY`: private key used only by the self-deploy script. Never commit it.

Run:

```bash
bun run dev
```

Build and test:

```bash
bun run contracts:build   # compile the contracts
bun run contracts:test    # run the contract tests
bun run check             # lint and typecheck
```
