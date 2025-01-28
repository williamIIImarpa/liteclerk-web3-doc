# Creating a Token on Solana

To create a token on Solana, you need to use the **Solana CLI** and **Solana Token Program**. Here’s how you can do it step-by-step.

## Prerequisites:
- **Solana CLI** installed: [Installation Guide](https://docs.solana.com/cli/install-solana-cli-tools)
- A **Solana Wallet** (use `solana-keygen` to create one)

## Steps to Create a Token:
### 1. Set up Solana CLI
Make sure your Solana CLI is configured to work on the `devnet` (or `mainnet` when ready):
```bash
solana config set --url devnet
