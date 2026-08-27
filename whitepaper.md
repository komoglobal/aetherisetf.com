# Aetheris (AETF) — Whitepaper

**Version 1.0 | June 2026**
**ASA ID: 3581842047 | Algorand Mainnet**

---

## Abstract

Aetheris (AETF) is a diversified, on-chain token pool built on Algorand. Each AETF token is backed by a basket of five assets — USDC, tokenized Gold, tokenized Silver, HOG, and xALGO — providing holders with diversified exposure across stablecoins, precious metals, and DeFi-native assets in a single token.

AETF is designed to offer downside protection through stable and defensive allocations while maintaining upside exposure to Algorand ecosystem growth. The basket rebalances passively through automated market maker (AMM) arbitrage, requiring no active management or smart contract risk.

> **📌 Strategic Update (June 2026):** AETF has rotated its FOLKS position back into **xALGO** (Folks Finance liquid-staked ALGO), restoring liquid, yield-bearing ALGO exposure as the growth sleeve in place of a single concentrated protocol-token bet. The ~70% defensive / ~30% growth structure is preserved. Allocations begin at these initial targets and **drift dynamically with the market** — live and verifiable on-chain at all times.

---

## 1. Problem

Crypto portfolios are inherently volatile. Most tokens on any given blockchain are highly correlated — when the market drops, everything drops together. Investors seeking diversification must manually manage multiple positions across different asset classes, incurring fees, complexity, and execution risk.

On Algorand specifically:
- Diversified, index-style basket tokens are scarce
- Real-world assets (Gold, Silver) are available via Meld Gold but underutilized
- DeFi and liquid-staking assets like xALGO capture ecosystem growth but sit siloed from safe-haven assets
- No product bridges traditional safe-haven assets with DeFi-native exposure

---

## 2. Solution

AETF solves this by packaging five distinct asset classes into one token:

| Asset | Allocation | Role | Provider |
|-------|-----------|------|----------|
| **USDC** | 35% | Stability floor — maintains value during drawdowns | Circle |
| **Gold (GOLD$)** | 17.5% | Inflation hedge — physical gold, tokenized and auditable | Meld Gold |
| **Silver (SILVER$)** | 17.5% | Precious metals diversification — physical silver, tokenized | Meld Gold |
| **HOG** | 15% | DeFi market maker — grows with Algorand ecosystem liquidity | LiquiHog |
| **xALGO** | 15% | Liquid-staked ALGO — ecosystem growth exposure plus native staking yield | Folks Finance |

**Total defensive allocation (USDC + Gold + Silver): 70%**
**Total growth allocation (HOG + xALGO): 30%**

---

## 3. How It Works

### 3.1 Structure

AETF is an Algorand Standard Asset (ASA) with a fixed supply of **10,000 AETF**. The token is paired with each of the five basket assets in separate liquidity pools on Tinyman DEX:

- AETF / USDC
- AETF / GOLD$
- AETF / SILVER$
- AETF / HOG
- AETF / xALGO

Each pool is seeded with liquidity proportional to the target allocation. The combined value of all pools constitutes the fund's Total Value Locked (TVL).

### 3.2 Passive Rebalancing

AETF does not rely on smart contracts for rebalancing. Instead, it leverages the natural arbitrage mechanism of AMM pools:

1. When one basket asset outperforms, its pool becomes mispriced relative to others
2. Arbitrage traders correct the imbalance by trading between pools
3. This process continuously adjusts the portfolio without any manual intervention
4. The fund effectively "sells high" on outperforming assets and "buys low" on underperforming ones

This creates a self-balancing portfolio with zero smart contract risk and zero management overhead.

### 3.3 Price Discovery

AETF's price is determined by the market across all five pools. The primary pricing reference is the AETF/USDC pool, as USDC provides a stable dollar-denominated benchmark. The Net Asset Value (NAV) is derived from the combined value of all basket positions.

---

## 4. Risk Architecture

### Downside Protection
- **35% USDC floor**: In a severe market crash, more than one-third of the basket holds its dollar value
- **35% precious metals**: Gold and Silver historically perform well during market stress and inflation
- **Combined 70% defensive**: Provides a structural floor that limits drawdown severity

### Upside Capture
- **15% HOG**: Captures Algorand DeFi ecosystem growth — as on-chain activity and liquidity increase, HOG benefits
- **15% xALGO**: Liquid-staked ALGO (Folks Finance) — ALGO ecosystem upside plus native staking yield, fully liquid and redeemable for ALGO

### No Smart Contract Risk
- AETF is a standard ASA — no complex contract logic that can be exploited
- Liquidity pools are managed by Tinyman's audited, battle-tested AMM
- No admin keys for freeze or clawback — the token is fully decentralized

---

## 5. Tokenomics

| Parameter | Value |
|-----------|-------|
| **Token Name** | Aetheris ETF *(immutable on-chain ASA name; brand: Aetheris)* |
| **Ticker** | AETF |
| **ASA ID** | 3581842047 |
| **Total Supply** | 10,000 AETF |
| **Decimals** | 6 |
| **Blockchain** | Algorand |
| **Launch Price** | $2.44 |
| **Freeze Address** | Zeroed (permanently disabled) |
| **Clawback Address** | Zeroed (permanently disabled) |
| **Creator** | T77MFFTY4IUNMMJ47NS4C5RBWZFRE3UVPU7KVHCDPVJGHZVUDAKB7DCNRM |
| **Manager** | 5LEDUTOGIWSMD2MZW4FIYJ2W3KZU262H2K3F7R2BBQNMHUYNDFHEA77UJQ |

### Supply Distribution
The entire supply of 10,000 AETF is deployed across the five liquidity pools, proportional to target allocations. There are no team allocations, vesting schedules, or locked tokens. The fund's value is fully transparent and verifiable on-chain.

---

## 6. Verification & Transparency

### On-Chain Verifiability
Every aspect of AETF is publicly auditable:
- Pool balances are visible in real-time on Algorand explorers
- Token holder distribution is publicly queryable
- All transactions (swaps, arbitrage, pool additions) are recorded on the Algorand blockchain
- NAV can be independently calculated from pool states at any time

### Asset Backing
| Asset | Verification Method |
|-------|-------------------|
| USDC | Circle attestation reports; on-chain balance visible |
| GOLD$ | Meld Gold — 1:1 backed by physical gold in audited vaults |
| SILVER$ | Meld Gold — 1:1 backed by physical silver in audited vaults |
| HOG | On-chain Tinyman pool; LiquiHog project |
| xALGO | Folks Finance liquid-staked ALGO; redeemable for ALGO + staking rewards, verifiable on-chain |

---

## 7. Roadmap

### Phase 1 — Launch ✅
- Token creation and liquidity seeding
- Website launch (aetherisetf.com)
- Tinyman and Vestige integration
- Community building and first communications

### Phase 2 — Growth (Q3 2026)
- Pera Wallet verification
- TVL growth to $100K+
- Expanded holder base (25+ holders)
- Whitepaper publication
- Community engagement (Twitter, Reddit, Algorand ecosystem)

### Phase 3 — Integration (Q4 2026)
- Folks Finance collateral listing proposal
- Cross-protocol composability
- Advanced analytics dashboard with live allocation tracking
- Partnerships with Algorand ecosystem projects

### Phase 4 — Scale (2027)
- TVL target: $1M+
- Potential basket expansion (additional asset classes)
- Governance framework for allocation adjustments
- Institutional onboarding pathways

---

## 8. Competitive Advantage

| Feature | AETF | Typical DeFi Token |
|---------|------|-------------------|
| Diversified backing | ✅ 5 assets | ❌ Single asset |
| Downside protection | ✅ 70% defensive | ❌ None |
| Yield generation | ✅ Pool trading fees accrue to NAV | ❌ None |
| Smart contract risk | ✅ None (pure ASA) | ⚠️ High |
| Rebalancing | ✅ Automatic (AMM arbitrage) | ❌ Manual |
| Transparency | ✅ Fully on-chain | ⚠️ Varies |
| Admin control | ✅ No freeze/clawback | ⚠️ Often enabled |

---

## 9. Risks & Disclaimers

### Risks
- **Market risk**: All basket assets are subject to price volatility
- **Liquidity risk**: Thin pool depth may cause slippage on large trades
- **Oracle/pricing risk**: Asset prices depend on DEX liquidity and market activity
- **Concentration risk**: HOG represents a single DeFi project; its failure would impact 15% of the basket
- **Regulatory risk**: Tokenized assets operate in an evolving regulatory landscape
- **Impermanent loss**: Liquidity pool positions are subject to impermanent loss during volatile periods

### Disclaimers
AETF is not a registered security, investment fund, or financial product. It is a decentralized token on the Algorand blockchain. Nothing in this document constitutes financial advice. Users should conduct their own research and understand the risks before purchasing AETF. Past performance does not guarantee future results.

---

## 10. Links

- **Website**: [aetherisetf.com](https://aetherisetf.com)
- **Tinyman**: [Buy AETF](https://app.tinyman.org/analytics/assets/detail/3581842047)
- **Vestige**: [Track AETF](https://vestige.fi/asset/3581842047)
- **Twitter**: [@AetherisETF](https://x.com/AetherisETF)
- **Algorand Explorer**: [ASA 3581842047](https://explorer.perawallet.app/asset/3581842047/)

---

*© 2026 Aetheris. All rights reserved. AETF is a token pool, not a registered security or investment fund. Nothing herein is investment advice — DYOR.*
