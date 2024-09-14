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
1. You must now manually create the memo string of the transaction.  This should be `POOL-:basispoints`
   - Refer to [official THORChain memo documentation][1] for the **Withdraw RUNEPool** memo syntax itself
   - `basispoints` should be a value of 0 to 10000, where `10000` means withdraw 100%, `5000` means withdraw 50%, etc.
   - **Do not** specify AFFILIATE or FEE parameters!
1. Click **Send**
1. The withdrawal should happen quickly (since everything is native to THORChain and not off-network)

[1]: https://dev.thorchain.org/concepts/memos.html#withdraw-runepool
