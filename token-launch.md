
---

### **6. `token-launch.md` (Token Launch and Market Setup)**

```markdown
# Launching Your Token Into the Market

Once you’ve created the token and set up liquidity, it’s time to launch your token into the market.

## Prerequisites:
- Your token created and minted as per [Creating a Token](token-creation.md)
- Liquidity set up on a DEX as per [Setting Up Liquidity](liquidity-setup.md)

## Steps to Launch Your Token:
### 1. Mint Tokens for Sale
If you have a total of 1 billion tokens and you want to offer 90% of them for sale, mint the following:
```bash
spl-token mint <TOKEN_ADDRESS> 900000000 <SALE_ACCOUNT_ADDRESS>

## 2. Listing Tokens
Tokens can be listed in various ways depending on the platform's architecture. Common methods include:

All Tokens: Displaying a comprehensive list of all available tokens on the platform.
My Tokens: Showing only the tokens that a specific user owns or has interacted with.




