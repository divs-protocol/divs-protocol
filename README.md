<div align="center">

<img src="logo.png" alt="DIVS Protocol" height="120" />

# ◈ DIVS PROTOCOL

**The stock market that never closes. Every fee goes to the people staking it.**

[![Website](https://img.shields.io/badge/Website-divsprotocol.com-10B981?style=for-the-badge)](https://www.divsprotocol.com)
[![Docs](https://img.shields.io/badge/Docs-Read-1F2228?style=for-the-badge)](https://www.divsprotocol.com/docs)
[![X](https://img.shields.io/badge/X-@DIVSProtocol-000000?style=for-the-badge&logo=x&logoColor=white)](https://x.com/DIVSProtocol)
[![Chain](https://img.shields.io/badge/Robinhood_Chain-4663-10B981?style=for-the-badge)](https://www.divsprotocol.com)

</div>

---

## ◈ What is DIVS Protocol?

DIVS Protocol is a decentralized exchange for **tokenized equities** on Robinhood
Chain. Buy Apple at 3am. Sell gold on a Sunday. Seventeen markets, no market
hours, no broker in the middle.

Every trade pays a fee. That fee is not revenue the protocol keeps — it is
routed on-chain to whoever is staking **$DIVS** when the trade lands.

---

## ◈ Markets

| Category | Tickers |
| --- | --- |
| **Equities** | AAPL · NVDA · TSLA · GOOGL · COIN · MSTR · GME · LLY · DJT · AMC · HIMS · CRCL · SPCX |
| **Index ETFs** | SPY · QQQ |
| **Commodity & Treasury** | GLD · SGOV |

Assets are Robinhood Stock Tokens implementing **ERC-8056** — dividends and
splits are applied through a display multiplier rather than by moving tokens.

---

## ◈ How it works

| | |
| --- | --- |
| **Trade** | Swap against on-chain pools. Settles in the block it lands in. |
| **Fee** | 10 bps charged in WETH, on whichever side of the trade WETH sits. |
| **Distribute** | The router forwards it to the vault, split by weight. |
| **Claim** | Stakers withdraw WETH and DIVS. Principal and lock untouched. |

```
weight = amount × poolMultiplier × tierMultiplier × lockMultiplier
claim  = weight × accWethPerWeight − debt
```

---

## ◈ Staking

Stake **$DIVS** single-sided, or the **DIVS/WETH LP**. Weight decides your
share, and the longer the lock, the heavier the weight.

| Lock | Multiplier |
| --- | --- |
| Flexible | 1.00× |
| 13 weeks | 1.75× |
| 26 weeks | 2.50× |
| 39 weeks | 3.25× |
| **52 weeks** | **4.00×** |

Holding $DIVS earns nothing. Only staked positions carry weight.

---

## ◈ Contracts

| Contract | Responsibility |
| --- | --- |
| `DivsStaking` | Holds stake, tracks weight, distributes WETH fees and DIVS emissions |
| `DivsRouter` | Executes trades against the pools and charges the protocol fee |

Two properties hold structurally rather than by convention. Fees are transferred
in **before** the accumulator is raised, so the contracts cannot record an
entitlement they do not hold. Emissions derive their rate from what has been
funded, so they cannot be scheduled beyond the budget backing them. Both are
covered by fuzzed tests.

$DIVS is launched on **Pons**. Deployed addresses are published at launch.

---

## ◈ Built on

- **Robinhood Chain** — chain 4663
- **Robinhood Stock Tokens** — ERC-8056 tokenized equities
- **Uniswap V3** pools for every market
- **Solidity + Hardhat 3** with forge-std fuzzing
- **Next.js + wagmi + viem**

---

<div align="center">

**[Launch the app →](https://www.divsprotocol.com)**

Built by [@DIVSProtocol](https://x.com/DIVSProtocol) · [divsprotocol.com](https://www.divsprotocol.com)

</div>
