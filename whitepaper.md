# Aetheris (AETF) — Whitepaper

**Version 1.0 | June 2026**
**ASA ID: 3581842047 | Algorand Mainnet**

---

## Abstract

Aetheris (AETF) is a diversified, on-chain token pool built on Algorand. AETF trades through public liquidity markets against USDC, tokenized Gold, tokenized Silver, HOG, and xALGO.

AETF is designed to offer diversified exposure through public liquidity markets. Its AMM pools can allow permissionless arbitrage to align AETF prices across markets, but they do not enforce target weights, guarantee NAV tracking, or buy dips according to an independent valuation rule. The ASA itself is simple; the external AMM pools have their own smart-contract and liquidity risks.

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
| **USDC** | 35% | Dollar-denominated quote asset and defensive launch target | Circle |
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

Each pool was seeded with liquidity based on launch targets. The combined value of the pools can be reported as pool-implied marked TVL, but it is not an independent NAV calculation or a fixed redemption reserve.

### 3.2 Passive Rebalancing

AETF does not contain an allocation-rebalancing contract. Instead, public AMM activity may create cross-pool arbitrage:

1. AETF can trade at different prices across its pools after market movement or a trade
2. Arbitrage traders may trade between pools when the price difference exceeds fees, slippage, and risk
3. That activity can align AETF prices, while reserves and economic weights drift with trading and liquidity flows
4. Arbitrageurs optimize for trade profit; they are not required to enforce target allocations or buy an asset because it is fundamentally cheap

This creates a market-alignment mechanism, not a guaranteed portfolio rebalancer. The system has no fixed-price protocol redemption mechanism.

### 3.3 Price Discovery

AETF's observable price is determined by trading across the five pools. The primary price reference is the AETF/USDC pool because USDC supplies a dollar-denominated quote. A pool-implied marked value can be calculated from the pool states, but it is not an independent NAV or a fixed redemption price.

---

## 4. Risk Architecture

### Defensive launch targets
- **35% USDC target at launch**: Provides a dollar-denominated trading counterparty and a defensive sleeve, not a guaranteed AETF price floor
- **35% precious-metals target at launch**: Gold and Silver add different market exposures; their value and liquidity can vary
- **Combined 70% defensive target at launch**: Actual pool-side weights can drift and do not constitute a guaranteed floor

### Upside Capture
- **15% HOG**: Captures Algorand DeFi ecosystem growth — as on-chain activity and liquidity increase, HOG benefits
- **15% xALGO**: Liquid-staked ALGO exposure through Folks Finance; review the provider's current liquidity and redemption terms

### Risk separation
- AETF is a standard ASA with no custom allocation contract
- Liquidity pools are managed by third-party AMM smart contracts with their own protocol, implementation, and liquidity risks
- The ASA's freeze and clawback fields are publicly observable; users should verify the current chain state rather than rely on a static document

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
| **Freeze / clawback fields** | Verify current zeroed state from the live ASA record |
| **Creator** | T77MFFTY4IUNMMJ47NS4C5RBWZFRE3UVPU7KVHCDPVJGHZVUDAKB7DCNRM |
| **Manager** | 5LEDUTOGIWSMD2MZW4FIYJ2W3KZU262H2K3F7R2BBQNMHUYNDFHEA77UJQ |

### Supply Distribution
The entire supply of 10,000 AETF was initially deployed across five public liquidity pools. Current balances and pool-side weights change with swaps, arbitrage, and liquidity operations, so launch targets are not current allocation guarantees. There are no team allocations or vesting schedules in the stated launch design. Pool balances are publicly verifiable; that does not create fixed-price redemption.

---

## 6. Verification & Transparency

### On-Chain Verifiability
Every aspect of AETF is publicly auditable:
- Pool balances are visible in real-time on Algorand explorers
- Token holder distribution is publicly queryable
- All transactions (swaps, arbitrage, pool additions) are recorded on the Algorand blockchain
- Pool-implied marks can be calculated from pool states; independent NAV depends on external pricing and the absence of a fixed redemption mechanism

### Underlying asset references
| Asset | Verification Method |
|-------|-------------------|
| USDC | Circle reserve disclosures; AETF pool balance visible on-chain |
| GOLD$ | Meld Gold asset; current provider backing and redemption terms should be verified separately |
| SILVER$ | Meld Gold asset; current provider backing and redemption terms should be verified separately |
| HOG | On-chain AETF/HOG liquidity market; LiquiHog project |
| xALGO | Folks Finance liquid-staked ALGO asset; current provider liquidity and redemption terms should be verified separately |

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
| Defensive launch target | ✅ 70% defensive at launch | ❌ None |
| LP fee exposure | ✅ Fees accrue to LP positions | ❌ None |
| Custom allocation contract | ✅ None in AETF ASA | ⚠️ Varies |
| Market alignment | ✅ Permissionless AMM arbitrage may align prices | ❌ Requires a separate policy |
| Transparency | ✅ Fully on-chain | ⚠️ Varies |
| ASA authority visibility | ✅ Publicly verifiable | ⚠️ Varies |

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
