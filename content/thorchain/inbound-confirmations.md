# Inbound confirmations

THORChain requires a certain number of [inbound confirmations][1] when
receiving an asset on the THORChain network.  This is sometimes called the
"inbound leg".

Reviewing inbound confirmations is somewhat complicated and technical:

1. Visit `https://thornode.ninerealms.com/thorchain/tx/status/YOUR_TRANSACTION_HASH` in your browser
   - Replace `YOUR_TRANSACTION_HASH` with the Transaction Hash/ID from the earlier procedure
   - If you see the message `{"error":"rpc error: code = Unknown desc = internal"}` then the Transaction Hash/ID is wrong
   - You can reload this page periodically to see the status of the inbound leg
1. If the transaction is found, you should be shown a JSON blob (a bunch of technical data in text)
1. Review the section called `inbound_finalised`.  Attributes:
   - If `completed` is **false**, then the inbound leg is still in progress
   - If `completed` is **true**, then your transaction **is not** stuck in the inbound leg
1. Review the section called `stages`, subsection `inbound_observed`.  Attributes:
   - `completed` should be **true**.  If it isn't, then THORChain has yet to see the transaction on the blockchain; this may be due to blockchain lag
1. Review the section called `stages`, subsection `inbound_confirmation_counted`.  Attributes:
   - `external_observed_height` is the block height of the source asset chain that needs to be reached before the transaction will complete
   - `external_confirmation_delay_height` is the block height the source asset chain
   - `remaining_confirmation_seconds` represents a rough ETA of when the transaction will complete.  This number usually decreases, but CAN increase!
1. Once the entire swap transaction is completed, section `swap_finalised` should have `completed` as **true**

[1]: https://thorchain-university.medium.com/under-the-hood-thorchain-transaction-delays-250d00ed57b7#f667
[2]: https://thorswap.medium.com/cross-chain-made-easy-thorswap-integrates-chainflip-liquidity-network-3894d24db1b8
