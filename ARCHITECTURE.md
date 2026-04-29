# 🏗️ TrustChain Architecture Document

## System Overview
TrustChain is a decentralized application (dApp) built on the Stellar blockchain, featuring Soroban smart contracts, multi-wallet support, and Fee Bump (gasless) transactions.

## Tech Stack
| Layer | Technology |
|-------|-----------|
| Frontend | React 18 + Vite |
| Blockchain | Stellar Testnet |
| Smart Contracts | Soroban |
| Wallet Integration | Freighter API |
| Deployment | Vercel |
| Fee Sponsorship | Stellar Fee Bump |

## Component Architecture

```
trustchain-black-belt/
├── src/
│   ├── App.jsx          # Main app component
│   ├── App.css          # Styles
│   └── main.jsx         # Entry point
├── public/              # Static assets
├── ARCHITECTURE.md      # This file
├── SECURITY.md          # Security checklist
├── TECHNICAL.md         # Technical docs + user guide
└── README.md            # Main documentation
```

## Data Flow

```
User Action
    ↓
React State Update
    ↓
Freighter API Call (sign transaction)
    ↓
Freighter Popup (user approves)
    ↓
Stellar Horizon API (submit transaction)
    ↓
Stellar Testnet (confirm transaction)
    ↓
UI Update (show hash + Explorer link)
```

## Smart Contract Architecture

```
TrustChain Contract (CBKD4WAM...)
    ├── getLatestLedger()     → Current ledger info
    └── [custom functions]    → Business logic

TrustToken Contract (CA2KOM5U...)
    ├── Token: TRUST (TRT)
    ├── getLatestLedger()     → Current ledger info
    └── [token functions]     → Mint, transfer, balance
```

## Fee Bump Architecture (Advanced Feature)

```
User
  │ Signs inner transaction
  ↓
Inner Transaction (user's operation)
  │
  ↓
Fee Bump Wrapper (sponsor pays fees)
  │ Sponsor account signs
  ↓
Stellar Network
  │ Confirms transaction
  ↓
User pays ZERO fees ✅
```

## Security Architecture

```
Frontend (Public)
  ├── No private keys
  ├── No API secrets  
  └── Read-only contract calls

Freighter Extension (User's Device)
  ├── Private key stored locally
  ├── Signs transactions locally
  └── User approves every tx

Stellar Network (Public)
  ├── All transactions verifiable
  ├── Immutable transaction history
  └── Cryptographic security
```

## Deployment Architecture

```
GitHub Repository
    ↓ (push)
Vercel CI/CD
    ↓ (auto-deploy)
Vercel Edge Network (CDN)
    ↓ (HTTPS)
User Browser
```

## Monitoring Architecture

```
Live Activity Feed (in-app)
    ├── All user actions logged
    ├── Transaction hashes stored
    └── Error messages displayed

Stellar Explorer (external)
    ├── All transactions indexed
    ├── Account balances tracked
    └── Contract calls verified

Horizon API (external)
    ├── Real-time blockchain data
    ├── Account sequence numbers
    └── Transaction status
```