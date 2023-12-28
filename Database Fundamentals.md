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

## Storage Engine

Th engine provides an abstraction over reading & writing data to persistent storage, with the goal of *high throughput* & *low latency*. The design usually consists of:

- The underlying data structure to store items on disk.
- ACID transactions
- Cache:
	- to not have to read from disk every time. Buffered I/O
- API Layer - SQL/ document/ graph

We will focus on two common categories of data structures. Mutable & Immutable.

### Mutable B-Trees
To achieve good performance as the amount of data scales, we should aim to search for an item in at most logarithmic time.

A BST (binary search tree) provides a data structure where the search time is $\mathcal{O}(\log(n))$. the problem however is the *spatial locality*, whereby nodes are place randomly apart, so its likely the next node is far away on the disk. B-Trees aim to solve this by allowing for nodes with more than two children.



### Immutable LSM Tree

#### Bloom Filters

### Write Ahead log

### Isolation

## Distributed Systems

### Consistent Hashing

### Leaderless Replication

### Anti Entropy

