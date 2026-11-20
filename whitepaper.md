# Aetheris (AETF) Whitepaper

**Version 1.1 | November 2026**
**ASA ID: 3581842047 | Algorand Mainnet**

---

## Abstract

Aetheris (AETF) is a diversified, on-chain token pool built on Algorand. AETF trades through public liquidity markets against USDC, Folks V2 USDC (fUSDC), and HOG on Tinyman, Pact, and LiquiHog STAMM.

AETF is designed to offer diversified exposure through public liquidity markets. Its AMM pools can allow permissionless arbitrage to align AETF prices across markets, but they do not enforce target weights, guarantee NAV tracking, or buy dips according to an independent valuation rule. The ASA itself is simple. The external AMM pools have their own smart-contract and liquidity risks.

> **Market update (November 2026):** AETF trades against and makes markets in USDC, fUSDC, and HOG pools on Tinyman, Pact, and LiquiHog. fUSDC is Folks Finance interest-bearing USDC, so part of the pool liquidity earns lending yield. No APY or yield is guaranteed.

---

## 1. Problem

Crypto portfolios are inherently volatile. Most tokens on any given blockchain are highly correlated: when the market drops, everything drops together. Investors seeking diversification must manually manage multiple positions across different asset classes, incurring fees, complexity, and execution risk.

On Algorand specifically:
- Diversified, index-style basket tokens are scarce
- Dollar, lending-market, and DeFi-native assets often sit in separate venues
- Combining those exposures in one publicly tradable token still requires the holder to accept AMM, protocol, and liquidity risk

---

## 2. Solution

AETF packages public trading markets against three assets into one token:

| Asset | Role | Provider |
|-------|------|----------|
| **USDC** | Dollar-denominated quote asset and primary price anchor | Circle |
| **fUSDC** | Folks Finance interest-bearing USDC. Part of pool liquidity may earn variable lending yield from Folks. No APY or yield is promised. | Folks Finance |
| **HOG** | DeFi market-maker token that trades in public AETF/HOG pools | LiquiHog |

Live pool-implied composition is displayed on [aetherisetf.com](https://aetherisetf.com). Actual pool-side weights can drift as markets trade and liquidity changes.

---

## 3. How It Works

### 3.1 Structure

AETF is an Algorand Standard Asset (ASA) with a fixed supply of **10,000 AETF**. The token is paired with USDC, fUSDC, and HOG in separate liquidity pools on Tinyman, Pact, and LiquiHog STAMM:

- AETF / USDC (Tinyman, Pact, LiquiHog STAMM)
- AETF / fUSDC (Tinyman, Pact, LiquiHog STAMM)
- AETF / HOG (Tinyman, Pact, LiquiHog STAMM)

The combined value of the pools can be reported as pool-implied marked TVL, but it is not an independent NAV calculation or a fixed redemption reserve. Current weights drift with market trades, liquidity operations, and market-making.

### 3.2 Market alignment

AETF does not contain an allocation-rebalancing contract. Instead, public AMM activity may create cross-pool arbitrage:

1. AETF can trade at different prices across its pools after market movement or a trade
2. Arbitrage traders may trade between pools when the price difference exceeds fees, slippage, and risk
3. That activity can align AETF prices, while reserves and economic weights drift with trading and liquidity flows
4. Arbitrageurs optimize for trade profit. They are not required to enforce target allocations or buy an asset because it is fundamentally cheap

This describes a market-alignment mechanism, not a promised strategy or a guaranteed portfolio rebalancer. The system has no fixed-price protocol redemption mechanism.

### 3.3 Price Discovery

AETF's observable price is determined by trading across the public pools. The primary price reference is the AETF/USDC pools, because USDC supplies a dollar-denominated quote. A pool-implied marked value can be calculated from the pool states, but it is not an independent NAV or a fixed redemption price.

---

## 4. Risk Architecture

Allocations and pool-side weights change through market trades, liquidity flows, and market-making. None of the points below is a guaranteed floor or a current NAV statement.

### Dollar and lending-market counterparties
- **USDC pools**: Provide a dollar-denominated trading counterparty and the primary price mark. They are not a guaranteed AETF price floor.
- **fUSDC pools**: fUSDC is Folks Finance interest-bearing USDC, so part of this liquidity earns lending yield. Yield can vary, is not guaranteed, and is not stated here as an APY. These pools also carry Folks Finance protocol risk.

### DeFi exposure
- **HOG pools**: Provide public AETF/HOG markets. HOG is a single DeFi project, so its failure would affect this sleeve of the basket.

### Risk separation
- AETF is a standard ASA with no custom allocation contract
- Liquidity pools are managed by third-party AMM smart contracts (Tinyman, Pact, and LiquiHog STAMM) with their own protocol, implementation, and liquidity risks
- The ASA's freeze and clawback fields are publicly observable. Users should verify the current chain state rather than rely on a static document

---

## 5. Tokenomics

| Parameter | Value |
|-----------|-------|
| **Token Name** | Aetheris ETF *(immutable on-chain ASA name, brand: Aetheris)* |
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
The entire supply of 10,000 AETF was initially deployed across public liquidity pools. Current balances and pool-side weights change with swaps, arbitrage, liquidity operations, and market-making, so earlier launch targets are not current allocation guarantees. AETF makes markets in USDC, fUSDC, and HOG. There are no team allocations or vesting schedules in the stated launch design. Pool balances are publicly verifiable. That does not create fixed-price redemption.

---

## 6. Verification & Transparency

### On-Chain Verifiability
Every aspect of AETF is publicly auditable:
- Pool balances are visible in real-time on Algorand explorers
- Token holder distribution is publicly queryable
- All transactions (swaps, arbitrage, pool additions) are recorded on the Algorand blockchain
- Pool-implied marks can be calculated from pool states. Independent NAV depends on external pricing and the absence of a fixed redemption mechanism

### Underlying asset references
| Asset | Verification Method |
|-------|-------------------|
| USDC | Circle reserve disclosures, and the AETF pool balance is visible on-chain |
| fUSDC | Folks Finance interest-bearing USDC (ASA 971384592). Current provider terms should be verified separately. Lending yield is not guaranteed. |
| HOG | On-chain AETF/HOG liquidity markets, and the LiquiHog project |

---

## 7. Roadmap

### Phase 1: Launch ✅
- Token creation and liquidity seeding
- Website launch (aetherisetf.com)
- Tinyman, Pact and LiquiHog integration
- Community building and first communications

### Phase 2: Growth (Q3 2026)
- Pera Wallet verification
- TVL growth to $100K+
- Expanded holder base (25+ holders)
- Whitepaper publication
- Community engagement (Twitter, Reddit, Algorand ecosystem)

### Phase 3: Integration (Q4 2026)
- Folks Finance collateral listing proposal
- Cross-protocol composability
- Advanced analytics dashboard with live allocation tracking
- Partnerships with Algorand ecosystem projects

### Phase 4: Scale (2027)
- TVL target: $1M+
- Potential basket expansion (additional asset classes)
- Governance framework for allocation adjustments
- Institutional onboarding pathways

---

## 8. Competitive Advantage

| Feature | AETF | Typical DeFi Token |
|---------|------|-------------------|
| Diversified markets | ✅ USDC, fUSDC, and HOG across nine public pools | ❌ Single asset |
| Active venues | ✅ Tinyman, Pact, and LiquiHog STAMM | ⚠️ Varies |
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
- **Concentration risk**: HOG represents a single DeFi project, and its failure would affect the HOG sleeve of the basket
- **Protocol risk**: fUSDC carries Folks Finance protocol and lending-market risk, and yield is not guaranteed
- **Regulatory risk**: Tokenized assets operate in an evolving regulatory landscape
- **Impermanent loss**: Liquidity pool positions are subject to impermanent loss during volatile periods

### Disclaimers
AETF is not a registered security, investment fund, or financial product. It is a decentralized token on the Algorand blockchain. Nothing in this document constitutes financial advice. Users should conduct their own research and understand the risks before purchasing AETF. Past performance does not guarantee future results.

---

## 10. Links

- **Website**: [aetherisetf.com](https://aetherisetf.com)
- **Tinyman**: [Buy AETF](https://app.tinyman.org/analytics/assets/detail/3581842047)
- **Pact**: [Buy AETF](https://app.pact.fi/analytics/tokens/3581842047)
- **LiquiHog**: [Buy AETF](https://app.liquihog.com/asset/3581842047)
- **Twitter**: [@AetherisETF](https://x.com/AetherisETF)
- **Algorand Explorer**: [ASA 3581842047](https://explorer.perawallet.app/asset/3581842047/)

---

*© 2026 Aetheris. All rights reserved. AETF is a token pool, not a registered security or investment fund. Nothing herein is investment advice. DYOR.*
