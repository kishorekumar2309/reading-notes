# Distributed Data

Motivation for a distributed database:

- *Scalability*
- *Fault tolerance/high availability*
- *Latency*

# Scaling to Higher Load

- *vertical scaling* or *scaling up* / *shared-memory architecture* 
- *horizontal scaling* or *scaling out* / *shared-nothing architectures*

## Replication Versus Partitioning

*Replication*:

- Keeping a copy of the same data on several different nodes
- redundancy
- improve performance

*Partitioning*:

- Splitting a big database into smaller subsets
- different partitions can be assigned to different nodes (sharding)

