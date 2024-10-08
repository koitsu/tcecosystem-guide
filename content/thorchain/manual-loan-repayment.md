# Manual loan repayment

This article describes how you can pay off a loan manually by creating a
THORChain memo using the MsgDeposit feature and exclusively using RUNE
as the repayment asset.

This can be useful in two (2) scenarios:

1. Paying off a loan that has a small amount left on it.  As of late December 2023, it's common that there is price movement during the transaction.  This can/will result in a very small amount of debt remaining (usually in US cents), which blocks the return of your collateral
1. Cases where THORChain lending is partially suspended due to protocol issues.  When this is the case, front-ends tend to inhibit you from doing any loan operations, even though closures or repayments are usually still functional

<div class="warning">
<strong>This procedure only works when using RUNE as the repayment asset.</strong>
<p></p>
<strong>Other assets cannot be used with this procedure!</strong>
</div>

You can check the status of a loan at any time by following the
[Loan status](loan-status.md) procedure.

<div class="warning">
The below procedure is an advanced feature that should not be performed by
users unless they understand what they are doing.  A single typo or mistake
could result in loss of funds.
<p></p>
<strong>If you at any time feel unsure about using this procedure, then please
stop and use a front-end for safety!</strong>
</div>

## Procedure

The below procedure uses THORSwap as a front-end.  Other front-ends may not
support this feature due to its advanced use.

1. Get your loan address.  This is the wallet address with which you provided collateral.  Ex: if you opened a loan using BTC, this would be your Bitcoin address
1. Look up details of the loan using the [Midgard API]: `https://midgard.ninerealms.com/v2/borrower/YOUR_WALLET_ADDRESS`
   - In the above link, replace `YOUR_WALLET_ADDRESS` with your loan address from the previous step
   - In the resulting page, take note of the `collateral_asset` field &mdash; you'll need it later
1. In the upper right corner of THORSwap: **Cog wheel > Pro Mode Settings > Show Send Custom Tx > Enable**
1. In the menu on the left, click **Wallet > Send** and then **enable** the **Toggle custom MsgDeposit form** option
1. You must now manually create the memo string of the transaction.  This should be `LOAN-:collateral_asset:loan_address`
   - Refer to [official THORChain memo documentation][1] for the **Repay Loan** memo syntax itself
   - **Do not** specify a MINOUT parameter!
1. Things to note:
   - You will need at least 0.02 RUNE in your THORChain wallet to pay for gas
   - If the amount sent is in excess of the debt, the difference will be treated as a "credit" (associated with the loan address)
1. Click **Send**
1. Wait about 5 full minutes; the repayment transaction should be in progress.  In the THORSwap Transaction History UI (upper right of the site), you can click on the link button to be taken to [RuneScan] and watch the repayment transaction in real-time.  It will take several minutes, but [RuneScan] should eventually show "Success" for a "Repay" transaction.
1. Once the repayment is successful, THORChain will begin the process of sending the collateral back to the original address which opened the loan.  This is (usually) an outbound transaction and thus subject to THORChain outbound delays.  Refer to [Tracking a withdrawal](../thorswap/tracking-a-withdrawal.md) to find the outbound transaction and get its ETA.

## Example scenario

- An individual opened a loan for some BTC, providing collateral in ETH
- The ETH address associated with the loan is `0x123abcd`
- They have paid off 99% of their loan, but a small amount of debt worth US$0.41 remains and they need to pay it off fully
- They don't have any other assets to use to pay off their loan, so their friend comes to the rescue
- Their friend wants to help pay off their remaining debt using RUNE
- In this example, we pretend 1 RUNE == US$1.00

The friend then does the following:

1. Gets the loan address (address of ETH collateral): 0x123abcd
1. Visits `https://midgard.ninerealms.com/v2/borrower/0x123abcd` and sees `collateral_asset` is `ETH.ETH`
1. Connects their THORChain wallet to THORSwap, enables "Show Send Custom Tx", and goes to Wallet > Send
1. Manually enters a memo of `LOAN-:ETH.ETH:0x123abcd`
1. Selects RUNE, and chooses an amount of 0.50
1. Clicks Send
   - A total of 0.52 RUNE will taken from their wallet: 0.50 for the loan repayment, and 0.02 for transaction fees/gas
   - The US$0.09 worth of RUNE "in excess" will be tracked as a credit, associated with the loan address `0x123abcd`
1. Waits a few minutes then checks the transaction on [RuneScan]: it says "Success" and "Repay"
1. Waits a few more minutes, then follows the [Tracking a withdrawal](../thorswap/tracking-a-withdrawal.md) procedure
   - He finds the ETH collateral is in the [Scheduled Queue](queues.md) and is to be processed in 55 minutes

[1]: https://dev.thorchain.org/concepts/memos.html#repay-loan
[Midgard API]: https://midgard.ninerealms.com/v2/doc
[RuneScan]: https://runescan.io/
