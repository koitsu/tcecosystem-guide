# Manually claiming TCY

Sometimes the THORSwap interface has bugs or API issues with THORChain.  Below is a way you can claim TCY (for an old Savers/Earn position or open Loan) manually using a basic Send operation.

## Preparation

There are 2 steps that must be done before you can issue a claim:

### Get your own THORChain address

You need to have your own self-custody wallet THORChain address (thor1xxx).  Sometimes people call this a "RUNE wallet".

Any wallet that supports THORChain coin type 931 (the default) should work.

There are many wallets that support this asset.  Three examples are Trust Wallet, Gem Wallet, and Vultisig.

### Get THORChain protocol details

You now need to get various details from the THORChain protocol about the chain pertaining to
your Savers/Earn position or open Loan.  An example will be provided below.

1. Visit <https://gateway.liquify.com/chain/thorchain_api/thorchain/inbound_addresses> and look for a `chain: "XXX"` section, where `XXX` is the chain your asset lives on
   - Some chains are named unintuitively; for example, Cosmos chain is named `GAIA`
   - This is documented: <https://dev.thorchain.org/concepts/querying-thorchain.html>
1. Within the section, find the `halted` field and make sure it is set to `false`
   - If the value is `true` then you cannot issue a claim at this time (chain is paused on THORChain)
1. Within the section, find the `address` field, as you will need it later
   - Note: this address can change based on THORChain churn, load balancer infrastructure, and there being multiple THORChain vaults
1. Within the section, find the `dust_threshold` field and convert it from 1e8 format into into a human-readable number using math: `dust_threshold / 10^8`

Below is a preparation example for BCH chain.

<div class="warning">
This is purely an example and should not be used verbatim, otherwise you are likely to lose funds.
</div>

We visit <https://gateway.liquify.com/chain/thorchain_api/thorchain/inbound_addresses> and find the `"chain": "BCH"` section:

```json
{
    "chain": "BCH",
    "pub_key": "thorpub1addwnpepq2dxvtsjwz8de5k96ct7aap2d7ccgjeekr02n0eudcankqa02d89udx7767",
    "address": "qpk3zrsl6nlxm9mr8au8fenn932sjw0m8y4pnsakyk",
    "halted": false,
    "global_trading_paused": false,
    "chain_trading_paused": false,
    "chain_lp_actions_paused": false,
    "observed_fee_rate": "2",
    "gas_rate": "3",
    "gas_rate_units": "satsperbyte",
    "outbound_tx_size": "1500",
    "outbound_fee": "104393",
    "dust_threshold": "10000"
},
```

From this we can tell:

- The chain is not halted (`"halted": false`) -- great!
- The destination address is `qpk3zrsl6nlxm9mr8au8fenn932sjw0m8y4pnsakyk`
- The dust threshold is 10000, so the human readable value is 0.0001 (math: `10000 / 10^8`)

## Claim issuance

1. Connect your wallet to THORSwap V2: <https://v2.thorswap.finance/>
   - This should be the wallet that contains your Savers/Earn position or your Loan collateral
1. In the left menu, go to **Wallet > Send** and select the relevant asset
1. For the amount, enter the amount calculated from the **Preparation** step exactly -- no more, no less
1. For the recipient, enter the `address` from the **Preparation** step
1. For the memo, enter: `tcy:thor1xxx` where `thor1xxx` is your own THORChain address from the **Preparation** step
   - This syntax is documented: <https://dev.thorchain.org/concepts/memos.html#claim-tcy>
1. Click **Send**

Remember that newly claimed TCY is auto-staked, so it won't show up as (held) TCY in most wallets.  You can use one of the above block explorers to see how much staked TCY you have, or use Rune Tools (see below).

Additionally, remember that to **unstake** TCY, your THORChain wallet need to hold RUNE for transaction costs.  Each transaction costs 0.02 RUNE.

## Post-send verification

1. Visit either <https://runescan.io/> or <https://thorchain.net/> THORChain block explorers
1. Search for your own THORChain address
1. You should see a TCY Claim transaction that was successful (no errors).  If there are errors, they should be shown

You can also verify that your old Savers/Earn position or open Loan has been closed:

1. Visit <https://rune.tools/tcy-claims>
1. Search for your old Savers/Earn or open Loan address
1. The "Claimed" column should have a green checkmark

To verify you have staked TCY:

1. Visit <https://rune.tools/tcy>
1. Search for your THORChain address
1. Relevant details should be shown to you, including staked amount and any earnings over time
