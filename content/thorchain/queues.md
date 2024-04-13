# Queues

THORChain has two (2) kinds of queues that pertain directly to outbound
transactions: the Scheduled Queue, and the Outbound Queue.

You can see both of these queues using the [9R THORChain Tracker].

## Scheduled Queue

Transactions in the Scheduled Queue are intentionally delayed due to
THORChain's [outbound throttling](delays.md) security mechanism.

Transactions in this queue have an **ETA** field, which is the amount of time
remaining until your transaction is moved into the Outbound queue.

The Scheduled Queue data comes directly from the `/thorchain/queue/scheduled`
[THORNode API endpoint][1].

## Outbound Queue

Transactions in the Outbound Queue are actively being processed by THORChain
(i.e. not delayed).  When a transaction enters this queue, it's assigned to an
[Asgard vault], which then signs the transaction and generates the actual
outbound transaction (on the destination blockchain).  Once this process has
completed, the transaction is no longer THORChain's responsibility.

These transactions have an **AGE** field.  This field represents how long a
transaction has been assigned to an As vault, but not yet signed or having its
outbound transaction (on the destination blockchain) completed successfully.
If neither of the latter scenarios have not completed within 30 minutes (or
more precisely, 300 blocks ([SigningTransactionPeriod][3])), the transaction
will be reassigned to a different Asgard vault and **AGE** reset to 0 minutes.

In normal cases, this queue is processed quickly.  However, there are some
scenarios where the queue can become large (or "clogged").  In these
situations, it is common to see transactions with an abnormally large **AGE**
field, or transaction which seem "stuck" (going from 30m to 0m; see above).

Some example scenarios where this might happen:

- [Asgard vault churn][2], which is done periodically (usually every 2.5 to 3 days)
  - Transactions with a **Type** of `MIGRATE` are indicators churn is happening
- Gas estimation quirks or bugs (such as those fixed in [THORNode v1.131.0][4])
- Anomalous conditions which require THORChain developer attention (and possibly a chain halt)

The Outbound Queue data comes directly from the `/thorchain/queue/outbound`
[THORNode API endpoint][1].

[1]: https://thornode.ninerealms.com/thorchain/doc
[2]: https://docs.thorchain.org/thornodes/overview#churning
[3]: https://thornode.ninerealms.com/thorchain/constants
[4]: https://gitlab.com/thorchain/thornode/-/tags/v1.131.0
[9R THORChain Tracker]: https://track.ninerealms.com/
[Asgard vault]: https://thorchain-university.medium.com/under-the-hood-asgard-vaults-tss-and-node-churns-4767f3a5624b
