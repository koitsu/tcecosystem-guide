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

<sup>†</sup>: It is possible to swap from asset X to Y with only the native chain for X connected.  You can enable the **Custom Recipient Address** feature in the Swap UI and then manually enter the destination address for asset Y.  THORSwap populates this field for you automatically if you choose to connect both asset X and asset Y chains simultaneously.

"Native chain" means whatever chain an asset lives on.  Some examples:

| Chain                | Asset        | Gas asset   |
| -------------------- | ------------ | ----------- |
| Avalanche C-Chain    | USDC (AVAX)  | AVAX        |
| Binance Smart Chain  | USDC (BEP20) | BNB (BEP20) |
| Bitcoin              | BTC          | BTC         |
| Bitcoin Cash         | BCH          | BCH         |
| Cosmos               | ATOM         | ATOM        |
| Dogecoin             | DOGE         | DOGE        |
| Ethereum             | THOR (ERC20) | ETH         |
| Ethereum             | USDC (ERC20) | ETH         |
| Litecoin             | LTC          | LTC         |
| THORChain            | Any synth    | RUNE        |
