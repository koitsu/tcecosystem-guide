# Delays

A common scenario we get in the THORSwap Discord is a user a particular
transaction (ex. swap, withdrawal, closing a loan, etc.) and seeing the
THORSwap transaction tracker show things in a "pending" state for a very long
time.  In other cases, the THORSwap transaction tracker doesn't show anything,
or might even show a blank page.

As of this writing (2023-11-19) there are bugs/quirks with the THORSwap
transaction tracker's "Details" feature, where parts of the UI don't get
updated properly.  This leads to users panicking, thinking something has
gone wrong, followed by claims that their transaction is "stuck".

Most of the time (~98%) the transaction is not "stuck", but subject to
one or more conditions that can delay a transaction:

## Inbound confirmation counts

When THORChain receives an asset on any supported blockchain (ex. BTC, DOGE,
etc.), it requires a certain number of
[inbound confirmations](https://thorchain-university.medium.com/under-the-hood-thorchain-transaction-delays-250d00ed57b7#f667)
before continuing to process the transaction.

For more details about this subject, refer
[inbound confirmations](inbound-confirmations.md).

## Outbound throttling

THORChain makes use of a
[throttling mechanism for outbound off-chain transactions](https://docs.thorchain.org/frequently-asked-questions#what-is-outbound-throttling)
that can delay transactions **for up to 1 hour**.

For more information on the security mechanism, refer to this
[THORChain University article](https://thorchain-university.medium.com/under-the-hood-thorchain-transaction-delays-250d00ed57b7#9534)
which covers this and additional scenarios.

In mid-January 2024, THORChain implemented
[swapper clout](https://gitlab.com/thorchain/thornode/-/issues/1723)
to help ease some of the burden of said this security mechanism.
You can check your THORChain clout score by using the
[rune.tools Swapper Clout](https://rune.tools/clout)
application.

## Streaming swaps

THORChain offers what are called
[streaming swaps](https://medium.com/thorchain/introducing-streaming-swaps-eff37f6150f3)
which help relieve slippage by breaking down a swap transaction into
smaller "sub-swaps".  Refer to the linked article for details.

Some front-ends, like THORSwap, employ use of streaming swaps by default.
On THORSwap, the streaming parameters can be adjusted &mdash; and even
disabled (for instant swaps) if the asset value is large enough.

Streaming swap duration can vary greatly, and in cases of limited liquidity
in a pool, may be longer than expected (ex. 24 hours or longer).

## Wallet-related delays

Every wallet requires a number of of blockchain confirmation counts before
funds are considered "in your wallet".  The number varies per wallet; there is
no standard.

Blockchain validators (miners) can sometimes take a while to verify
transactions.  For example, on the BTC blockchain, there have been times where
validators have taken upwards of 60 minutes to validate and provide enough
confirmations for funds to appear in a user's wallet.  We have also seen times
of over 2 hours on the BCH blockchain.  This is not the fault of THORChain.

If you've verified using a blockchain explorer that funds have arrived at
your address, but your wallet still isn't seeing them, contact the support
team associated with your wallet.
