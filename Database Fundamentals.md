---
created: 2023-08-26 16:21
tags:
  - Statistics
---


# Database Internals

This page aims to summarise the `Databse Internals` and `Designing Data-intensive Applications` highlighting the fundamentals underlying modern databases.

## Transaction Processing & recovery

Almost all databases strive to guarantee what are called `ACID` transactions namely: *Atomicity*, *Consistency*, *Isolation*, *Durability*.

**Atomicity**:
> All steps associated with a transaction either execute successfully or none of them do. Each transaction can either commit (make all operations visible) or abort (roll back all transaction effects that haven't been made visible).

**Consistency**:
> Application-specific guarantee; a transaction should only take the database from one valid state to another valid state. This is a weakly defined property, and is controlled by the user.

**Isolation**:
> Defines when the changes to the database state may become visible. Essentially multiple concurrently executing transactions should be able to run without interference and with the same outcome as running them sequentially. 

**Durability**:
> Once a transaction has been committed, the database state must be persisted to disk and able to survive power outages, system failures & crashes.



