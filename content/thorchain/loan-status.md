# Loan status 

You can use [RuneScan] to check the state of your loan:

1. Visit [RuneScan]
1. Search for your loan address.  This is the wallet address with which you provided collateral.  Ex: if you opened a loan using BTC, this would be your Bitcoin address
   - If your address is found, it will appear in a pull-down menu which you must select (unlike other search interfaces where you need to hit Enter)
   - Alternately, you can visit `https://runescan.io/address/YOUR_WALLET_ADDRESS` in your browser
1. Click the **Loans** tab
   - This will only be present if you have an open loan or a loan credit
   - If there is no **Loans** tab, then the address no longer has an open loan
   - If there is a negative value for **Debt Current** then your address has a loan credit

You can also examine your transactions on RuneScan:

- Loan open transactions will show "Loan" in blue
- Loan repayments (or closures) transactions will show "Repay" in green
- You can drill down onto any transaction to see its state.  Completed
  transactions will show "Success" in green

If you're closing a loan and want to check the status of your collateral
being returned to you:

- Use RuneScan to make sure your loan is paid off in full (i.e. no **Loans** tab, or
  a loan credit is present), as described above
- Follow the [Tracking a withdrawal](../thorswap/tracking-a-withdrawal.md) procedure

If you have a loan that you've paid off, but still have a small amount left on it
(ex. less than US$1.00), refer to the
[Manual loan repayment](manual-loan-repayment.html)
procedure to learn how to use RUNE to pay off the small remainder.

[RuneScan]: https://runescan.io/
