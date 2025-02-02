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

### 2. Create a New Keypair:
You'll need a wallet to create and manage the token. Generate a new keypair or use an existing one:

bash
solana-keygen new --outfile ~/my-keypair.json

If you already have a wallet, you can check your public key with:
solana address

### 3. Airdrop SOL for Transaction Fees
If you're using devnet, request some SOL to cover fees:
bash
solana airdrop 2


Verify your balance:
bash
solana balance

