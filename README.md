# Wallet Audit V2

A local-first Python desktop application for extracting wallet data, deriving MetaMask-compatible public addresses, and checking balances across 12 popular EVM networks.

## Supported networks

- Ethereum
- BNB Smart Chain
- Polygon
- Arbitrum One
- Optimism
- Base
- Avalanche C-Chain
- Gnosis
- Linea
- zkSync Era
- Mantle
- Sonic

Bitcoin and Fantom are intentionally excluded.

## Reported assets

The reports include native and selected wrapped balances for:

- ETH
- WETH
- BNB
- POL
- AVAX
- xDAI
- MNT
- S

Polygon WETH is checked using contract `0x7ceB23fD6bC0adD59E62ac25578270cFf1b9f619`.

## Features

- Extracts valid BIP39 recovery phrases and EVM addresses from TXT, CSV, TSV, XLS, XLSX, or pasted text
- Derives MetaMask-compatible addresses using `m/44'/60'/0'/0/index`
- Performs batched EVM balance requests
- Keeps recovery phrases local; only public addresses are sent to RPC and price services
- Produces address-level and seed-level portfolio reports
- Creates a filtered report containing only records with at least `0.001` of a checked asset
- Requires no third-party Python packages

## Installation and use

1. Install Python 3.11 or newer.
2. Download or clone this repository.
3. On Windows, double-click **Launch Wallet Audit.bat**, or run:

```powershell
python wallet_audit.py
```

4. Add input files or paste mixed text into the application.
5. Choose the number of MetaMask accounts to derive per phrase.
6. Click **Extract and derive**.
7. Click **Check balances**.
8. Click **Export results** and select an output folder.

## Exported files

- `seed_phrases_PRIVATE.csv` and `seed_phrases_PRIVATE.txt`: recovery phrases, when private export is enabled
- `address_mapping.csv`: derived addresses and paths linked by seed ID
- `address_portfolio.csv`: one row per public address
- `seed_portfolio_PRIVATE.csv`: one aggregate row per seed phrase
- `balances_found_PRIVATE.csv`: only seeds or listed wallets meeting the `0.001` threshold
- `balances.csv`: raw per-chain balance records and query statuses
- `public_addresses.txt`: unique public addresses

## Security

Recovery phrases control funds. Never commit them, upload them, paste them into a website, or use a phrase you still need in an online or untrusted environment. Store private exports offline and delete them when they are no longer required.

The included `.gitignore` excludes the application's private export filenames and local result files.

## Limitations

This application is a focused EVM balance checker. It does not inspect every token, NFT, DeFi position, exchange account, pending transaction, or derivation path. Public RPC endpoints and price services can be unavailable or rate-limited. Empty values and request errors must not be interpreted as confirmed zero balances.

## License

MIT
