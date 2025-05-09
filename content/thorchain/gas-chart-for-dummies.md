# Gas chart for dummies

| Details                        | Gas required        | Required wallet connection    |
| ------------------------------ | ------------------- | ----------------------------- |
| Send asset                     | Native chain        | Native chain                  |
| Swap asset X to asset Y        | Native chain for X  | Native chain for X and/or Y<sup>†</sup> |
| Swap synth X to asset Y        | RUNE ≥0.02          | THORChain                     |
| LP asymm: deposit RUNE         | RUNE                | THORChain                     |
| LP asymm: withdraw RUNE        | RUNE ≥0.02          | THORChain                     |
| LP asymm: deposit asset        | Native chain        | Native chain                  |
| LP asymm: withdraw asset       | Native chain        | Native chain                  |
| LP symm: deposit RUNE + asset  | RUNE + native chain | THORChain and native chain    |
| LP symm: withdraw RUNE + asset | RUNE ≥0.02          | THORChain                     |
| LP symm: withdraw 100% asset   | RUNE ≥0.02          | THORChain                     |
| LP symm: withdraw 100% RUNE    | RUNE ≥0.02          | THORChain                     |
| Earn/Savers deposit            | Native chain        | Native chain                  |
| Earn/Savers withdraw           | Native chain        | Native chain                  |
| RUNEPool deposit               | RUNE ≥0.02          | THORChain                     |
| RUNEPool withdraw              | RUNE ≥0.02          | THORChain                     |
| Claiming TCY (Savers/Lending)  | Native chain        | Native chain<sup>‡</sup>       |
| Claiming TCY (Synths)          | RUNE ≥0.02          | THORChain                     |
| Staking TCY                    | RUNE ≥0.02          | THORChain                     |
| Unstaking TCY                  | RUNE ≥0.02          | THORChain                     |
| TCY compounding options        | RUNE ≥0.02          | THORChain                     |
| Staking $THOR into $vTHOR      | ETH (ERC20)         | Ethereum                      |
| Unstaking $vTHOR into $THOR    | ETH (ERC20)         | Ethereum                      |

> <sup>†</sup>&ensp; On THORSwap and possibly other front-ends, it is possible to swap from
asset X to Y with only the native chain for X connected.  Simply enable the
**Custom Recipient Address** feature in the Swap UI cog wheel, then manually enter
the destination address for asset Y.  (If you don't use this feature, then THORSwap
automatically populates the recipient address for you, as long as you connect chains
for both asset X and asset Y simultaneously.  This can pose a problem for hardware
wallets like Ledger, hence the aforementioned feature.)
>
> <sup>‡</sup>&ensp; Transaction cost when claiming varies per native chain.  For example,
it's known that for BTC, a minimum of 0.00012 BTC is required.  Other chains are
more difficult to calculate.  Please refer to gas trackers for whatever chain your
asset is on, or simply try claiming and see if you get an insufficient balance error.

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
| TCY             | THORChain            | RUNE           |
| THOR (ERC20)    | Ethereum             | ETH (ERC20)    |
| USDC (AVAX)     | Avalanche C-Chain    | AVAX           |
| USDC (BEP20)    | Binance Smart Chain  | BNB (BEP20)    |
| USDT (ARB)      | Arbitrum             | ETH (ARB)      |
| USDT (ERC20)    | Ethereum             | ETH (ERC20)    |
| USK (Kujira)    | Kujira               | KUJI           |
