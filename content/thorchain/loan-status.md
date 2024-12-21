# Loan status 

There are two (2) ways you can check the state of your loan:

## rune.tools

1. Visit the [rune.tools Lending Position app]
1. Select the collateral asset type (BTC or ETH)
1. Enter your loan address.  This is the wallet address with which you provided collateral.  Ex: if you opened a loan using BTC, this would be your Bitcoin address

You will be shown your current debt and current collateral amounts.

If your current debt is shown as $0.00 then your loan has been paid off in full (or has a loan credit).

## RuneScan

1. Visit [RuneScan]
1. Search for your loan address.  This is the wallet address with which you provided collateral.  Ex: if you opened a loan using BTC, this would be your Bitcoin address
   - If your address is found, it will appear in a pull-down menu which you must select (unlike other search interfaces where you need to hit Enter)
1. Click the **Loans** tab
   - This will only be present if you have an open loan or a loan credit
   - If there is no **Loans** tab, then the address no longer has an open loan
   - If there is a negative value for **Debt Current** then your address has a loan credit

## Collateral return check

If you're closing a loan and want to check the status of your collateral being returned to you:

1. Use one of the above two sites and ensure you have either a) no remaining debt, or b) a loan credit
1. Follow the [Tracking a withdrawal](../thorswap/tracking-a-withdrawal.md) procedure

If your debt has been mostly paid off, but shows small remainder left (ex. less than $1.00), refer to the
[Manual loan repayment](manual-loan-repayment.md)
procedure to use RUNE to pay off the remainder.

[RuneScan]: https://runescan.io/
[rune.tools Lending Position app]: https://rune.tools/lending
