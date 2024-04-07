# Inbound confirmations

THORChain requires a certain number of [inbound confirmations][1] when
receiving an asset on the THORChain network.  This is sometimes called the
"inbound leg".

Reviewing inbound confirmations is somewhat complicated and technical:

1. Visit `https://thornode.ninerealms.com/thorchain/tx/status/YOUR_TRANSACTION_HASH` in your browser
   - Replace `YOUR_TRANSACTION_HASH` with the Transaction Hash/ID from the earlier procedure
   - You may need to ensure the Transaction Hash/ID is in **all lowercase**
   - If you see the message `{"error":"rpc error: code = Unknown desc = internal"}` then the Transaction Hash/ID is wrong
1. If the transaction is found, you should be shown a JSON blob (a bunch of technical data in text)
1. Look through the structured data for a section called `stages`
   - There are sub-sections called `inbound_observed` and `inbound_confirmation_counted` which are related to inbound confirmations
1. Review the section called `inbound_finalised`
   - If the `completed` field is **false**, then the inbound leg is still in progress
   - If the `completed` field is **true**, then your transaction **is not** stuck in the inbound leg

[1]: https://crypto-university.medium.com/under-the-hood-thorchain-transaction-delays-250d00ed57b7#f667
[2]: https://thorswap.medium.com/cross-chain-made-easy-thorswap-integrates-chainflip-liquidity-network-3894d24db1b8
[9R THORChain Tracker]: https://track.ninerealms.com/
[Chainflip swap tracker]: https://scan.chainflip.io/swaps
[RuneScan]: https://runescan.io/
