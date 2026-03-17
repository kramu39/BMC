# BuyMeCoffee (BMC) — Stacks SIP-010 Token

A fully on-chain tipping token built on the [Stacks](https://www.stacks.co) blockchain using [Clarity](https://clarity-lang.org) smart contracts. Anyone can mint **BMC** tokens and send them as a coffee tip to their favourite builders.

---

## What is BMC?

| Property | Value |
|---|---|
| Token Name | BuyMeCoffee |
| Symbol | BMC |
| Standard | SIP-010 Fungible Token |
| Decimals | 6 |
| Max Supply | 1,000,000 BMC |
| Mint Price | 1 µSTX per unit |
| Network | Stacks (mainnet / testnet) |

The deployer becomes the contract owner and receives all STX paid during mints.

---

## Repository Structure

```
BMC/
├── contracts/                  # Clarity smart contracts & tests
│   ├── contracts/
│   │   └── buy-me-coffee-token.clar   # SIP-010 BMC token contract
│   ├── tests/                  # Clarinet unit tests (Vitest)
│   ├── Clarinet.toml           # Clarinet project config
│   └── settings/               # Network settings (gitignored for mainnet/testnet)
├── dapp/                       # Front-end dApp (coming soon)
└── .gitignore
```

---

## Getting Started

### Prerequisites

| Tool | Purpose | Install |
|---|---|---|
| [Clarinet](https://github.com/hirosystems/clarinet) | Clarity dev & test toolchain | See below |
| Node.js ≥ 18 | Run tests | [nodejs.org](https://nodejs.org) |

### Install Clarinet

```bash
# macOS / Linux via Homebrew
brew install clarinet

# Or via the installer script
curl -sS https://downloads.hiro.so/clarinet/install.sh | sh
```

### Clone & Run Tests

```bash
git clone https://github.com/kramu39/BMC.git
cd BMC/contracts
npm install
npx clarinet test
```

---

## Contract: `buy-me-coffee-token.clar`

### Public Functions

| Function | Description |
|---|---|
| `mint (amount uint) (recipient principal)` | Mint BMC tokens; pays STX to contract owner |
| `transfer (amount uint) (sender principal) (recipient principal) (memo ...)` | SIP-010 transfer |

### Read-Only Functions

`get-balance`, `get-total-supply`, `get-name`, `get-symbol`, `get-decimals`, `get-token-uri`

### Error Codes

| Code | Meaning |
|---|---|
| `u100` | Owner only |
| `u101` | Not token owner |
| `u102` | Invalid amount |
| `u103` | Max supply reached |
| `u104` | Payment failed |

---

## Contributing

1. Fork the repo and create a feature branch.
2. Write or update Clarity contracts under `contracts/contracts/`.
3. Add tests in `contracts/tests/`.
4. Run `npx clarinet check` and `npx clarinet test` — all tests must pass.
5. Open a pull request against `main`.

---

## License

MIT — use freely, tip generously.
