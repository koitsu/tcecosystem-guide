# Dust threshold chart

| Asset           | Threshold         | Equivalent      |
| --------------- | ----------------- | --------------- |
| BTC             | 10,000 sats       | 0.0001 BTC      |
| BCH             | 10,000 sats       | 0.0001 BCH      |
| LTC             | 10,000 sats       | 0.0001 LTC      |
| DOGE            | 100,000,000 koinu | 1 DOGE          |
| ETH and ERC20   | 10 gwei           | 0.00000001 ETH  |
| AVAX            | 10 gwei           | 0.00000001 AVAX |
| ATOM            | 0 uatom           | 0 ATOM          |
| BNB             | 0 nbnb            | 0 BNB           |

<div class="warning">
ETH and AVAX have a 10 gwei threshold due to those chains using 1e18
granularity.  However, THORChain only supports up to 1e8 granularity.
</div>
<div class="warning">
As of November 2023, the
<a href="https://dev.thorchain.org/saving-guide/quickstart-guide.html#basic-mechanics">original source</a>
for these values is incorrect and outdated.
</div>
