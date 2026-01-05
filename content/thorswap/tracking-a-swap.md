# Tracking a swap

Historically, swaps were exclusively done through THORChain.  However, beginning early 2024, THORSwap
began integrating other providers (a.k.a. "paths" in the THORSwap UI):

- March 2024: [Chainflip][1]
- April 2024: [Maya Protocol][2]
- October 2025: [NEAR Intents][3]
- December 2025: [Harbor][4]

<div class="warning">
As of August 2024, Chainflip and Maya-based swaps do not show up in the THORSwap Transaction History UI
in the upper-right corner.  Instead, users will be shown a blank page or a page with a never-ending spinner.
</div>

<div class="warning">
As of November 2025, NEAR Intents transactions will not show valid transaction hashes in the THORSwap
Transaction History UI in the upper-right corner.  Instead, users will be shown transaction IDs that
contain all zeros.  This is a known issue devs are working on fixing.
</div>

Below are per-provider instructions for how you can find your swap.

If you aren't sure which provider/path you used for your swap, you will need to try each of them until you
find it.  This can be a little confusing, especially in cases where THORChain RUNE is involved.

## Harbor procedure

1. In THORSwap, click the Transaction History button in the upper right, then choose View Details on your transaction
1. Copy the **Transaction ID** at the bottom of the details window
1. Visit the [Harbor explorer]
1. In the search box, paste the transaction ID obtained in the previous step
   - If the transaction ID starts with `0x`, remove those characters (e.g. `0x1234` becomes `1234`)
1. If you swap was done through Harbor, you should be shown details of your swap
1. If your swap is not found, try the next protocol/path below

## NEAR Intents procedure

1. In THORSwap, click the Transaction History button in the upper right, then choose View Details on your transaction
1. You will be shown multiple "stages" of the swap.  Click View Tx on the **furthest left "Transfer" entry**
   - For example, if you did a BTC to USDC (Solana) swap, the first stage would be a Transfer of BTC
1. In the block explorer you're taken to, copy the address where your funds were **sent to**
   - This destination address is handled by NEAR Intents
   - For UTXO chains, this would be the Output address, not the Change address
1. Enter `https://explorer.near-intents.org/transactions/` in your browser, appending the destination address from the previous step to the URL
   - For example, if the destination address in the previous step was `abc123456`, you would visit `https://explorer.near-intents.org/transactions/abc123456`
1. If your swap was done through NEAR Intents, you should be shown details of your swap
1. If your swap is not found, try the next protocol/path below

## Maya Protocol procedure

1. Visit [Xscanner] or [MayaScan]
1. Enter your source or destination wallet address (source wallet preferred) in the search box
1. If your swap was done through Maya, you should be shown transaction details.  Click on the transaction ID to see a progress meter (if streaming swaps were used), and transaction aggregation features
1. If your swap is not found, try the next protocol/path below

## Chainflip procedure

1. Visit the [Chainflip explorer]
1. In the search box, enter your **destination wallet address** and wait to see if any swaps are shown
   - For example, if you swapped BTC into ETH, you would enter your Ethereum wallet address
1. If your swap was done through Chainflip, you should be shown a list of swaps.  The most recent should be at the top.  Click the swap to see details, including a progress indicator
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
[3]: https://thorswap.medium.com/introducing-near-intents-%EF%B8%8F-thorswaps-new-revolutionary-cross-chain-provider-2a18bbf31dfe
[4]: https://x.com/THORSwap/status/1998958126427746749
[9R THORChain Tracker]: https://track.ninerealms.com/
[Chainflip explorer]: https://scan.chainflip.io/
[Harbor explorer]: https://explorer.harbor.xyz/
[MayaScan]: https://www.mayascan.org/
[RuneScan]: https://runescan.io/
[Xscanner]: https://www.xscanner.org/
