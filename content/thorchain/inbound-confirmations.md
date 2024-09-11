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
   - `completed: false` &mdash; the inbound leg is still in progress
   - `completed: true` &mdash; your transaction **is not** stuck in the inbound leg
1. Review the section called `stages`, subsection `inbound_observed`.  Attributes:
   - `completed: true` &mdash; THORChain is aware of the transaction
   - `completed: false` &mdash; THORChain has not yet seen the inbound transaction (may be due to daemon lag)
1. Review the section called `stages`, subsection `inbound_confirmation_counted`.  Attributes:
   - `external_observed_height` &mdash; block height of the source asset chain that needs to be reached before the transaction will complete
   - `external_confirmation_delay_height` &mdash; block height the source asset chain
   - `remaining_confirmation_seconds` &mdash; rough ETA of when the transaction will complete.  This number usually decreases, but *can* increase!
1. Once the entire swap transaction is completed, section `swap_finalised` should have `completed: true`

[1]: https://thorchain-university.medium.com/under-the-hood-thorchain-transaction-delays-250d00ed57b7#f667
[2]: https://thorswap.medium.com/cross-chain-made-easy-thorswap-integrates-chainflip-liquidity-network-3894d24db1b8
