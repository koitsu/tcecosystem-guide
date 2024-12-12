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

Regarding yield and performance: every position's PnL will vary based on
deposit time, just like that of a standard THORChain LP.

## Viewing your position

There are multiple UIs to view your RUNEPool position:

- <https://rune.tools/pool> &mdash; "My Position" sub-tab + enter your THORChain address
  - You can also use <https://rune.tools/pool?address=YOURADDRESS> as a bookmark.  Replace `YOURADDRESS` with your THORChain address
- <https://thorchain.net/thorfi/runepool> &mdash; "Members" sub-tab, in Search area enter last 6 digits of your THORChain address
- <https://thorchain.network/runepool/> &mdash; manually navigate each page to find your address

## Viewing pools and metrics

There are multiple UIs examine pool metrics such as POL weight and LUVI, or
just general RUNEPool information as an aggregate:

- <https://rune.tools/pool>
- <https://thorchain.net/thorfi/runepool>
- <https://thorchain.network/runepool/>

## Determining withdrawal quantity

When withdrawing from RUNEPool, the only transaction seen on THORChain's
blockchain is the withdrawal request itself.  This comes in the form of a memo
instructs THORChain to initiate the withdrawal, and (effectively) the
percentage to withdraw (ex: `POOL-:10000` means withdraw 100% from RUNEPool).

The actual quantity of RUNE returned to the user's wallet is not found on the
blockchain (i.e. you will not find it on RuneScan), which poses a problem when
using third-party services for tax or financial ledger purposes (ex. Koinly);
THORChain simply adds to the user's wallet the relevant amount of RUNE.

So how do we determine what actual RUNE quantity was returned to a wallet?

To do this, we need the original withdrawal request transaction ID, as well as a
"special" URL that can see within the internal THORChain accounting/ledger
layer called Cosmos.

The URL is `https://thornode-v2.ninerealms.com/cosmos/tx/v1beta1/txs/YOURTRANSACTIONID`

This will return a JSON blob with various information.  The amount is stored
deep within nested sections:

- `tx_response` &rarr; `logs` &rarr; `events` &rarr; `rune_pool_withdraw`

Once you find `rune_pool_withdraw`, look for a key called `rune_amount` and its
associated `value`.  This number will be in 1e8 format (i.e. 10^8), so you will
need to do some basic math to turn it into actual RUNE quantity.  Two examples:

- 77266305 &rarr; `77266305 / 10^8` &rarr; 0.77266305 RUNE
- 7551111378 &rarr; `7551111378 / 10^8` &rarr; 75.51111378 RUNE

## References

The official THORSwap and THORChain RUNEPool documentation is quite good.  We
urge people considering contributing to RUNEPool to read (not skim!) these
resources:

- [THORSwap's RUNEPool documentation](https://docs.thorswap.finance/thorswap/thorswap/runepool), especially "Key Features and Considerations"
- [THORChain's RUNEPool documentation](https://docs.thorchain.org/thorchain-finance/runepool)
- [THORChain's RUNEPool Developer documentation](https://dev.thorchain.org/concepts/rune-pool.html)
