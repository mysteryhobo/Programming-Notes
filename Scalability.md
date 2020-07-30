# Scalability

# Traffic Scaling:

## 1. More Servers and a Load Balancer:

Routes the clients requests to the best suited web server 

Horizontal scaling

Does health checks to test server availability

Auto scaling instances to adapt to spikes / waves of traffic

# Database Scaling:

## 1. Efficiency:

Improve database with indexes and performance testing improvements

## 2. Vertical Scaling (A Bigger machine)

Faster/Larger/Newer Machine (More Processing)

Improved Memory with caching: (Caching Note)

## 3. Sharding (Partitioning): (Data Storage Scaling)

Allows you to scale the amount of data stored in your system.

The act of splitting up a database into different parts while maintaining its schema

- Horizontal: splitting apart different rows of a table
    - effective when queries tend to return a subset of rows that are often grouped together
- Vertical: splitting apart different columns of a table
    - Effective when queries tend to return only a subset of columns

## 4. Replication: (Read and Write Scaling)

Allows you to scale of read and writes in a system.

Duplicates of databases (and their data)

- Master / Slave: one master that gets written to and forwards the writes to multiple slave databases. Good for when there are more reads than writes
- Multi-master: multiple master nodes that can be written to