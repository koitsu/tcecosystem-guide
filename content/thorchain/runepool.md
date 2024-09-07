# RUNEPool

## Baseline concepts

There are some "baseline" facts to understand about RUNEPool:

- RUNEPool **is not** the same as staking.
- RUNEPool **does not** provide a "global APY".
- There is no per-position breakdown of how much you've earned/lost over time; PnL (profits-and-loss) values are in real-time.
- Every address participating in RUNEPool will have a different PnL, based on deposit time and pool performance since deposit(s).
- As of August 2024, the "minimum deposit lock-up period" is 30 days, not 90.  Official documentation has yet to be updated.

## ELI5 economic model

A "ELI5" (explain-like-I'm-five) explanation of RUNEPool's earnings "model" is
a common request in the THORSwap Discord.  Here's a simple explanation, which
assumes you are familiar with THORChain LPs:

RUNEPool's economic model can be thought of like an asymmetrical LP deposit of
RUNE (i.e. highly dependent upon RUNE:asset price ratio), but with one distinct
difference: RUNEPool exposes you to multiple pools, unlike a standard LP where
you are exposed to a single asset/pool.

In reality, RUNEPool is more like a user holding multiple dual-sided LPs,
with one for each pool that RUNEPool consists of.  This is even covered in
[THORChain's Medium blog post](https://medium.com/thorchain/runepool-on-thorchain-bf8fef5587d5).

Regarding yield and performance: **generally speaking**, when RUNE is
performing well (USD value is up), a position's PnL will decrease (possibly
negative).  However, when RUNE is performing poorly (USD value is down), a
position's PnL will increase.

Please note the emphasis on the phrase "generally speaking"; this description
is not a guarantee.  As said above, every position's PnL will vary based on
deposit time (just like that of an LP).

## Viewing your position

There are multiple UIs to view your RUNEPool position:

- <https://runepool.replit.app/> &mdash; "My Position" sub-tab + enter your THORChain address
  - You can also use <https://runepool.replit.app/?address=YOURADDRESS> as a bookmark.  Replace `YOURADDRESS` with your THORChain address
- <https://thorchain.net/thorfi/runepool> &mdash; "Members" sub-tab, in Search area enter last 6 digits of your THORChain address
- <https://thorchain.network/runepool/> &mdash; manually navigate each page to find your address

## Viewing pools and metrics

There are multiple UIs examine pool metrics such as POL weight and LUVI, or
just general RUNEPool information as an aggregate:

- <https://thorchain.net/thorfi/runepool>
- <https://thorchain.network/runepool/>

## References

The official THORSwap and THORChain RUNEPool documentation is quite good.  We
urge people considering contributing to RUNEPool to read (not skim!) these
resources:

- [THORSwap's RUNEPool documentation](https://docs.thorswap.finance/thorswap/thorswap/runepool), especially "Key Features and Considerations"
- [THORChain's RUNEPool documentation](https://docs.thorchain.org/thorchain-finance/runepool)
- [THORChain's RUNEPool Developer documentation](https://dev.thorchain.org/concepts/rune-pool.html)
