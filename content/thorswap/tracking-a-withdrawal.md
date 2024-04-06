# Tracking a withdrawal

These instructions can be used for any of the following scenarios:

- Withdrawing from an LP
- Withdrawing from Savers/Earn
- Closing a loan

## Procedure

1. Visit the [9R THORChain Tracker]
1. Search the web page for the **last 4 digits of your destination wallet address** using your browser (Ctrl-F or Command-F)
   - "Wallet address" in this context means the address to which the funds are being **sent to** (or **withdrawn to**)
   - **DO NOT use the "Swap Transaction ID" search box at the top of the page!**
1. If you are able to find your transaction:
   - See if it's under the **Outbound** or **Scheduled** sections of the page:
     - **Outbound**: your transaction is currently being processed by THORChain (i.e. not delayed).  However, be aware there are cases where additional network delays can occur, such as during THORChain Asgard [vault churn][1]. There is no need to worry, it will get processed!
     - **Scheduled**: your transaction is delayed due to THORChain's [outbound throttling](delays.md) security mechanism.  There's an **ETA** column for your transaction, which is the amount of time remaining until your transaction is moved into the **Outbound** queue
   - Once the transaction has left the **Outbound** queue, then it should be on the blockchain of whatever asset you were withdrawing and no longer THORChain's responsibility
   - Use a blockchain explorer for that blockchain network and search for your destination wallet address.  A good starter is [Blockchair] &mdash; but it depends on the blockchain!
   - You should eventually be able to find the deposit or receive transaction into your wallet.  Every wallet has different confirmation count requirements, so when the asset will arrive in your wallet now depends on validators (miners) on that blockchain

If you are still not able to find your transaction, ask for help in the
THORSwap Discord channel `#lp-and-earn` where THORSwap community moderators can
help.  If you prefer official THORSwap staff support which is one-on-one and
private, open a ticket in the `#support-desk` channel and be patient.

[1]: https://docs.thorchain.org/thornodes/overview#churning
[9R THORChain Tracker]: https://track.ninerealms.com/
[Blockchair]: https://blockchair.com/
