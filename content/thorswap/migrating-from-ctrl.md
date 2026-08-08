# Migrating from Ctrl Wallet

## Preface

As of August 3rd 2026, Ctrl Wallet is no longer functional:

<https://ctrl.xyz/news/ctrl-wallet-deprecation-what-you-need-to-know/>

Ctrl Wallet users should therefore extract their seed phrase ("Recovery Phrase")
and import it into another wallet.  The above link describes how to extract
your seed phrase.

<div class="warning">
Please extract your seed phrase no matter what &mdash; even if it means
temporarily writing it down on a piece of paper!  Your seed phrase represents
your entire wallet (all accounts) and is how you gain access to your funds that
live on each respective blockchain.
</div>

This document is intended to help THORSwap users migrate from Ctrl Wallet to
either a) Metro Wallet (on V3 THORSwap or Metro Exchange), or b) Keystore File
(on V2 THORSwap).

Here are links to each respective interface:

- V2 THORSwap: <https://v2.thorswap.finance/>
- V3 THORSwap: <https://thorswap.finance/>
- Metro Exchange: <https://metro.exchange/>

Which you choose depends on what types of assets, investments, and features you
use; everyone's use-cases are different.  Continue reading.

## Do you have any THORChain investments?

"THORChain investments" specifically refers to these aspects of THORChain:

- TCY staking, unstaking, and claiming
- Liquidity Pools (symmetrical or asymmetrical)
- Savers/Earn
- Lending/Loans
- RunePool
- Node bonding

"THORChain investments" **DOES NOT** refer to holding TCY or holding RUNE.  TCY
and RUNE as held assets are simply layer-1 coins on THORChain and are supported
in V3 THORSwap as well as Metro Exchange.

If **no**: V3 THORSwap or Metro Exchange will be a great fit for you,
especially when using Metro Wallet (THORSwap's built-in client-side wallet).
Simply
[import your Ctrl Wallet seed phrase into Metro Wallet](https://docs.thorswap.finance/thorswap/thorswap/wallets/migrate-ctrl-wallet)
and you're ready to go.

If **yes**: you should use V2 THORSwap with Keystore File for accessing these
features, as V3 THORSwap nor Metro Exchange support these features.  In this
scenario,
[import your Ctrl Wallet seed phrase into Keystore File](https://docs.thorswap.finance/thorswap/thorswap/wallets/importing-a-wallet-to-keystore)
using V2 THORSwap and then keep reading.

As of this writing (August 2026) there are practically no wallets that support
both THORChain investment features as well as multiple assets; even wallets
like Keplr do not actually function correctly when trying to do
THORChain-related transactions.  Metro Wallet and/or Keystore File are the best
choices right now.

## Do you use multiple accounts in Ctrl?

If **no**: then use of Metro Wallet (on V3 THORSwap or Metro Exchange) is a
great choice, but feel free to use whatever wallet fits your needs.

If **yes**: you need to determine what the derivation paths of your accounts
are (more specifically, the index numbers in the derivation path for each
account).  This process is long and tedious, due to wallets choosing not to
show useful information (derivation paths) on a per-address basis.

A single wallet (seed phrase) can contain literally millions of addresses, all
referenced by a combination of derivation path parameters -- particularly the
`account` and `index` fields.  The `index` field is the last number in the
derivation path.

Many wallets (including Ctrl) inaccurately used the term "account" to represent
the `index` field, which creates further confusion.  In other words: the term
"Account" in Ctrl actually refers to the `index` field in a derivation path.

For example, a single seed phrase wallet might contain the following addresses
(derivation paths) for THORChain (coin type 931).  Note the change in `index`
field (0 vs. 1 vs. 2):

```
m/44'/931'/0'/0/0 = thor1abcdefghijklmnopqrstuvwxyz0123456789ab
m/44'/931'/0'/0/1 = thor1jhswhogxcixgoijo33hkjxdfxi83hsds8zx8ig
m/44'/931'/0'/0/2 = thor19hskjxl298xhg34nposfpjxihuieyh22sdfhyx
```

Unfortunately, Ctrl Wallet does not offer a way to display full derivation path
information on an account or wallet address.  This makes it difficult to
determine which index is associated with what wallet address.

So how do we do it?  There are 3 options:

1. Trial and error method using V2 THORSwap and Keystore File

   When connecting your wallet, **select only a single chain**, then manually enter
   the index number of the account you wish to access.  The default index is 0.

   Look closely at the Wallet menu/UI and take note of what your addresses are.
   Compare these to what's in Ctrl.  Disconnect your wallet, reconnect your wallet
   and select index 1, etc...  Repeat the process until you've create a "mapping"
   of index numbers with wallet addresses.

   Be aware that in V2 THORSwap, some chains (particularly EVM) offer different derivation
   path syntaxes.  Use the default, named `MetaMask (m/44'/xxx'/0'/0/{index})`.

2. Use Metro Wallet to scan indexes

   When importing a seed phrase into Metro Wallet (on V3 THORSwap or Metro
   Exchange), the front-end will "scan" various derivation paths for assets.  If
   assets are found, the derivation path will be shown and its associated address.

   THORChain users should be aware Metro Wallet only scans coin type 931 (which is
   correct), not coin type 118.

3. Use Keplr Wallet to scan indexes

   The [Keplr Wallet browser extension](https://www.keplr.app/), when importing a
   seed phrase, can/will "scan" various derivation paths for assets.  If you hold
   Cosmos, RUNE, or TCY assets across multiple accounts, this can be helpful.

   This information is shown only at the very last step of importing and no where
   else in the wallet.  If this information isn't shown, then odds are it only
   found assets on a single index.

   However, this comes with several complications and nuances which are too long
   to go into here &mdash; especially those involving incorrect coin type 118.
   "Old" Ctrl Wallet users may run into this situation (for THORChain assets),
   pertaining to Ctrl Wallet (as well as Keplr) using incorrect coin type 118 to
   represnent THORChain derivation paths (they should have used 931).  In this
   scenario, it's recommended you open a support ticket on THORSwap's website or
   on their official Discord, as the process is complicated.

General advice: despite how tempting "a single wallet with multiple accounts"
may be, in general this feature is poorly supported by most wallet softwares
when used on DEXes.  It's generally safer to have multiple wallets (one per
account), then keep a list of addresses associated with each wallet.

## Wallets using incorrect coin type 118 for THORChain

Old versions of some wallets &mdash; such as Ctrl Wallet and Keplr Wallet
&mdash; incorrectly used coin type 118 (Cosmos) for THORChain derivation paths.
THORChain has always used coin type 931.  How/why this happened is unknown, but
it's suspected these wallet vendors assumed THORChain used coin type 118 since
THORChain uses Cosmos/Tendermint.

As of this writing (August 2026), any wallet address using a coin type 118
derivation path will usually fail when attempting to do transactions with
THORChain assets.

Here is a breakdown of the behaviours per wallet and coin type:

| Wallet        | Coin type  | Method         | Result                                     |
| ------------- | ---------- | -------------- | ------------------------------------------ |
| Ctrl Wallet   | 118        | In wallet      | Transactions fail, no longer functional    |
| Ctrl Wallet   | 931        | In wallet      | No longer functional as of August 3rd 2026 |
| Ctrl Wallet   | 118 or 931 | THORSwap       | Fails to connect or transactions fail      |
| Ctrl Wallet   | 118 or 931 | Metro Exchange | Fails to connect or transactions fail      |
| Keplr Wallet  | 118        | In wallet      | Send works, other transaction types fail   |
| Keplr Wallet  | 931        | In wallet      | Works                                      |
| Keplr Wallet  | 118        | THORSwap       | Fails with signature verification failed   |
| Keplr Wallet  | 931        | THORSwap       | Works                                      |
| Keplr Wallet  | 118        | Metro Exchange | Fails during approval phase                |
| Keplr Wallet  | 931        | Metro Exchange | Works                                      |
| Keystore File | 118        | THORSwap       | Cannot be used (only supports 931)         |
| Keystore File | 931        | THORSwap       | Works                                      |
| Keystore File | 118        | Metro Exchange | Cannot be used (only supports 931)         |
| Keystore File | 931        | Metro Exchange | Works                                      |

Unfortunately there is no "simple" way to determine what coin type your
THORChain addresses were generated from.  One method that is known to work,
however, is to import your seed phrase into Keplr Wallet.  If near the end of
the import phase you are shown multiple derivation paths &mdash; one for coin
type 931, and one for coin type 118 &mdash; along with your associated wallet
address, then odds are you do have a wallet using coin type 118.

If you have a wallet using coin type 118, it is **strongly recommended** that
you migrate to a new/fresh wallet that uses coin type 931.  You can do this in
any number of ways, but the easiest is to generate a new seed phrase and move
all your funds from your 118-based address to your new 931-based address.

Users who wish to use Keplr Wallet may find this process confusing given
extremely poor UI design on Keplr's part.  Here are the processes for Keplr:

For making a new wallet:

- Launch Keplr Wallet extension
- Add a new wallet
- Choose "Create a new wallet"
- Go through the process -- coin type 931 will be used by default

For making a new wallet backed by Ledger:

- Run the THORChain application on your Ledger device
- Launch Keplr Wallet extension
- Choose "Connect Hardware Wallet"
- Choose "Connect Ledger"
- Under "Connect to", choose the "THORChain app" menu item
  - This item is barely visible due to poor UI design; it's below "Secret app"
  - Selecting "THORChain app" ensures coin type 931
  - If you want to use multiple accounts or indexes, see below paragraph
- Choose "Next" and go through the USB approval dialog (if prompted)
- For chain selection, make sure THORChain is selected (Cosmos cannot be deselected)
- Go through the process -- you're done

If you want to use multiple accounts or indexes on your Ledger, you can do so by
using the "Set Custom Derivation Path (Advanced)" feature during the "Connect to"
step.  In this situation, the furthest right field represents the `index` number.
Repeat the process (adding a new wallet etc.) for each index you want to add.

You can verify coin type 931 by expanding your list of accounts; the Ledger
account should show a derivation path of `m/-'/931'/0'/0/0` (or another `index`
if applicable).

<div class="warning">
The "Set Custom Derivation Path (Advanced)" feature does not allow you to change
the coin type &mdash; only the index, receiving/change, and account fields can
be changed.  The "THORChain app" setting is what uses coin type 931, while the
"Cosmos app" setting (incorrectly) uses coin type 118.
</div>
