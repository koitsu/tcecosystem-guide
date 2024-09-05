# RUNEPool

## Baseline concepts

There are some "baseline" facts to understand about RUNEPool:

- RUNEPool **is not** the same as staking.
- RUNEPool **does not** provide a "global APY".
- There is no per-position breakdown of how much you've earned/lost over time.  PnL (profits-and-loss) is in real-time.
- Every address participating in RUNEPool will have a different PnL, based on deposit time and pool performance since deposit(s).
- As of August 2024, the "minimum deposit lock-up period" is 30 days, not 90.  Official documentation has yet to be updated.

## ELI5 economic model

A "ELI5" (explain-like-I'm-five) explanation of RUNEPool's earnings "model" is
a common request in the THORSwap Discord.  Here's a simple explanation, which
assumes you are familiar with THORChain LP'ing:

RUNEPool's economic model can most easily be thought of as similar to an
asymmetrical LP deposit of RUNE (i.e. highly dependent upon RUNE:asset price
ratio), but with two (2) distinct differences:

1. RUNEPool exposes you to multiple pools, unlike an LP where you are exposed to a single asset/pool.
1. RUNEPool contributors are only rewarded with swap fees.

**Generally speaking**, when RUNE is performing well (USD value is up), a
position's PnL will decrease (possibly negative).  However, when RUNE is
performing poorly (USD value is down), a position's PnL will increase.

Please note the emphasis on the phrase "generally speaking"; this description
is not a guarantee.  As said above, everyone position's PnL will vary based on
deposit time (much like that of an LP).

Choosing to looking at RUNEPool in terms of "how much RUNE (quantity) I
deposited vs. how much RUNE (quantity) I can withdraw" is not effective.
RUNEPool in essence is more like an actual symmetrical LP behind the scenes,
even though from a user's standpoint they are only depositing a single asset.

## Viewing your position

There are multiple UIs to view your RUNEPool position:

- <https://runepool.replit.app/> -- "My Position" tab + enter your THORChain address
- <https://thorchain.net/thorfi/runepool?tab=rune-pools> -- "Members" tab, in Search area enter last 6 digits of your THORChain address
- <https://thorchain.network/runepool/> -- manually navigate each page to find your address

## Viewing pools and metrics

There are multiple UIs examine pool metrics such as POL weight and LUVI, or
just general RUNEPool information as an aggregate:

- <https://thorchain.net/thorfi/runepool?tab=rune-pools>
- <https://thorchain.network/runepool/>

## References

The official THORSwap and THORChain RUNEPool documentation is quite good.  We
urge people considering contributing to RUNEPool to read (not skim!) these
resources:

- [THORSwap's RUNEPool documentation](https://docs.thorswap.finance/thorswap/thorswap/runepool), especially "Key Features and Considerations"
- [THORChain's RUNEPool documentation](https://docs.thorchain.org/thorchain-finance/runepool)
- [THORChain's RUNEPool Developer documentation](https://dev.thorchain.org/concepts/rune-pool.html)
- [THORChain's Medium blog post about RUNEPool](https://medium.com/thorchain/runepool-on-thorchain-bf8fef5587d5), which contains a FAQ
