1. problems without locks:
- both could see the book as available simultaneously
- both could mark it as borrowed
- result: One copy appears to be borrowed twice (lost update problem)

2. lock types for each step:

i. Shared lock </br>
ii. Exclusive lock </br>
iii. Exclusive lock maintained </br>

3. holding locks until completion:
- prevents other transactions from seeing intermediate states
- maintains isolation property
</br>
Timestamp Ordering Algorithm:

- Assigns each transaction a unique timestamp
- Tracks read/write timestamps for each data item
- Ensures transactions execute as if in timestamp order
- If a transaction tries to read a value written by a younger transaction, it's aborted
- If a transaction tries to write a value read by a younger transaction, it's aborted
- Provides serializability without locking, but may cause more aborts
