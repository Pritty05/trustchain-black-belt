# 🏗️ TrustChain MVP — Architecture Document

> Level 5 — Blue Belt Submission | Stellar Journey to Mastery Monthly Builder Challenges

---

## 📌 Overview

TrustChain MVP is a decentralized application (dApp) built on the **Stellar Testnet**. It enables users to connect multiple wallets, send XLM, interact with Soroban smart contracts, mint TRUST tokens, and submit verifiable on-chain feedback — all through a clean React frontend deployed on Vercel.

---

## 🧱 Tech Stack

| Layer | Technology | Purpose |
|-------|-----------|---------|
| Frontend | React 18 + Vite | UI and user interactions |
| Blockchain | Stellar Testnet | Transaction processing |
| Smart Contracts | Soroban (Rust) | On-chain business logic |
| Horizon API | Stellar Horizon Testnet | Account queries, tx submission |
| Wallet Layer | Freighter API, xBull, Albedo | Transaction signing |
| Deployment | Vercel | Hosting + CI/CD |
| Styling | CSS3 | Responsive purple gradient UI |

---

## 🗺️ System Architecture Diagram

```
┌──────────────────────────────────────────────────────────┐
│                      USER BROWSER                        │
│                                                          │
│   ┌──────────────────────────────────────────────────┐   │
│   │           React Frontend (Vite)                  │   │
│   │                                                  │   │
│   │  ┌────────────┐  ┌─────────┐  ┌──────────────┐  │   │
│   │  │ Freighter  │  │  xBull  │  │    Albedo    │  │   │
│   │  └─────┬──────┘  └────┬────┘  └──────┬───────┘  │   │
│   │        └──────────────┴──────────────┘           │   │
│   │                   Wallet Layer                   │   │
│   │              (local tx signing only)             │   │
│   │                       │                         │   │
│   └───────────────────────┼─────────────────────────┘   │
└───────────────────────────┼──────────────────────────────┘
                            │
              ┌─────────────▼──────────────┐
              │   Stellar Horizon API       │
              │   (Testnet)                 │
              │   horizon-testnet.stellar.org│
              │                             │
              │  • Load account info        │
              │  • Submit XLM payments      │
              │  • Submit feedback tx       │
              │  • Fetch transaction history│
              └─────────────┬───────────────┘
                            │
              ┌─────────────▼──────────────┐
              │  Soroban Smart Contracts    │
              │  (Stellar Testnet)          │
              │                             │
              │  • TrustChain Contract      │
              │    CBKD4WAM25RMVZ7...       │
              │                             │
              │  • TRUST Token SAC          │
              │    CA2KOM5UCLNG5Z...        │
              └─────────────────────────────┘
```

---

## 🔄 Complete User Flow

```
1. User visits trustchain-mvp-omega.vercel.app
         │
         ▼
2. Clicks "Connect Wallet" → selects Freighter/xBull/Albedo
         │
         ▼
3. Wallet popup appears → User approves connection
         │
         ▼
4. App loads wallet address + XLM balance from Horizon API
         │
         ├──► SEND XLM
         │       │
         │       ▼
         │    Enter recipient + amount → Freighter signs
         │       │
         │       ▼
         │    Transaction submitted to Horizon → confirmed ✅
         │
         ├──► CALL SOROBAN CONTRACT
         │       │
         │       ▼
         │    Invoke TrustChain contract function
         │       │
         │       ▼
         │    Freighter signs → submitted to Testnet ✅
         │
         ├──► MINT TRUST TOKEN
         │       │
         │       ▼
         │    Call TRUST Token SAC contract
         │       │
         │       ▼
         │    Tokens minted to wallet ✅
         │
         └──► FILL FEEDBACK FORM
                 │
                 ▼
            Button clicked → check wallet connected
                 │
                 ▼
            Build transaction (0.0000001 XLM to self)
            with memo: "trustchain-feedback"
                 │
                 ▼
            Freighter popup → User signs
                 │
                 ▼
            Transaction submitted → Hash returned
                 │
                 ▼
            Transaction hash + Explorer link shown ✅
                 │
                 ▼
            Google Form opens automatically ✅
```

---

## 📦 Frontend Component Structure

```
App.jsx (main component)
├── State Management
│   ├── walletAddress       — connected wallet public key
│   ├── walletType          — freighter | xbull | albedo
│   ├── balance             — XLM balance
│   ├── activityFeed        — recent transactions array
│   └── txHash              — feedback transaction hash
│
├── Wallet Connection Section
│   ├── Connect Wallet button
│   ├── Wallet selector modal (Freighter / xBull / Albedo)
│   └── Connected wallet display (address + balance)
│
├── Send XLM Section
│   ├── Recipient address input
│   ├── Amount input
│   └── Send button → Horizon submit
│
├── Call Contract Section
│   ├── Contract address display
│   └── Invoke function button → Soroban call
│
├── Mint TRUST Token Section
│   └── Mint button → TRUST Token SAC call
│
├── Live Activity Feed
│   └── Recent transactions list (real-time)
│
└── Feedback Banner
    ├── On-chain feedback button
    │   └── fires tx → shows hash → opens Google Form
    └── Transaction hash display + Explorer link
```

---

## 📜 Smart Contracts

### TrustChain Core Contract
- **Address:** `CBKD4WAM25RMVZ7KFZE5IUFYW7HWLEHY2F6QU5VQ4NEZIZXEOL7DEQSK`
- **Network:** Stellar Testnet
- **Language:** Rust (Soroban)
- **Purpose:** Core on-chain business logic for TrustChain

### TRUST Token Contract (SAC)
- **Address:** `CA2KOM5UCLNG5ZQZ2D3FQMKH2QPHCYNT27SWMTIYFNOAVHNX3PRM2HUF`
- **Network:** Stellar Testnet
- **Language:** Rust (Soroban SAC)
- **Purpose:** Custom fungible token for the TrustChain ecosystem

---

## 🔐 Security Design

| Concern | How Addressed |
|---------|--------------|
| Private key exposure | Never stored/transmitted — all signing done locally in browser extension |
| Transaction approval | Every transaction requires explicit user approval in Freighter popup |
| Network risk | All operations on Testnet — no real funds at risk |
| API security | Read-only Horizon API calls for account queries |
| XDR handling | Handles all Freighter response formats (string, signedTxXdr, xdr) |

---

## 🚀 Deployment Architecture

```
Developer pushes code to GitHub
        │
        ▼
GitHub → Vercel webhook triggered
        │
        ▼
Vercel auto-build: npm run build
        │
        ▼
Vite bundles React app → static files
        │
        ▼
Deployed to Vercel Edge CDN globally
        │
        ▼
Live at: https://trustchain-mvp-omega.vercel.app
```

- **Build tool:** Vite
- **Output:** Static HTML/CSS/JS
- **CDN:** Vercel Edge Network
- **Deploy time:** ~60 seconds from push to live

---

## 📈 Level 6 Planned Architecture Additions

| Feature | Architecture Change |
|---------|-------------------|
| 30+ user scale | User registry smart contract in Soroban |
| Live metrics dashboard | Horizon streaming API + React state |
| Gasless transactions | Fee bump transaction wrapper |
| Data indexing | Custom indexer or SubQuery integration |
| Security audit | Input validation + rate limiting layer |
| Production monitoring | Logging + alerting integration |

---

## 🔗 Key URLs

| Resource | URL |
|----------|-----|
| Live App | https://trustchain-mvp-omega.vercel.app |
| GitHub Repo | https://github.com/Pritty05/trustchain-mvp |
| Horizon Testnet | https://horizon-testnet.stellar.org |
| Stellar Explorer | https://stellar.expert/explorer/testnet |
| Soroban Docs | https://developers.stellar.org/docs/smart-contracts |

---

*TrustChain MVP — Built for Stellar Journey to Mastery, Level 5 Blue Belt*