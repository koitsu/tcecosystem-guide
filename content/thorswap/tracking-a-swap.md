# Tracking a swap

Historically, swaps were exclusively done through THORChain.  However, in early
March 2024, [THORSwap introduced Chainflip][2] as a secondary liquidity
protocol for swaps.

How to track a swap depends on which provider was used.

As of this writing (2024/03/30), Chainflip-based swaps do not show up in the
THORSwap Transaction History UI (users will be shown a blank page, or a page
with a never-ending spinner).

If you're unsure which provider was used for your swap, start with Chainflip.

## Chainflip procedure

1. Visit the [Chainflip swap tracker]
1. Scroll down the page until you find the **Search by swap ID or destination address** search box
1. Enter your **destination wallet address**.  For example, if you swapped BTC into ETH, you would enter your Ethereum wallet address
1. If your swap was done through Chainflip, you should be show details of your swap, as well as a progress indicator
1. If your swap is not found, try following the THORChain procedure below

## THORChain procedure

1. Find the Transaction Hash/ID of your THORSwap activity: click the Transaction History button in the upper right of THORSwap and then choose View Details
   - If you still can't find your Transaction Hash/ID: try using [RuneScan] to search for your wallet address (either source or destination wallet) and find your transaction.  Once you find it, click on it and there should be an icon to copy the Transaction Hash/ID
1. Visit the [9R THORChain Tracker]
1. Enter the Transaction Hash/ID into the **Swap Transaction ID** search box at the top of the page
1. If your transaction is found, details about it will be shown, including an ETA

If you still can't find your transaction, then it's possible the transaction is still waiting for
[inbound confirmations][1] on the THORChain network.  We sometimes call this the "inbound leg".

Checking inbound confirmations is a little complicated and technical.  Here's how to do it:

1. Visit `https://thornode.ninerealms.com/thorchain/tx/status/YOUR_TRANSACTION_HASH` in your browser
   - Replace `YOUR_TRANSACTION_HASH` with the Transaction Hash/ID from the earlier procedure
1. If successful, you should be shown a JSON blob (a bunch of technical data in text)
   - If you see the message `{"error":"rpc error: code = Unknown desc = internal"}` then the Transaction Hash/ID is wrong
   - You may need to ensure the Transaction Hash/ID is in all lowercase
1. Look through the structured data for a small section called `stages`
   - There are sub-sections called `inbound_observed` and `inbound_confirmation_counted` which are related to inbound confirmations
1. Examine the `inbound_finalised` section
   - If the `completed` field is **false**, then the inbound leg is still in progress
   - If the `completed` field is **true**, then your transaction **is not** stuck in the inbound leg

If you're still having problems, ask for help in the THORSwap Discord channel
`#thorswap-general` where THORSwap community moderators can help.  If you
prefer official THORSwap staff support which is one-on-one and private, open a
ticket in the `#support-desk` channel and be patient.

[1]: https://crypto-university.medium.com/under-the-hood-thorchain-transaction-delays-250d00ed57b7#f667
[2]: https://thorswap.medium.com/cross-chain-made-easy-thorswap-integrates-chainflip-liquidity-network-3894d24db1b8
[9R THORChain Tracker]: https://track.ninerealms.com/
[Chainflip swap tracker]: https://scan.chainflip.io/swaps
[RuneScan]: https://runescan.io/
