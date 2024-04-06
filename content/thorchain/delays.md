# Delays

A common scenario we get in the THORSwap Discord is a user a particular
transaction (ex. swap, withdrawal, closing a loan, etc.) and seeing the
THORSwap transaction tracker show things in a "pending" state for a very long
time.  In other cases, the THORSwap transaction tracker doesn't show anything,
or might even show a blank page.

As of this writing (2023-11-19) there are bugs/quirks with the THORSwap
transaction tracker's "Details" feature, where parts of the UI don't get
updated properly (if at all).  This leads to users panicking, thinking
something has gone wrong, followed by claims that "their transaction is stuck".

Most of the time (~98%) the transaction is not "stuck", but rather subject to
THORChain's [outbound throttling][1] security mechanism.

**This security mechanism can delay the "outbound" portion of the transaction
up to 1 hour.**

For more information on the security mechanism, refer to
[this THORChain University article][2] which covers some other scenarios.

In mid-January 2024, THORChain implemented [swapper clout][3] to help ease some
of the burdeons of said mechanism.

Additionally, blockchain validators (miners) can sometimes take a while to
verify transactions.  For example, on the BTC blockchain, there have been times
where validators have taken upwards of 45 minutes to validate and provide
enough confirmations for funds to appear in a user's wallet.  This is not the
fault of THORChain.

[1]: https://docs.thorchain.org/frequently-asked-questions#what-is-outbound-throttling
[2]: https://crypto-university.medium.com/under-the-hood-thorchain-transaction-delays-250d00ed57b7#9534
[3]: https://gitlab.com/thorchain/thornode/-/issues/1723
