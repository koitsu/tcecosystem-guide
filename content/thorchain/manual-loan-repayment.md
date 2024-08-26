# Manual loan repayment

When paying off a loan on THORChain, as of this writing (2023/12/29), it's
common that there is price movement during the transaction.  This can/will
result in a very small amount of debt remaining (usually in US cents),
which blocks the return of your collateral.  You can check this by following
the [Loan status](loan-status.md) procedure.

The rest of this article describes how you can pay off the remaining part of
the loan by manually creating a THORChain memo using the MsgDeposit feature.

<div class="warning">
The below procedure is an advanced feature that should not be performed by
users unless they understand what they are doing.  A single typo or mistake
could result in loss of funds.
<p></p>
<strong>If you at any time feel unsure about using this procedure, then please
stop and use a front-end for safety!</strong>
</div>

## Procedure

1. Get your loan address.  This is the wallet address with which you provided collateral.  Ex: if you opened a loan using BTC, this would be your Bitcoin address
1. Look up details of the loan using the [Midgard API]: `https://midgard.ninerealms.com/v2/borrower/YOUR_WALLET_ADDRESS`
   - In the above link, replace `YOUR_WALLET_ADDRESS` with your loan address from the previous step
   - In the resulting page, take note of the `collateral_asset` field -- you'll need it later
1. In the upper right corner of THORSwap: **Cog wheel > Pro Mode Settings > Show Send Custom Tx > Enable**
1. In the menu on the left, click **Wallet > Send** and then **enable** the **Toggle custom MsgDeposit form** option
1. You must now manually create the memo string of the transaction.  This should be `LOAN-:collateral_asset:loan_address`
   - Refer to [official THORChain memo documentation][1] for the **Repay Loan** memo syntax itself
   - **Do not** specify a MINOUT parameter!
1. Select the source asset you want to use to pay off the loan, and the amount.  Things to note:
   - Gas/transaction fees will come of out of the sender's wallet and **is not** part of the "amount to send"
   - If the amount sent is in excess of the debt, the difference will be treated as a "credit" (associated with the loan address)
1. Click **Send**
1. The repayment transaction should be in progress.  In the THORSwap Transaction History UI (upper right of the site), you can click on the link button to be taken to [RuneScan] and watch the repayment transaction in real-time.  It will take several minutes, but [RuneScan] should eventually show "Success" for a "Repay" transaction.
1. Once the repayment is successful, THORChain will begin the process of sending the colleteral back to the original address which opened the loan.  This is (usually) an outbound transaction and thus subject to THORChain outbound delays.  Refer to [Tracking a withdrawal](../thorswap/tracking-a-withdrawal.md) to find the outbound transaction and get its ETA.

## Example scenario

- An individual opened a loan for some BTC, providing collateral in ETH
- The ETH address associated with the loan is `0x123abcd`
- They have paid off 99% of their loan, but a small amount of debt worth US$0.45 remains and they need to pay it off fully
- They don't have any other assets to use to pay off their loan, so their friend comes to the rescue
- Their friend wants to help pay off their remaining debt using RUNE
- In this scenario, 1 RUNE is worth US$1.00

The friend then does the following:

1. Gets the loan address (address of ETH collateral): 0x123abcd
1. Visits `https://midgard.ninerealms.com/v2/borrower/0x123abcd` and sees `collateral_asset` is `ETH.ETH`
1. Connects their THORChain wallet to THORSwap, enables "Show Send Custom Tx", and goes to Wallet > Send
1. Manually enters a memo of `LOAN-:ETH.ETH:0x123abcd`
1. Selects RUNE, and chooses an amount of 1.01.  (The minimum amount of RUNE you can send has exceed that of US$1.00.  This is a THORSwap limitation.)
1. Clicks Send
   - A total of 1.03 RUNE will taken from their wallet: 1.01 for the loan repayment, and 0.02 for transaction fees/gas
   - The $0.56 worth of RUNE "in excess" will be tracked as a credit, associated with the loan address `0x123abcd`
1. Waits a few minutes then checks the transaction on [RuneScan]: it says "Success" and "Repay"
1. Waits a few more minutes, then follows the [Tracking a withdrawal](../thorswap/tracking-a-withdrawal.md) procedure
   - He finds the ETH collateral is in the [Scheduled Queue](queues.md) and is to be processed in 55 minutes

[1]: https://dev.thorchain.org/concepts/memos.html#repay-loan
[Midgard API]: https://midgard.ninerealms.com/v2/doc
[RuneScan]: https://runescan.io/
