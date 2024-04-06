# Manual loan repayment

When paying off a loan on THORChain, as of this writing (2023/12/29), it's
common that there is price movement during the transaction.  This can/will
result in a very small amount of debt remaining (usually in US cents).  This
section describes how you can pay off the remaining part of the loan by
manually creating a THORChain memo using the MsgDeposit feature.

## Procedure

1. Get the collateral address associated with the loan
1. Look up details of the loan using the [Midgard API] using the collateral address: `https://midgard.ninerealms.com/v2/borrower/YOUR_WALLET_ADDRESS`
   - In the above link, replace `YOUR_WALLET_ADDRESS` with the address with which you deposited collateral
   - In the resulting page, take note of the `collateral_asset` field -- you'll need it later
1. In the upper right corner of THORSwap: **Cog wheel > Pro Mode Settings > Show Send Custom Tx > Enable**
1. In the menu on the left, click **Wallet > Send** and then **enable** the **Toggle custom MsgDeposit form** option
1. You must now manually create the memo string of the transaction.  This should be `LOAN-:collateral_asset:loan_address`
   - Refer to [official THORChain memo documentation][1] for the **Repay Loan** memo syntax itself
   - **Do not** specify a MINOUT parameter!
1. Select the source asset you want to use to pay off the loan, and the amount.  Things to note:
   - Gas/transaction fees will come of out of the sender's wallet and **is not** part of the "amount to send"
   - If the amount sent is in excess of the debt, the difference will be treated as a "credit" (associated with the collateral address)
1. Click **Send**
1. The repayment transaction should be in progress.  In the THORSwap Transaction History UI (upper right of the site), you can click on the link button to be taken to [RuneScan] and watch the repayment transaction in real-time.  It will take several minutes, but [RuneScan] should eventually show "Success" for a "Repay" transaction.
1. Once the repayment is successful, THORChain will begin the process of sending the colleteral back to the original address which opened the loan.  This is (usually) an outbound transaction and thus subject to THORChain outbound delays.  Refer to [How to track a transaction] to find the outbound transaction and get its ETA.

## Example scenario

- An individual opened a loan for some BTC, providing collateral in ETH
- The Ethereum ETH address associated with the loan is `0x123abcd`
- They have paid off 99% of their loan, but a small amount of debt worth US$0.45 remains and they need to pay it off fully
- They don't have any other assets to use to pay off their loan, so their friend comes to the rescue
- Their friend wants to help pay off their remaining debt using RUNE
- In this scenario, 1 RUNE is worth US$1.00

The friend then does the following:

1. Gets the collateral address for the loan: 0x123abcd
1. Visits `https://midgard.ninerealms.com/v2/borrower/0x123abcd` and sees `collateral_asset` is `ETH.ETH`
1. Connects their THORChain wallet to THORSwap, enables "Show Send Custom Tx", and goes to Wallet > Send
1. Manually enters a memo of `LOAN-:ETH.ETH:0x123abcd`
1. Selects RUNE, and chooses an amount of 1.01.  (The minimum amount of RUNE you can send has exceed that of US$1.00.  This is a THORSwap limitation.)
1. Clicks Send
   - A total of 1.03 RUNE will taken from their wallet: 1.01 for the loan repayment, and 0.02 for transaction fees/gas
   - The $0.56 worth of RUNE "in excess" will be tracked as a credit for collateral address `0x123abcd` (for future loans)
1. Waits a few minutes then checks the transaction on [RuneScan]: it says "Success" and "Repay"
1. Waits a few more minutes, then follows the [Tracking a withdrawal](tracking-a-withdrawal.md) procedure.  He finds that the ETH collateral is in the THORChain scheduled queue (to be processed in 55 minutes).  Nothing more to do but wait!

[1]: https://dev.thorchain.org/concepts/memos.html#repay-loan
[Midgard API]: https://midgard.ninerealms.com/v2/doc
[RuneScan]: https://runescan.io/
