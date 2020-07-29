# Database Design

## CAP Theorem: Distributed Systems

Distributed data storage can only guarantee 2 of the following:

- Consistency: Every distributed node returns the same, most recent data
- Availability: Every non-failing node returns a response in a reasonable amount of time
- Partition Tolerant: A network partition is a rare occurrence in the system

- CP: CP systems sacrifice availability in the event of a network partition
- CA: CA systems sacrifice partitioning in favor of guaranteed consistency and availability, a single database is an example of this.
- AP: AP systems sacrifice consistency in the event of a rare event

A better summarization of CAP theorm:

- During a network partition (rare event) in a distributed system you must select either availability or consistency but not both
    - The response may either be slow or might be out of date

## ACID:

- Atomicity: all the transaction succeeds or none of it does, no partials
- Consistency: All data is consistent
- Isolation: Transactions occur in isolation and cannot be affected by any other transactions that have not yet been completed
- Durability: All transactions are permanent and cannot be undo unless done so by another transaction

## BASE:

typical of nosql databases who sacrifice some of the ACID properties for others like scale and resilience

- Basic Availability: The data appears to work most of the time
- Soft-state: Stores aren't write and mutually consistent all of the time
- Eventual Consistency: Store will eventually be consistent

## Types of Databases:

- Relational: ACID — MySQL, PostgreSQL, Oracle
- newSQL: horizontally scalable?
- Graph: ACID — neo4j
- Document: BASE — Mongo, CouchDB
- key Value: BASE — Redis, Dynamo
- Big Table: Cassandra, HBase, BigTable