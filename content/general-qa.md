# General Q&A

This section contains general Q&A items, primarily induced by repeated
questions asked on the THORSwap Discord.

## How can I track my LP earnings?

- THORYield mobile app for Android (via Google Play Store) (recommended)
- THORYield mobile app for iOS (via Apple Store) (recommended)
- [THORYield app] (web-based)

## I just opened my LP and it's not showing up in THORYield!

As of mid-November 2023, THORYield is a bit slow to notice new LPs.
**Please give things 24-48 hours to settle.**

In the meantime, you can use the [THORChain Network Explorer] to verify your LP
exists.  Simply visit the site and search for your wallet address (for
symmetrical LPs, please use your THORChain address), then visit the LP tab
and wait a few moments for the details to appear.

Alternately, you can use the [Midgard API] directly if you are technically
inclined.  Use the `/v2/member` endpoint.

## If I deposit an asset asymmetrically in an LP, and I expect the opposite asset to gain in value, will I end up with more of the asset I deposited?

Yes.  This is because when adding the asset you deposited, 50% of it was
automatically swapped into the opposing asset.

Example: you entered into an asymmetric LP depositing BTC (thus putting you in
the BTC.RUNE pool).  This causes half of your deposit to be swapped for RUNE
(at the time the LP was opened).  If RUNE pumps, your LP position will
auto-rebalance 50:50, thus you will have more ETH than originally deposited.

For further information on asymmetric LPing and 50:50 balancing, as well as
impermanent loss, please see the following THORChain Community blog posts:

- [THORChain Community - Calculating Redeemable Value of a Liquidity Pool][1]
- [THORChain Community - Distinguishing Between Price Exposure and Impermanent Loss in Asymmetrical LP’ing][2]
- [THORChain Community - THORChain LP — FAQ][3]

## Is the APR percentage on THORSwap/THORYield real (e.g. 500%)?

Yes.  However, it's important you understand that LPs are not like bank
accounts with static or guaranteed interest rates; the APR varies constantly.
The numbers shown on THORSwap and THORYield refer to the gains over the past
period (usually 7 days on THORSwap, and 180 days on THORYield).  The APRs are
LUVI-based.

Quoting SamYap of THORChain Community:

> * LP APRs are backward calculated, not guarantee of any future returns
> * LP APRs depends significantly on RUNE price movements & calculation time periods
>
> See <https://thorchain-community.medium.com/under-the-hood-liquidity-pool-apr-3e5e662e6675> and <https://thorchain-community.medium.com/under-the-hood-apr-of-a-fluctuating-position-948f49dace8a>
>
> Note: The synth leverage on @THORChain's LP goes both ways.
>
> * When RUNE:Asset price ratio drops, you may see -100% APR (or lower).
> * When RUNE:Asset price ratio increase, LPs can get a similarly "exponential" positive yield as well.
>
> Doing LP is like betting on RUNE price performance.

## Is the negative APR I see correct?  How can that be?

Yes.  Quoting paperX of THORSwap:

> Any "negative % APR" stems from THORChain's "synths effect" and LUVI based calculations. You can read all about the details here (See part 3): <https://medium.com/thorchain/introduction-to-luvi-and-midgard-apr-calculation-update-cf15e743276d>

## What are the risks associated with LPs?

- [THORChain Community - Impermanent Loss][6]
  - Please note Impermanent Loss Protection was [officially sunset][7] in December 2023
- [THORChain Community - Synth Leveraging 101][8]
- [THORChain Community - Synth Leveraging 201][9]

## Where can I see APR performance over time?

Try the [THORChain Network Explorer].  Navigate to Insights &rarr; APR.  There
you can see 30, 60, 90, and 180-day histories.

[1]: https://thorchain-community.medium.com/calculating-redeemable-value-of-a-liquidity-pool-e89a452afeec
[2]: https://thorchain-community.medium.com/distinguishing-between-price-exposure-and-impermanent-loss-in-asymmetrical-lping-f3fcd0e84887
[3]: https://thorchain-community.medium.com/thorchain-lp-faq-7f60950aa277
[4]: https://docs.thorchain.org/thorchain-finance/savings
[6]: https://thorchain-community.medium.com/impermanent-loss-and-impermanent-loss-protection-a4a0f78d1701
[7]: https://thorchain-community.medium.com/lpu-thorchain-updates-nov-2023-17af629c7763
[8]: https://thorchain-community.medium.com/under-the-hood-liquidity-pool-apr-3e5e662e6675
[9]: https://thorchain-community.medium.com/under-the-hood-liquidity-pool-apr-synth-leverage-201-c412b2cb8cb5
[Midgard API]: https://midgard.ninerealms.com/v2/doc
[THORChain Network Explorer]: https://thorchain.net/dashboard
[THORYield app]: https://app.thoryield.com/dashboard
