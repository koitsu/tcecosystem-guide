# Dust threshold chart

The below values were last updated October 17th 2026.

<div class="warning">
It is possible for these values to be outdated.  Always check the API first!
</div>

The THORChain protocol honours the `dust_threshold` parameter obtained from the
[inbound addresses](https://gateway.liquify.com/chain/thorchain_api/thorchain/inbound_addresses)
API endpoint.  The values are in 1e8 format, as THORChain only supports 1e8
granularity (even for EVM chains and AVAX).

Threshold minimums are therefore calculated as `dust_threshold / 10^8`.

| Asset (chain)   | Raw API value | Threshold minimum |
| --------------- | ------------- | ----------------- |
| ATOM            | 1000000       | 0.01 ATOM         |
| AVAX            | 100000        | 0.001 AVAX        |
| BCH             | 10000         | 0.0001 BCH        |
| BNB             | 10000         | 0.0001 BNB        |
| BTC             | 1000          | 0.00001 BTC       |
| DOGE            | 100000000     | 1 DOGE            |
| ETH (BASE)      | 10000         | 0.0001 ETH        |
| ETH (ERC20)     | 1000          | 0.00001 ETH       |
| LTC             | 100000        | 0.0001 LTC        |
| SOL             | 100000        | 0.0001 SOL        |
| TRON (TRC20)    | 10000000      | 0.1 TRON          |
| XRP             | 100000000     | 1 XRP             |
| ZEC             | 15000         | 0.00015 ZEC       |
