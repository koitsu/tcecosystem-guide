# Queues

THORChain has two (2) kinds of queues that pertain directly to outbound
transactions: the Scheduled Queue, and the Outbound Queue.

You can see both of these queues using the [9R THORChain Tracker].

## Scheduled Queue

Transactions in the Scheduled Queue are intentionally delayed due to
THORChain's [outbound throttling](delays.md) security mechanism.

Transactions in this queue have an **ETA** field, which is the amount of time
remaining until your transaction is moved into the Outbound queue.

## Outbound Queue

Transactions in the Outbound Queue are actively being processed by THORChain
(i.e. not delayed).  A transaction will remain here until it it has made it
onto the associated blockchain, after which it is no longer THORChain's
responsibility.  (You can see these transactions in a blockchain explorer for
the associated blockchain.  [Blockchair] is a good general-purpose explorer!)

These transactions have an **AGE** field, which represents how long the
transaction has been in the Outbound Queue.  Transactions which have been in
this queue for longer than 30 minutes will have their **AGE** reset to 0,
followed by THORChain "re-attempting" internal processing.  This is a fail-safe
mechanism for edge cases (bugs), where for some reason a transaction gets
overlooked initially.

In normal cases, the Outbound Queue is processed quickly.  However, there are
some scenarios where the queue can become large (or "clogged").  In these
situations, it is common to see transactions with an abnormally large **AGE**
field.

Some example scenarios are:

- [Asgard vault churn], which is done periodically (usually every 2.5 to 3 days)
  - Transactions with a **Type** of `MIGRATE` are indicators churn is happening
- Gas estimation complications
- Anomalous conditions which require THORChain developer attention (and possibly
  a chain halt)

[9R THORChain Tracker]: https://track.ninerealms.com/
[Asgard vault churn]: https://docs.thorchain.org/thornodes/overview#churning
[Blockchair]: https://blockchair.com/
