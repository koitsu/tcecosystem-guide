# Troubleshooting

THORChain offers several different HTTP APIs for seeing various states of
addresses, transactions, balances, actions, and so on.  Portions of the
Cosmos (Tendermint) accounting layer are also accessible.

<div class="warning">
The below documentation uses Liquify infrastructure endpoints, which are
subject to rate-limiting, and have other stipulations.
<p></p>
It is recommended (and sometimes required) that requests sent to these
interfaces include an <code>X-Client-ID</code> header that identifies
who you are.  If you have joined the THORChain Dev Discord, please set
this header to a value of <code>discord:YOURUSERNAME/YOURIDNUMBER</code>
so that the requests can be identified.
<p></p>
Users who are wishing to consume large amounts of data
<strong>SHOULD NOT</strong> use these endpoints, and should instead run
their own Midgard and/or THORNode infrastructure which can be queried
(often via localhost).
</div>

## Midgard

- Swagger API docs: <https://gateway.liquify.com/chain/thorchain_midgard/v2/doc>

## THORNode

### THORNode layer

- Swagger API docs: <https://gateway.liquify.com/chain/thorchain_api/thorchain/doc>

### Cosmos (Tendermint) layer

- Accounts: <https://gateway.liquify.com/chain/thorchain_api/cosmos/auth/v1beta1/accounts>
- Account details: <https://gateway.liquify.com/chain/thorchain_api/cosmos/auth/v1beta1/accounts/ADDRESS>
- Supply: <https://gateway.liquify.com/chain/thorchain_api/cosmos/bank/v1beta1/supply>
- Transaction: <https://gateway.liquify.com/chain/thorchain_api/cosmos/tx/v1beta1/txs/TXNID>
  - Note: transaction ID **should not** include any `0x` prefix
- Wallet balance: <https://gateway.liquify.com/chain/thorchain_api/cosmos/bank/v1beta1/balances/ADDRESS>
