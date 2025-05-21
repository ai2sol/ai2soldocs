# Key Features

The ai2sol-mcp server offers a comprehensive set of tools for Solana blockchain interactions. Below are the core functionalities:

## 1. Check Solana Balance (check-solana-balance)

Retrieve the SOL balance for a specified wallet address.

## 2. Check Token Balance (check-token-balance)

Fetch the balance of a specific SPL token in a wallet.

## 3. Audit Token Security (audit-token-security)

Analyze security metrics for a given SPL token, including:

- **Mintability**: Checks if the token’s mint authority is disabled.
- **Freeze Authority**: Verifies if the token has a freeze authority enabled.
- **Supply Concentration**: Evaluates the distribution of token supply to detect potential risks.

## 4. Send Solana (send-solana)

Transfer SOL between wallets. **Caution**: Requires careful review to avoid errors or loss of funds.

## 5. Send Tokens (send-token)

Transfer SPL tokens between wallets, supporting various token types.

## 6. Token Swapping (swap-token)

Swap SOL or tokens using Raydium liquidity pools, supporting bidirectional swaps.

## 7. Token Price Lookup (token-price)

Retrieve approximate token prices based on Raydium liquidity pool data.
