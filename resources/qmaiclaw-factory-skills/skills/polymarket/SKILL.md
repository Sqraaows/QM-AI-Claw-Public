# Polymarket

**Source**: https://clawhub.ai/joelchance/polymarket

Query Polymarket prediction markets from the terminal. Read-only commands work immediately.

## Setup

Read-only commands work without install.

For trading, install [Polymarket CLI](https://github.com/Polymarket/polymarket-cli):
```bash
curl -sSL https://raw.githubusercontent.com/Polymarket/polymarket-cli/main/install.sh | sh
```

## Commands

### Browse Markets (no CLI needed)
```bash
# Trending/active markets
polymarket trending

# Search markets
polymarket search "trump"

# Get specific event
polymarket event "fed-decision-in-october"

# Get by category
polymarket category politics
polymarket category crypto
```

### Order Book & Prices (CLI required)
```bash
# Order book for token
polymarket book TOKEN_ID

# Price history
polymarket price-history TOKEN_ID --interval 1d
```

### Wallet (CLI + wallet required)
```bash
polymarket wallet-setup
polymarket wallet-show
polymarket wallet-balance
```

### Trading (CLI + wallet required)
⚠️ All trades require `--confirm` to execute. Without it, preview only.

```bash
# Buy limit order: 10 shares at $0.50
polymarket --confirm trade buy --token TOKEN_ID --price 0.50 --size 10

# Market order: buy $5 worth
polymarket --confirm trade buy --token TOKEN_ID --market-order --amount 5
```

### Orders & Positions
```bash
polymarket orders                           # List open orders
polymarket --confirm orders --cancel ORDER_ID  # Cancel order
polymarket --confirm orders --cancel all       # Cancel all
polymarket positions                         # View positions
```

## Example Chat Usage

- "What are the odds Trump wins 2028?"
- "Trending on Polymarket?"
- "Search Polymarket for Bitcoin"
- "Show me the order book for [token]"
- "Buy 10 shares of YES on [market] at $0.45"
- "What are my open positions?"

## ⚠️ Safety Notes

- Real money. Trades execute on Polygon with real USDC.
- All trades require `--confirm`. Without it, preview only.
- CLI is experimental - use at your own risk
- Private key stored in `~/.config/polymarket/config.json`
- Gas fees require MATIC on Polygon

---

*Install date: 2026-04-27*
