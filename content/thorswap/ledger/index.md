# Ledger

## Installing and using the THORChain Ledger app

1. [Follow Ledger's official documentation][1]
1. At the **Pending Ledger review** screen, press **both buttons** on your Ledger
1. Connect your Ledger to whatever front-end supports Ledger and THORChain

<div class="warning">
Failure to press both buttons at the "Pending Ledger review" screen will cause your
Ledger connection to fail!
</div>

## Failed Ethereum transactions

Some users have had success in enabling Blind Signing inside of the Ethereum
app on their Ledger.

In the Ethereum app, choose Settings &rarr; Blind Signing, then press both
buttons to change it to Enabled.

## Incorrect asset quantity

Ledger, especially with UTXO-based chains (ex. BTC, DOGE, etc.), tends to
"spread" funds across multiple indexes<sup>†</sup> on your Ledger.  Ledger Live
is able to aggregate all the assets/quantities into one lump sum.  This is
indirectly described in the official Ledger document titled
[Understanding Crypto Addresses and Derivation Paths][2].
However, THORSwap cannot do this -- it can only see one index at a time
(default index 0).  Here's an example:

- Pretend your Ledger Live says you have 1.2 BTC total
- Index 0 = address bc1abcd (holds 1 BTC)
- Index 16 = address bc12345 (holds 0.2 BTC)
- THORSwap says you only have 1 BTC.  The 0.2 BTC that's "missing" is because it's on index 16, not 0

The workaround:

1. Ensure Ledger Live is not running or in the system tray; if so, exit it
1. Connect your Ledger to THORSwap on the chain of your choice
1. Click the **Wallet** button in THORSwap and examine what your wallet address is -- this is the address of index 0.  Save/copy this address
1. Disconnect your Ledger from THORSwap
1. Launch Ledger Live
1. In Ledger Live, send the quantity of the asset to the address you previously copied in an earlier step
   - This is a super basic transaction that will cost you gas
   - What this does is effectively put the funds you send on index 0, since this is all THORSwap can see
1. Wait a little while for network confirmations on your transaction.  How long to wait depends on the chain's validators; most are pretty fast, but BTC in particular is slow (can take 30-45 minutes at times)
1. Re-connect your Ledger to THORSwap and you should see the funds you sent

<sup>†</sup>: We're unsure if this is account indexes or address indexes, but the end result for the user is the same regardless.

[1]: https://support.ledger.com/hc/en-us/articles/4402987997841-THORChain-RUNE-?docs=true
[2]: https://www.ledger.com/blog/understanding-crypto-addresses-and-derivation-paths
