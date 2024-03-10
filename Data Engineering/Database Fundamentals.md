---
created: 2023-08-26 16:21
tags:
  - DataEngineering
  - Database
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

![[BST.png]]

On each page read from disk, we iterate over multiple nodes sequentially from memory which reduces the amount of data we need to read from disk.

A B+ Tree takes B-Trees a step further, where the final leaf nodes hold the values and other nodes just the keys. Hence when fetching data from disk, we have many more keys to compare.

B-trees, to be spaced optimised, sometimes need to reclaim space due to data framgmentation:
- Big value updates - might overwrite data of the next node, so the tree re-locates the item.
- Small value updates - leaves a hole at the end
- Deletes - leaves a hole

the process that takes care of space reclamation and page rewrites is called a *vacuum*, *compaction*, *page defragmentation* and *maintenance*.

B-Trees are most commonly used as the underlying data structure of an index (*postgreSQL* does this), or all data (as in *DynamoDB*).

### Immutable LSM Tree

If you only append data to a file, the disk needle doesn't need to move as much to the next position where data will be written. On heavy workload this can be beneficial, and LSM's take advantage of this.

The append only data structure LSM *Log Structured Merge tree* is used by many modern database engines such as: *RocksDB*, *Cassandra*, *ScyllaDB*.

The general idea is to buffer writes to a data structure in memory, one that is easy to iterate (*AVL tree*, *Red Black tree*, *Skip List*) and once it reaches some capacity, flush it to a file called SSTable (*Sorted String Table*).  This table stores sorted data, letting us use binary search and sparse indexes to lower disk I/O.

To maintain durability, the action of writing data to memory is stored in a WAL *Write-Ahead Log* so that the program can reset the state if there is a shutdown or crash. 

Deletions are also appended in the same way a write would be, but it simply holds a tombstone instead of a value. Tombstones are then deleted in the compaction process. 

Reading data is where we introduce some unwanted latency. For a given key, if not found in the in memory data structure we must search through all the SSTables with lookup time complexity:

$$\log( \text{num files} * \text{table size}) < \text{num files} * \log(\text{table size})$$

And so compaction, combining small SSTables into a big one, whilst removing all tombstones significantly speeds up this lookup process. This process can be implimented with binary heap/priority queues. 

Optimising this further, we want to consider when and on which SSTables to compact. *RocksDB* implements a Levelled Compaction, where newly flushed SSTables enter level0, and once a configured N number of files are create in that level, they are compacted and the new files in promoted to the next level. 

#### Bloom Filters

A probabilistic set data structure that lets you efficiently check whether an item doesn't exist in a set. A bloom filter set has space complexity $\mathcal{O}(\log(n))$

### Write Ahead log

### Isolation

## Distributed Systems

### Consistent Hashing

### Leaderless Replication

### Anti Entropy

