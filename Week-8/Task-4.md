### Violated ACID properties
1. Atomicity: because the transaction was partially completed
2. Consistency: because $500 was deducted but not added somewhere else
3. Durability: if changes weren't properly persisted before teh crash

### How to ensure each property
1. Atomicity: use transaction logs to undo imcomplete transactions
2. Consistency: put constraints and validate before committing
3. Isolation: use locking to prevent concurrent access problems
4. Durability: ensure changes are saved to non-volatile storage before committing

### Suppose two users try to transfer funds from the same account at the same time. Which ACID property would prevent data corruption?
- Isolation property prevents this using locking techniques

### Imagine the system crashes but recovers using a transaction log. Which ACID property makes this possible, and how?
- Durability
- Using transaction logs - records all changes so they can be undone if incomplete and redid if they weren't written to disk
