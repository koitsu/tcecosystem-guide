# Tracking a swap

Historically, swaps were exclusively done through THORChain.  However, in early
March 2024, [THORSwap introduced Chainflip][2] as a secondary liquidity
protocol for swaps.

How to track a swap depends on which provider was used.

If you're unsure which provider was used for your swap, start with Chainflip.

## Chainflip procedure

As of this writing (2024/03/30), Chainflip-based swaps do not show up in the
THORSwap Transaction History UI (users will be shown a blank page or a page
with a never-ending spinner).  Below is how you can find your swap:

1. Visit the [Chainflip swap tracker]
1. Scroll down the page until you find the **Search by swap ID or destination address** search box
1. Enter your **destination wallet address**.  For example, if you swapped BTC into ETH, you would enter your Ethereum wallet address
1. If your swap was done through Chainflip, you should be shown details of your swap, as well as a progress indicator
1. If your swap is not found, try following the THORChain procedure below

## THORChain procedure

1. Find the Transaction Hash/ID of your THORSwap activity.  There are multiple ways to do this:
   - In THORSwap: click the Transaction History button in the upper right, then choose View Details
   - In [RuneScan]: search for your wallet address (either source or destination address) and look for your swap transaction.  If found, click on it and there should be an icon to copy the Transaction Hash/ID
   - If you still can't find your transaction, then THORChain might be waiting for [inbound confirmations](../thorchain/inbound-confirmations.md)
1. Visit the [9R THORChain Tracker]
1. Enter the Transaction Hash/ID into the **Swap Transaction ID** search box at the top of the page

If your transaction is found, details about it will be shown.  Depending on
which queue your transaction is in, it may or may not have an **ETA**.  Refer
to [THORChain queues](../thorchain/queues.md) for further details.

If you still can't find your transaction on THORChain, you can try the procedure
documented in [Tracking a withdrawal](tracking-a-withdrawal.md).

[1]: https://crypto-university.medium.com/under-the-hood-thorchain-transaction-delays-250d00ed57b7#f667
[2]: https://thorswap.medium.com/cross-chain-made-easy-thorswap-integrates-chainflip-liquidity-network-3894d24db1b8
[9R THORChain Tracker]: https://track.ninerealms.com/
[Chainflip swap tracker]: https://scan.chainflip.io/swaps
[RuneScan]: https://runescan.io/
