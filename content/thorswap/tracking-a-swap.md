# Tracking a swap

Historically, swaps were exclusively done through THORChain.  However,
beginning early 2024, THORSwap began integrating other providers
(a.k.a. "paths" in the THORSwap UI):

- March 2024: [Chainflip][1]
- April 2024: [Maya Protocol][2]

<div class="warning">
As of August 2024, Chainflip and Maya-based swaps do not show up in the
THORSwap Transaction History UI in the upper-right corner.  Instead, users will
be shown a blank page or a page with a never-ending spinner.
</div>

Below are per-provider instructions for how you can find your swap.

If you aren't sure which provider/path you used for your swap, you will
need to try each of them until you find it.  This can be a little confusing,
especially in cases where THORChain RUNE is involved.

## Maya Protocol procedure

1. Visit [Xscanner] or [MayaScan]
1. Enter your source or destination wallet address (source wallet preferred) in the search box
1. If your swap was done through Maya, you should be shown transaction details.  Click on the transaction ID to see a progress meter (if streaming swaps were used), and transaction aggregation features
1. If your swap is not found, try the next protocol/path below

## Chainflip procedure

1. Visit the [Chainflip swap tracker]
1. Scroll down the page until you find the **Search by swap ID or destination address** search box
1. Enter your **destination wallet address**.  For example, if you swapped BTC into ETH, you would enter your Ethereum wallet address
1. If your swap was done through Chainflip, you should be shown details of your swap, as well as a progress indicator
1. If your swap is not found, try the next protocol/path below

## THORChain procedure

1. Find the Transaction Hash/ID of your THORSwap activity.  There are multiple ways to do this:
   - In THORSwap: click the Transaction History button in the upper right, then choose View Details
   - In [RuneScan]: search for your wallet address (either source or destination address) and look for your swap transaction.  If found, click on it and there should be an icon to copy the Transaction Hash/ID
   - If you still can't find your transaction, then THORChain might be waiting for [inbound confirmations](../thorchain/inbound-confirmations.md)
1. Visit the [9R THORChain Tracker]
1. Enter the Transaction Hash/ID into the **Swap Transaction ID** search box at the top of the page
   - If your transaction is found, details about it will be shown
   - Depending on which queue your transaction is in, it may or may not have an **ETA**.  Refer to [THORChain queues](../thorchain/queues.md) for further details
1. If you still can't find your transaction on THORChain, you can try the procedure documented in [Tracking a withdrawal](tracking-a-withdrawal.md)

[1]: https://thorswap.medium.com/cross-chain-made-easy-thorswap-integrates-chainflip-liquidity-network-3894d24db1b8
[2]: https://thorswap.medium.com/seamless-cross-chain-trading-thorswap-welcomes-maya-protocol-ba89b918b879
[9R THORChain Tracker]: https://track.ninerealms.com/
[Chainflip swap tracker]: https://scan.chainflip.io/swaps
[MayaScan]: https://www.mayascan.org/
[RuneScan]: https://runescan.io/
[Xscanner]: https://www.xscanner.org/
