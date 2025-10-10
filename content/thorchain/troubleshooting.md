# Troubleshooting

THORChain offers several different HTTP APIs for seeing various states of
addresses, transactions, balances, actions, and so on.  Portions of the
Cosmos (Tendermint) accounting layer are also accessible.

<div class="warning">
The below documentation uses 9R (Nine Realms) infrastructure endpoints,
which are behind Cloudflare, subject to rate-limiting, and have other
stipulations.
<p></p>
It is recommended (and sometimes required) that requests sent to these
interfaces include an `X-Client-ID` header that identifies who you are.
If you have joined the THORChain Dev Discord, please set this header
to a value of `discord:YOURUSERNAME/YOURIDNUMBER` so that the requests
can be identified.
<p></p>
Users who are wishing to consume large amounts of data **SHOULD NOT**
use these endpoints, and should instead run their own Midgard and/or
THORNode infrastructure which can be queried (often via localhost).
</div>

## Midgard

- Swagger API docs: <https://midgard.ninerealms.com/v2/doc>

## THORNode

### THORNode layer

- Swagger API docs: <https://thornode.ninerealms.com/thorchain/doc>
- Archive endpoints:
  - <https://thornode-archive.ninerealms.com>
    - This endpoint will automatically use the correct versioned endpoint based on provided block height HTTP query param
- Versioned endpoints:
  - Blocks 17562001 to present: <https://thornode-v2.ninerealms.com>
  - Blocks 4786560 to 17562000: <https://thornode-v1.ninerealms.com>

### Cosmos (Tendermint) layer

- Accounts: <https://thornode.ninerealms.com/cosmos/auth/v1beta1/accounts>
- Account details: <https://thornode.ninerealms.com/cosmos/auth/v1beta1/accounts/ADDRESS>
- Supply: <https://thornode.ninerealms.com/cosmos/bank/v1beta1/supply>
- Transaction: <https://thornode.ninerealms.com/cosmos/tx/v1beta1/txs/TXNID>
  - Note: transaction ID **should not** include any `0x` prefix
- Wallet balance: <https://thornode.ninerealms.com/cosmos/bank/v1beta1/balances/ADDRESS>
