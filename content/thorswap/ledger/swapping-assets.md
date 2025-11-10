# Swapping assets

There are two options for swapping using a Ledger:

## Use Ledger Wallet

Follow Ledger's official [How to swap crypto using THORSwap][1] procedure.

## Use THORSwap directly

The biggest complication with Ledger devices stems from the fact that only one
app can be run at a time.  When trying to swap from assets X to Y, THORSwap
normally prefers the chains of both assets X and Y be connected at once.  X is
mandatory, while having Y attached just makes THORSwap auto-populate the
**Recipient Address** field.

A little-known feature of THORSwap is that you can actually do a swap from
asset X to Y with only chain X atttached **as long as you know the wallet
address of Y.**  This method uses the **Custom Recipient Address** feature of
THORSwap, and in the case of Ledger, can save users a lot of pain.

1. Ensure Ledger Wallet is not running or in the system tray; if so, exit it
1. Find the wallet address of asset Y (i.e. destination asset); save it/copy it somewhere
   - **Note: it's important you get the correct address for the correct chain.  It is very possible to send funds to a wrong address/wrong chain and lose the funds.  Please double-check your wallet address!**
1. Attach your Ledger to your USB port (if not already)
1. On your Ledger, run the relevant application for the chain asset X is on.  (See below notes too)
1. Launch your web browser (Chrome and Brave confirmed working)
1. Visit the [THORSwap app]
1. Click the "Connect" button in the upper right
1. Under **Hardware Wallets**, select **Ledger**
1. In the **Select chains** menu on the left, select the chain asset X is on
1. Click **Connect Wallet**
1. If you get a pop-up that says `app.thorswap.finance wants to connect`, click your Ledger device, then click **Connect**
1. In the bottom right of the THORSwap UI, you should see some messages that pop up/disappear that says something like `Connecting XYZ Ledger #0` and `Successfully connected XYZ Ledger #0`
1. Click the **Wallet** button in the upper right and verify your wallet contents are correct
1. In the Swap UI:
   1. To the right of the word **Swap**, there should be a cog wheel.  Click it, then change **Set Custom Recipient** to **On**
   1. Change the top asset to asset X, then enter the asset quantity you wish to swap
   1. Change the lower asset to asset Y
1. In the Recipient Address field, paste the destination address you copied/saved in Step #2
1. Click Swap

[THORSwap app]: https://app.thorswap.finance/
[1]: https://support.ledger.com/hc/en-us/articles/12168993164957-How-to-swap-crypto-using-THORSwap?docs=true
