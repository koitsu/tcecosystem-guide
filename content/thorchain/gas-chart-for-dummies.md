# Gas chart for dummies

| Details                       | Gas required        | Required wallet connection    |
| ----------------------------- | ------------------- | ----------------------------- |
| Swap asset X to asset Y       | Native chain for X  | Native chain for X and/or Y<sup>†</sup> |
| Swap synth X to asset Y       | RUNE ≥0.02          | THORChain                     |
| LP Deposit  asymm RUNE        | RUNE                | THORChain                     |
| LP Withdraw asymm RUNE        | RUNE ≥0.02          | THORChain                     |
| LP Deposit  asymm asset       | Native chain        | Native chain                  |
| LP Withdraw asymm asset       | Native chain        | Native chain                  |
| LP Deposit  symm RUNE + asset | RUNE + native chain | THORChain and native chain    |
| LP Withdraw symm RUNE + asset | RUNE ≥0.02          | THORChain                     |
| LP Withdraw symm (100% RUNE)  | RUNE ≥0.02          | THORChain                     |
| LP Withdraw symm (100% asset) | RUNE ≥0.02          | THORChain                     |
| Earn/Savers Deposit           | Native chain        | Native chain                  |
| Earn/Savers Withdraw          | Native chain        | Native chain                  |
| Staking $THOR into $vTHOR     | ETH                 | Ethereum                      |
| Unstaking $vTHOR into $THOR   | ETH                 | Ethereum                      |

"Native chain" means whatever chain an asset lives on.  Some examples:

| Asset           | Chain                | Gas asset      |
| --------------- | -------------------- | -------------- |
| ATOM (BEP20)    | Binance Smart Chain  | BNB (BEP20)    |
| ATOM (Cosmos)   | Cosmos               | ATOM           |
| BCH             | Bitcoin Cash         | BCH            |
| BTC             | Bitcoin              | BTC            |
| CACAO           | Maya Protocol        | CACAO          |
| DOGE            | Dogecoin             | DOGE           |
| LTC             | Litecoin             | LTC            |
| RUNE            | THORChain            | RUNE           |
| Synths          | THORChain            | RUNE           |
| THOR (ERC20)    | Ethereum             | ETH            |
| USDC (AVAX)     | Avalanche C-Chain    | AVAX           |
| USDC (BEP20)    | Binance Smart Chain  | BNB (BEP20)    |
| USDT (Arbitrum) | Arbitrum             | ETH (Arbitrum) |
| USDT (ERC20)    | Ethereum             | ETH            |
| USK (Kujira)    | Kujira               | KUJI           |

<sup>†</sup>: On THORSwap and possibly other front-ends, it is possible to swap from
asset X to Y with only the native chain for X connected.  Simply enable the
**Custom Recipient Address** feature in the Swap UI cog wheel, then manually enter
the destination address for asset Y.  (If you don't use this feature, then THORSwap
automatically populates the recipient address for you, as long as you connect chains
for both asset X and asset Y simultaneously.  This can pose a problem for hardware
wallets like Ledger, hence the aforementioned feature.)
