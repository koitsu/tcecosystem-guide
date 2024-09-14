# Manual RUNEPool withdrawal

This article describes how you can withdraw from THORChain's RUNEPool
by creating a THORChain memo using the MsgDeposit feature.

This can be useful in cases where a THORChain front-end is experiencing
issues with RUNEPool, and other front-ends are not a viable option.

You can check your RUNEPool position by following relevant instructions
in the [RUNEPool](runepool.md) document.

<div class="warning">
The below procedure is an advanced feature.
<p></p>
<strong>If you at any time feel unsure about using this procedure, then please
stop and wait for the front-end to fix their issue!</strong>
</div>

## Procedure

The below procedure uses THORSwap as a front-end.  Other front-ends may not
support this feature due to its advanced use.

1. Visit THORSwap
1. Connect your THORChain/RUNE wallet originally used for the RUNEPool deposit
   - Make sure your wallet contains at least 0.02 RUNE to pay for gas!
1. In the upper right corner of THORSwap: **Cog wheel > Pro Mode Settings > Show Send Custom Tx > Enable**
1. In the menu on the left, click **Wallet > Send** and then **enable** the **Toggle custom MsgDeposit form** option
1. **Do not** enter any amount to send!
1. In the Memo field, enter `POOL-:basispoints` with the following changes:
   - `basispoints` should be from 0 to 10000, where `10000` means withdraw 100%, `5000` means 50%, and so on
   - Refer to [official THORChain memo documentation][1] for the **Withdraw RUNEPool** memo syntax itself
   - **Do not** specify AFFILIATE or FEE parameters!
1. Click **Send**
1. The withdrawal should happen quickly (within a few minutes), since everything stays on THORChain

<div class="warning">
Please note that after doing so, THORSwap's Transaction History UI will show an
infinite spinner.  When expanding the UI, it will state that there is a pending
**Deposit** transaction of **Send 0 RUNE**.
<p></p>
This is a THORSwap UI bug.  You can safely ignore it, or click the trash can icon,
then Confirm, to clear your entire Transaction History.  (Sadly there is no way to
remove just this one individual entry.)
</div>

[1]: https://dev.thorchain.org/concepts/memos.html#withdraw-runepool
