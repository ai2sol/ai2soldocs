# Usage Examples

Below are practical examples for each tool, including command syntax, sample output, and important notes.

## 1. Check Solana Balance (check-solana-balance)

**Syntax**:
```bash
node dist/index.js check-solana-balance --wallet <WALLET_ADDRESS>
```

**Example**:
```bash
node dist/index.js check-solana-balance --wallet 5xY2...abc
```

**Sample Output**:
```json
{
  "wallet": "5xY2...abc",
  "balance": 2.345,
  "unit": "SOL"
}
```

**Notes**:
- Requires a valid Solana wallet address.
- Balance is returned in SOL (not lamports).

## 2. Check Token Balance (check-token-balance)

**Syntax**:
```bash
node dist/index.js check-token-balance --wallet <WALLET_ADDRESS> --token <TOKEN_MINT_ADDRESS>
```

**Example**:
```bash
node dist/index.js check-token-balance --wallet 5xY2...abc --token EPjFW...xyz
```

**Sample Output**:
```json
{
  "wallet": "5xY2...abc",
  "token": "EPjFW...xyz",
  "balance": 1000.50,
  "symbol": "USDC"
}
```

**Notes**:
- Ensure the token mint address is valid.
- Returns balance in the token’s native units.

## 3. Audit Token Security (audit-token-security)

**Syntax**:
```bash
node dist/index.js audit-token-security --token <TOKEN_MINT_ADDRESS>
```

**Example**:
```bash
node dist/index.js audit-token-security --token EPjFW...xyz
```

**Sample Output**:
```json
{
  "token": "EPjFW...xyz",
  "mintable": false,
  "freezeAuthority": null,
  "supplyConcentration": {
    "topHolderPercentage": 15.3,
    "top10Holders": 45.7
  },
  "securityStatus": "Safe"
}
```

**Notes**:
- Checks for potential red flags (e.g., active mint authority, concentrated supply).
- Use to evaluate token trustworthiness before trading.

## 4. Send Solana (send-solana)

**Syntax**:
```bash
node dist/index.js send-solana --from <SENDER_WALLET> --to <RECEIVER_WALLET> --amount <AMOUNT>
```

**Example**:
```bash
node dist/index.js send-solana --from 5xY2...abc --to 7zW3...def --amount 1.5
```

**Sample Output**:
```json
{
  "transactionId": "2x3y...ghi",
  "status": "Confirmed",
  "amount": 1.5,
  "unit": "SOL"
}
```

**Notes**:
- Warning: Double-check the recipient address and amount. Transactions are irreversible.
- Requires `USER_PRIVATE_KEY` in the configuration.
- Ensure sufficient SOL for fees.

## 5. Send Tokens (send-token)

**Syntax**:
```bash
node dist/index.js send-token --from <SENDER_WALLET> --to <RECEIVER_WALLET> --token <TOKEN_MINT_ADDRESS> --amount <AMOUNT>
```

**Example**:
```bash
node dist/index.js send-token --from 5xY2...abc --to 7zW3...def --token EPjFW...xyz --amount 100
```

**Sample Output**:
```json
{
  "transactionId": "4a5b...jkl",
  "status": "Confirmed",
  "amount": 100,
  "token": "EPjFW...xyz"
}
```

**Notes**:
- Verify token mint and recipient address.
- Ensure the sender has sufficient token balance and SOL for fees.

## 6. Token Swapping (swap-token)

**Syntax**:
```bash
node dist/index.js swap-token --wallet <WALLET_ADDRESS> --from <FROM_TOKEN> --to <TO_TOKEN> --amount <AMOUNT>
```

**Example**:
```bash
node dist/index.js swap-token --wallet 5xY2...abc --from SOL --to EPjFW...xyz --amount 1
```

**Sample Output**:
```json
{
  "transactionId": "6c7d...mno",
  "status": "Confirmed",
  "from": "SOL",
  "to": "USDC",
  "amountIn": 1,
  "amountOut": 150.25
}
```

**Notes**:
- Uses Raydium liquidity pools for swaps.
- Check pool liquidity and slippage settings to avoid unexpected losses.

## 7. Token Price Lookup (token-price)

**Syntax**:
```bash
node dist/index.js token-price --token <TOKEN_MINT_ADDRESS>
```

**Example**:
```bash
node dist/index.js token-price --token EPjFW...xyz
```

**Sample Output**:
```json
{
  "token": "EPjFW...xyz",
  "symbol": "USDC",
  "price": 1.002,
  "unit": "USD"
}
```

**Notes**:
- Prices are approximate, sourced from Raydium liquidity pools.
- Use for quick reference, not guaranteed for trading.
