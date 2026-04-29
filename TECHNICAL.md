# 📚 TrustChain — Technical Documentation & User Guide

## Table of Contents
1. [Architecture Overview](#architecture)
2. [Smart Contracts](#contracts)
3. [Advanced Feature: Fee Sponsorship](#fee-sponsorship)
4. [API Reference](#api)
5. [User Guide](#user-guide)
6. [Troubleshooting](#troubleshooting)

---

## 🏗️ Architecture Overview {#architecture}

```
┌─────────────────────────────────────────┐
│           User Browser                   │
│  ┌─────────────────────────────────┐    │
│  │   React + Vite Frontend          │    │
│  │   (trustchain-black-belt)        │    │
│  └──────────────┬──────────────────┘    │
│                 │                        │
│  ┌──────────────▼──────────────────┐    │
│  │   Freighter Wallet Extension     │    │
│  │   (Signs transactions locally)   │    │
│  └──────────────┬──────────────────┘    │
└─────────────────┼───────────────────────┘
                  │
     ┌────────────▼────────────┐
     │   Stellar Horizon API    │
     │   (horizon-testnet)      │
     └────────────┬────────────┘
                  │
     ┌────────────▼────────────┐
     │   Stellar Testnet        │
     │   Blockchain             │
     │  ┌──────────────────┐   │
     │  │ TrustChain       │   │
     │  │ Soroban Contract │   │
     │  └──────────────────┘   │
     │  ┌──────────────────┐   │
     │  │ TrustToken (TRT) │   │
     │  │ Soroban Contract │   │
     │  └──────────────────┘   │
     └─────────────────────────┘
```

---

## 📜 Smart Contracts {#contracts}

### TrustChain Contract
- **ID:** `CBKD4WAM25RMVZ7KFZE5IUFYW7HWLEHY2F6QU5VQ4NEZIZXEOL7DEQSK`
- **Network:** Stellar Testnet
- **Explorer:** [View Contract](https://stellar.expert/explorer/testnet/contract/CBKD4WAM25RMVZ7KFZE5IUFYW7HWLEHY2F6QU5VQ4NEZIZXEOL7DEQSK)

### TrustToken Contract (TRUST/TRT)
- **ID:** `CA2KOM5UCLNG5ZQZ2D3FQMKH2QPHCYNT27SWMTIYFNOAVHNX3PRM2HUF`
- **Token:** TRUST (TRT)
- **Network:** Stellar Testnet
- **Explorer:** [View Contract](https://stellar.expert/explorer/testnet/contract/CA2KOM5UCLNG5ZQZ2D3FQMKH2QPHCYNT27SWMTIYFNOAVHNX3PRM2HUF)

---

## ⛽ Advanced Feature: Fee Sponsorship {#fee-sponsorship}

### What is Fee Bump?
Stellar's Fee Bump allows a sponsor account to pay transaction fees on behalf of users, enabling truly gasless transactions.

### Implementation Flow:
```
1. User initiates transaction
      ↓
2. Inner transaction built (user's operation)
      ↓
3. User signs inner transaction via Freighter
      ↓
4. Sponsor wraps with Fee Bump transaction
      ↓
5. Sponsor signs and submits
      ↓
6. User's transaction confirmed — ZERO fees paid by user
```

### Code Pattern:
```javascript
// Inner transaction (user signs this)
const innerTx = new TransactionBuilder(userAccount, {
  fee: BASE_FEE,
  networkPassphrase: Networks.TESTNET,
})
  .addOperation(Operation.payment({...}))
  .addMemo(Memo.text("trustchain-gasless"))
  .setTimeout(30)
  .build();

// Fee Bump (sponsor signs this — happens on backend)
const feeBumpTx = TransactionBuilder.buildFeeBumpTransaction(
  sponsorKeypair,           // sponsor pays fees
  (BASE_FEE * 10).toString(),
  signedInnerTx,
  Networks.TESTNET
);
feeBumpTx.sign(sponsorKeypair);
await server.submitTransaction(feeBumpTx);
```

### Sponsor Account:
```
Public: GAHJJJKMOKYE4RVPZEWZTKH5FVI4PA3VL7GK2LFNUBSGBV4UUZH7UNG
```

---

## 🔌 API Reference {#api}

### Horizon API Endpoints Used

| Endpoint | Purpose |
|----------|---------|
| `GET /accounts/{id}` | Fetch account balance + sequence |
| `POST /transactions` | Submit signed transaction |
| `GET /accounts/{id}/transactions` | Transaction history |

### Soroban RPC Endpoints

| Method | Purpose |
|--------|---------|
| `getLatestLedger` | Get current ledger info |
| `simulateTransaction` | Simulate contract call |

---

## 📖 User Guide {#user-guide}

### Getting Started

**Step 1: Install Freighter**
1. Go to [freighter.app](https://freighter.app)
2. Click "Add to Chrome"
3. Create a new wallet or import existing

**Step 2: Switch to Testnet**
1. Open Freighter extension
2. Click the 🌐 globe icon (top left)
3. Select "Test Net"

**Step 3: Get Free Testnet XLM**
1. Copy your wallet address from Freighter (G... address)
2. Go to: `https://friendbot.stellar.org/?addr=YOUR_ADDRESS`
3. Press Enter → 10,000 free XLM added!

**Step 4: Connect to TrustChain**
1. Go to [trustchain-black-belt-iwpx.vercel.app](https://trustchain-black-belt-iwpx.vercel.app)
2. Click "Connect Wallet"
3. Select "Freighter"
4. Approve in Freighter popup

### Sending XLM
1. Connect wallet
2. Go to "Send XLM" tab
3. Enter recipient address (G...)
4. Enter amount
5. Click "Send XLM"
6. Approve in Freighter

### Using Gasless Transactions
1. Connect wallet
2. Go to "Gasless (Fee Sponsored)" tab
3. Enter recipient + amount
4. Click "Send Gasless"
5. Approve in Freighter
6. **You pay ZERO fees!** ✅

### Submitting Feedback
1. Connect wallet
2. Scroll to bottom
3. Click "Fill Feedback Form"
4. Approve transaction in Freighter
5. Fill Google Form
6. Submit ✅

---

## 🔧 Troubleshooting {#troubleshooting}

| Error | Cause | Fix |
|-------|-------|-----|
| "Account not found on testnet" | Wallet not funded | Use Friendbot to get XLM |
| "Freighter is set to Main Net" | Wrong network | Switch Freighter to Testnet |
| "User rejected connection" | User cancelled | Try connecting again |
| "Transaction failed" | Insufficient balance | Check XLM balance |
| Popup not appearing | Incognito mode | Use normal Chrome window |

---

## 🛠️ Local Development

```bash
# Clone repo
git clone https://github.com/YOUR_USERNAME/trustchain-black-belt
cd trustchain-black-belt

# Install dependencies
npm install

# Start dev server
npm run dev

# Build for production
npm run build
```

### Environment
- Node.js 18+
- npm 9+
- Chrome with Freighter extension

---

## 📦 Dependencies

```json
{
  "@stellar/freighter-api": "latest",
  "stellar-sdk": "latest",
  "react": "^18.0.0",
  "vite": "latest"
}
```