# 5. Replication

*Replication* means keeping a copy of the same data on multiple machines that are connected via a network

- To keep data geographically close to your users (latency)
- Allow system to continue working even if some of its parts have failed
- To scale out the number of machines that can serve read queries (throughput)

Difficulty in replication lies in handling *changes* to replicated data.

Three popular algorithms for replicating changes between nodes: 

1. *single-leader*
2. *multi-leader*
3. *leaderless*

Types of replication:

1. *synchronous*
2. *asynchronous*

# Leaders and Followers

*replica* - Each node that stores a copy of the database

*Leader-based replication* (*active/passive* or *master–slave replication*):

- *leader* - processes write requests from client, writing it to the local storage
- *followers* (*read replicas*, *slaves*, *secondaries*, or *hot standbys*) - receives the *replication log* or *change stream* from leader and updates its local copy
- query - leader / follower, write - only leader

## Synchronous Versus Asynchronous Replication

In *synchronous* the leader waits until follower confirms, but in *asynchronous* the leader sends the message, but doesn’t wait for a response from the follower.

Advantages of Synchronous:

- follower is guaranteed to have an up-to-date copy of the data that is consistent with the leader
- in case if leader fails, the data is still available on the follower

Disadvantages of Synchronous:

- the write cannot be processed, if the follower does not respond
- leader must block all writes and wait until the replica is available again

***semi-synchronous***:

- *one* of the followers is synchronous, and the others are asynchronous
- if the synchronous follower becomes unavailable or slow, one of the asynchronous followers is made synchronous

Completely Asynchronous:

- disadvantage - if the leader fails and is not recoverable, any writes that have not yet been replicated to followers are lost
- advantage - leader can continue processing writes, even if all of its followers have fallen behind



