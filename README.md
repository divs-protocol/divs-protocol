<div align="center">

<img src="logo.png" alt="DIVS" height="72" />

### DIVS Protocol

Decentralized exchange for tokenized equities on Robinhood Chain.<br />
Instant settlement, markets that never close, and every trading fee paid to $DIVS stakers.

[divsprotocol.com](https://www.divsprotocol.com) · [Documentation](https://www.divsprotocol.com/docs) · [@DIVSProtocol](https://x.com/DIVSProtocol)

</div>

---

Seventeen equities and ETFs trade continuously against on-chain pools. A trade
settles in the block it lands in — no market hours, no settlement period, no
broker between a wallet and a pool.

Fees are not revenue the protocol retains. Every trade is charged on the WETH
side, and the proceeds are distributed to staked $DIVS by weight.

### Protocol

| | |
| --- | --- |
| Chain | Robinhood Chain · 4663 |
| Markets | 17 equities and ETFs |
| Assets | Robinhood Stock Tokens (ERC-8056) |
| Protocol fee | 10 bps, charged in WETH |
| Staking | Single-sided $DIVS and DIVS/WETH LP |
| Lock multiplier | 1× flexible to 4× at 52 weeks |

A position's share of every distribution is proportional to its weight — the
staked amount multiplied by three independent multipliers: pool, size tier and
lock duration.

```
weight = amount × poolMultiplier × tierMultiplier × lockMultiplier
claim  = weight × accWethPerWeight − debt
```

Two properties hold structurally. Fees are transferred in before the accumulator
is raised, so the contracts cannot record an entitlement they do not hold.
Emissions derive their rate from what has been funded, so they cannot be
scheduled beyond the budget backing them.

### Contracts

| Contract | Responsibility |
| --- | --- |
| `DivsStaking` | Holds stake, tracks weight, distributes WETH fees and DIVS emissions |
| `DivsRouter` | Executes trades against the pools and charges the protocol fee |

$DIVS is launched on Pons. Deployed addresses are published at launch.

<div align="center">

[divsprotocol.com](https://www.divsprotocol.com)

</div>
