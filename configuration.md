# Configuration

To use the ai2sol-mcp server, configure it in your MCP settings file. The configuration specifies the server’s runtime environment and tool permissions.

## Configuration File Location

- **macOS**: `~/Library/Application Support/Claude/claude_desktop_config.json`
- **Windows**: `%APPDATA%/Claude/claude_desktop_config.json`

## Example Configuration

```json
{
  "ai2sol-solana-to-ai": {
    "command": "node",
    "args": ["/path/to/ai2sol-mcp/dist/index.js"],
    "disabled": false,
    "autoApprove": [
      "check-solana-balance",
      "audit-token-security",
      "token-price"
    ],
    "env": {
      "USER_WALLET": "YOUR-WALLET-PUBLIC-KEY-HERE",
      "USER_PRIVATE_KEY": "YOUR-PRIVATE-KEY-HERE",
      "RPC_ENDPOINT": "" // Leave empty to use Solana mainnet-beta public RPC
    }
  }
}
```

## Configuration Notes

- **USER_WALLET**: Your Solana wallet’s public key (e.g., `5xY...`).
- **USER_PRIVATE_KEY**: Your wallet’s private key. Store securely—preferably in a `.env` file or environment variables.
- **RPC_ENDPOINT**: Optional. Defaults to Solana’s mainnet-beta public RPC (`https://api.mainnet-beta.solana.com`). For better performance, use a private RPC (e.g., QuickNode, Alchemy).
- **autoApprove**: Lists tools that can run without manual approval. Transactional tools like `send-solana` and `send-token` should not be auto-approved for safety.

### Security Warning

- Never hardcode private keys in configuration files.
- Use a `.env` file with a library like `dotenv` to load sensitive variables.
- Restrict file permissions to prevent unauthorized access.
