# 🔗 TrustChain MVP

<div align="center">

![Stellar](https://img.shields.io/badge/Stellar-Testnet-7B2FBE?style=for-the-badge&logo=stellar)
![React](https://img.shields.io/badge/React-18-61DAFB?style=for-the-badge&logo=react)
![Soroban](https://img.shields.io/badge/Soroban-Smart%20Contracts-FF6B35?style=for-the-badge)
![Vercel](https://img.shields.io/badge/Deployed-Vercel-000000?style=for-the-badge&logo=vercel)
![Level](https://img.shields.io/badge/Level%205-Blue%20Belt-0066FF?style=for-the-badge)

**A decentralized multi-wallet payment and token platform built on Stellar Testnet**

*Level 5 — Blue Belt Submission | Stellar Journey to Mastery Monthly Builder Challenges*

</div>

---

## 🚀 Live Demo

🌐 **Live App:** **[https://trustchain-mvp-omega.vercel.app](https://trustchain-mvp-omega.vercel.app)**

---

## 🎥 Demo Video

📹 **Full MVP Demo:** **[https://www.youtube.com/watch?v=coaLs_8rD8k](https://www.youtube.com/watch?v=coaLs_8rD8k)**

The video demonstrates the complete user flow:
- Connecting Freighter wallet on Stellar Testnet
- Sending XLM transactions
- Calling Soroban smart contracts
- Minting TRUST tokens
- Submitting on-chain feedback (verifiable on Stellar Explorer)
- Live activity feed showing real-time transactions

---

## 📌 Project Overview

TrustChain MVP is a real-world decentralized application (dApp) built on the **Stellar Testnet** that enables trustless, transparent, and verifiable user interactions on the blockchain.

### What it does:
- **Multi-wallet connectivity** — Connect via Freighter, xBull, or Albedo
- **XLM Payments** — Send XLM to any Stellar testnet address with live confirmation
- **Soroban Smart Contracts** — Interact with custom Rust-based contracts directly from the UI
- **TRUST Token Minting** — Mint custom TRUST tokens via Soroban SAC
- **On-chain Feedback** — Each user's feedback fires a real testnet transaction with memo `trustchain-feedback`, permanently verifiable on Stellar Explorer
- **Live Activity Feed** — Real-time transaction history tracking

---

## ✨ Features

| Feature | Description | Status |
|---------|-------------|--------|
| 🔌 Multi-Wallet Support | Freighter, xBull, Albedo | ✅ Live |
| 💸 Send XLM | Send to any testnet address | ✅ Live |
| 📜 Smart Contract Calls | Call Soroban contracts from UI | ✅ Live |
| 🪙 TRUST Token Mint | Custom token via Soroban SAC | ✅ Live |
| ⚡ Live Activity Feed | Real-time transaction tracking | ✅ Live |
| 📋 On-chain Feedback | Memo transaction proof per user | ✅ Live |
| 📱 Responsive Design | Mobile + Desktop | ✅ Live |

---

## 🛠️ Tech Stack

| Layer | Technology |
|-------|-----------|
| Frontend | React 18 + Vite |
| Blockchain | Stellar Testnet |
| Smart Contracts | Soroban (Rust) |
| Horizon API | https://horizon-testnet.stellar.org |
| Wallet Integration | Freighter API, xBull, Albedo |
| Deployment | Vercel (auto CI/CD on push to main) |
| Styling | CSS3, purple gradient responsive design |

---

## 🏗️ Architecture

📄 See full details: **[ARCHITECTURE.md](./ARCHITECTURE.md)**

```
User Browser
     │
     ▼
React Frontend (Vite)
     │
     ├── Wallet Layer
     │     ├── Freighter API
     │     ├── xBull
     │     └── Albedo
     │           │
     │           └── Transaction Signing (local, no private keys exposed)
     │
     ├── Stellar Horizon API (Testnet)
     │     ├── Account Queries
     │     ├── XLM Payment Submission
     │     └── Transaction History
     │
     └── Soroban Smart Contracts
           ├── TrustChain Contract (CBKD4WAM...)
           └── TRUST Token SAC   (CA2KOM5U...)
```

---

## 🚀 Getting Started

### Prerequisites
- Node.js 18+
- [Freighter Wallet](https://www.freighter.app/) browser extension
- Stellar Testnet account funded via [Friendbot](https://friendbot.stellar.org)

### Installation

```bash
git clone https://github.com/Pritty05/trustchain-mvp.git
cd trustchain-mvp
npm install
npm run dev
```

App runs at `http://localhost:5173`

### New User Testnet Setup

1. Install **Freighter** → [https://www.freighter.app/](https://www.freighter.app/)
2. Open Freighter → Settings → Switch network to **Testnet**
3. Copy your wallet address (starts with `G...`)
4. Fund it free → [https://friendbot.stellar.org](https://friendbot.stellar.org)
5. Visit the app → [https://trustchain-mvp-omega.vercel.app](https://trustchain-mvp-omega.vercel.app)
6. Click **Connect Wallet** → Use TrustChain!

---

## 👥 Testnet Users — Level 5 User Validation

**7 real testnet users onboarded** and wallets verified on Stellar Testnet Explorer:

| # | Name | Wallet Address | Rating | Feedback | Explorer |
|---|------|---------------|--------|----------|---------|
| 1 | Parna Dutta | `GBOPQB6MESNP2637PVHJBRVL5AXE6FA57GBD2VEZLSTRJ76UVIXI3O5H` | ⭐⭐⭐⭐ (4/5) | UI improvements | [🔍 View on Explorer](https://stellar.expert/explorer/testnet/account/GBOPQB6MESNP2637PVHJBRVL5AXE6FA57GBD2VEZLSTRJ76UVIXI3O5H) |
| 2 | Ennama Shakeel | `GDLGGNJJPDRXDYI7YO25QMJTDB5REDDNIYJAEJQQP2DVNXWC3CBRN64X` | ⭐⭐⭐⭐⭐ (5/5) | NA | [🔍 View on Explorer](https://stellar.expert/explorer/testnet/account/GDLGGNJJPDRXDYI7YO25QMJTDB5REDDNIYJAEJQQP2DVNXWC3CBRN64X) |
| 3 | Priyanshu Tiwari | `GBA3GN3QJKT4POX4YSCVSTYFZLRAQ644SKHG2NURRPMA3OXK7RJBCA56` | ⭐⭐⭐⭐⭐ (5/5) | It's all good | [🔍 View on Explorer](https://stellar.expert/explorer/testnet/account/GBA3GN3QJKT4POX4YSCVSTYFZLRAQ644SKHG2NURRPMA3OXK7RJBCA56) |
| 4 | Aritrika Das | `GBQEVBFYCZHSHABS6RTGXAQOAAOE72FV2F42A2CEZJUZYFVTAM3S4OQ7` | ⭐⭐⭐⭐⭐ (5/5) | Fine | [🔍 View on Explorer](https://stellar.expert/explorer/testnet/account/GBQEVBFYCZHSHABS6RTGXAQOAAOE72FV2F42A2CEZJUZYFVTAM3S4OQ7) |
| 5 | Preety Paul | `GCSFM4NP6FLUTMDIUCBM7RKGUFUERWGXWM77CRSKL2LTGKUWY3HKTEXB` | ⭐⭐⭐⭐⭐ (5/5) | Looks good | [🔍 View on Explorer](https://stellar.expert/explorer/testnet/account/GCSFM4NP6FLUTMDIUCBM7RKGUFUERWGXWM77CRSKL2LTGKUWY3HKTEXB) |
| 6 | Sunny Prakash | `GBMLOHUNCPKCQJKYD4ZMWMO7JPEPNEN37ZSJVFQLIFUPV2O6BTARKIYT` | ⭐⭐⭐⭐⭐ (5/5) | All is okay | [🔍 View on Explorer](https://stellar.expert/explorer/testnet/account/GBMLOHUNCPKCQJKYD4ZMWMO7JPEPNEN37ZSJVFQLIFUPV2O6BTARKIYT) |
| 7 | Vaibhav Goyal | `GCD6VREATHDHUOUFB2YCSFO3BJV4SMGPE2XIOMJA6GFV2YWTNNIKZFHL` | ⭐⭐⭐⭐⭐ (5/5) | Nice | [🔍 View on Explorer](https://stellar.expert/explorer/testnet/account/GCD6VREATHDHUOUFB2YCSFO3BJV4SMGPE2XIOMJA6GFV2YWTNNIKZFHL) |

> 🌟 **Average Rating: 4.86 / 5** across 7 real testnet users

---

## 📊 User Feedback Documentation

### Google Form
Users were onboarded via a structured Google Form collecting: **Full Name, Email Address, Stellar Wallet Address, Product Rating (1–5), and Improvement Suggestions.**

📝 **User Onboarding Form:** [https://docs.google.com/forms/d/e/1FAIpQLScCgc-YNdstJDQCW2sVOVOh6xXkwvCVLBGP9bX-eZvxf30sRA/viewform](https://docs.google.com/forms/d/e/1FAIpQLScCgc-YNdstJDQCW2sVOVOh6xXkwvCVLBGP9bX-eZvxf30sRA/viewform)

### Exported Feedback Data (CSV)
All 7 responses exported for analysis and record-keeping:

📊 **Download Feedback Sheet:** **[Untitled_form.csv](./Untitled_form.csv)**

> The CSV file is committed to this repository and contains all 7 user responses with timestamps, names, emails, wallet addresses, ratings, and feedback comments.

### Feedback Analysis Summary

| Metric | Value |
|--------|-------|
| Total Responses | 7 |
| Average Rating | 4.86 / 5 ⭐ |
| Users rating 5/5 | 6 out of 7 (86%) |
| Users rating 4/5 | 1 out of 7 (14%) |
| Main feedback theme | UI polish, overall very positive |

---

## 🔄 Improvement Plan — Based on User Feedback

### ✅ Iteration 1 — Completed (Level 5)

**Feedback received:** User 1 (Parna Dutta) rated 4/5 and suggested UI improvements.

**Problem identified:** Users found the feedback submission flow unclear — it was just a static link to a Google Form with no blockchain interaction.

**Fix implemented:** Replaced the static Google Form link with an on-chain feedback button that:
1. Fires a real Stellar testnet transaction (0.0000001 XLM, memo: `trustchain-feedback`)
2. Shows the transaction hash with a live Stellar Explorer link
3. Then opens the Google Form automatically

This gives every user a permanent, verifiable blockchain footprint proving they used the app.

**Git Commit:** [fix: freighter signed XDR handling](https://github.com/Pritty05/trustchain-mvp/commit/437cd4d) — https://github.com/Pritty05/trustchain-mvp/commit/437cd4d

---

### 🔜 Phase 2 — Planned Improvements for Level 6

Based on all 7 user responses, here is the prioritized improvement roadmap:

| Priority | Improvement | Based On | Target Phase |
|----------|-------------|----------|--------------|
| 🔴 High | Step-by-step onboarding wizard inside app | User 1 UI feedback | Level 6 |
| 🔴 High | Scale to 30+ active testnet users | Level 6 requirement | Level 6 |
| 🟡 Medium | Live metrics dashboard (DAU, total tx, tokens minted) | Product growth | Level 6 |
| 🟡 Medium | Persistent transaction history panel | User request | Level 6 |
| 🟡 Medium | Mobile wallet UX improvements | Responsive feedback | Level 6 |
| 🟢 Low | Gasless transactions via fee bump sponsorship | Advanced Stellar feature | Level 6 |
| 🟢 Low | Full security audit checklist | Production readiness | Level 6 |
| 🟢 Low | Data indexing via Horizon streaming | Performance | Level 6 |
| 🟢 Low | Stellar community contribution (Twitter/Discord) | Community building | Level 6 |

---

## 📜 Smart Contracts

| Contract | Address | Network |
|----------|---------|---------|
| TrustChain Contract | `CBKD4WAM25RMVZ7KFZE5IUFYW7HWLEHY2F6QU5VQ4NEZIZXEOL7DEQSK` | Stellar Testnet |
| TRUST Token SAC | `CA2KOM5UCLNG5ZQZ2D3FQMKH2QPHCYNT27SWMTIYFNOAVHNX3PRM2HUF` | Stellar Testnet |

---

## 📁 Project Structure

```
trustchain-mvp/
├── src/
│   ├── App.jsx           # Main app — wallet, transactions, feedback
│   ├── App.css           # Styling — purple gradient theme
│   ├── main.jsx          # React entry point
│   └── assets/           # Static assets
├── public/               # Public assets
├── ARCHITECTURE.md       # Full architecture documentation ✅
├── README.md             # This file ✅
├── Untitled_form.csv     # Exported user feedback CSV ✅
├── package.json
├── vite.config.js
└── index.html
```

---

## ✅ Level 5 Submission Checklist

| Requirement | Status | Link |
|-------------|--------|------|
| Public GitHub repository | ✅ Done | [github.com/Pritty05/trustchain-mvp](https://github.com/Pritty05/trustchain-mvp) |
| MVP fully functional | ✅ Done | [trustchain-mvp-omega.vercel.app](https://trustchain-mvp-omega.vercel.app) |
| README with complete documentation | ✅ Done | This file |
| Architecture document included | ✅ Done | [ARCHITECTURE.md](./ARCHITECTURE.md) |
| Minimum 10+ meaningful commits | ✅ Done | 12 commits on main branch |
| Live demo link | ✅ Done | https://trustchain-mvp-omega.vercel.app |
| Demo video link | ✅ Done | https://youtu.be/qK3RfrvmEK |
| 5+ user wallet addresses (verifiable) | ✅ Done | 7 users listed above with Explorer links |
| User feedback documentation | ✅ Done | [Untitled_form.csv](./Untitled_form.csv) |
| Google Form created | ✅ Done | Name, Email, Wallet, Rating, Feedback |
| Responses exported to Excel/CSV | ✅ Done | Attached in repo |
| CSV linked in README | ✅ Done | See feedback section above |
| Improvement plan with git commit link | ✅ Done | See improvement section above |
| 5+ real testnet users | ✅ Done | 7 users onboarded |
| 1 iteration completed | ✅ Done | On-chain feedback transaction added |

---

## 🌐 Deployment

| Detail | Value |
|--------|-------|
| Platform | Vercel |
| Live URL | https://trustchain-mvp-omega.vercel.app |
| CI/CD | Auto-deploys on every push to `main` |
| Network | Stellar Testnet |
| Repo | https://github.com/Pritty05/trustchain-mvp |

---

<div align="center">

*Built with ❤️ for the Stellar ecosystem*

**[🌐 Live Demo](https://trustchain-mvp-omega.vercel.app) • [🎥 Demo Video](https://www.youtube.com/watch?v=coaLs_8rD8k) • [💻 GitHub](https://github.com/Pritty05/trustchain-mvp)**

*Stellar Journey to Mastery — Level 5 Blue Belt Submission*

</div>