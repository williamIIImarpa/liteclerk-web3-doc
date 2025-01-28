
---

### **5. `liquidity-setup.md` (Setting up Liquidity)**

```markdown
# Setting Up Liquidity on Solana

To list and trade your token, you need to set up liquidity. Here’s how you can do it on Solana.

## Prerequisites:
- A token created as shown in [Creating a Token](token-creation.md)
- A liquidity pool on a DEX like Serum or Radium

## Steps to Set Up Liquidity:
### 1. Create a Serum Liquidity Pool
To add liquidity, you'll need to create a pool. You can do this with the Serum CLI:
```bash
serum-cli create-pool <TOKEN_ADDRESS> <PAIRING_TOKEN>
