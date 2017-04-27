# bantudb
BantuDB: a "scale-out MongoDB" drop-in replacement that keeps your operations team happy.

Summary:
The developers love MongoDB, it's been working quite well as your product matured from idea to prototype and even into production.  But that single node, or single replica group production cluster of MongoDB is the reason the operations team is going nuts keeping things working.  Now, with BantuDB, you don't have to migrate to Cassandra.  You can keep your MongoDB investment intact and scale out with BantuDB.  A replicated and/or sharded MongoDB deployment is a outtage waiting to happen, BantuDB solves this problem.

How is BantuDB the same as MongoDB?
 - any exiting application that uses MongoDB 3.4+ should work without modification
 - use any MongoDB-compatible client library in any language
 - use any tool that works against 

How is BantuDB different?
 - supports global replication without the 
 
Details:

BantuDB speaks the MongoDB network protocol making it compatible with all clients, applications, tools, and frameworks that use MongoDB today.

Language: Java, not C:
While it supports all the features of MongoDB it is implemented in Java.

On-Disk Storage: B+Tree in AO/WAL with ACID Transactions and Recovery, not a LSM index.
While MongoDB servers have a plug-in storage layer with support for WiredTiger, RocksDB and others BantuDB uses a pure-Java storage engine called Oracle Berkeley DB Java Edition (ASLv2 licensed).  JE is a very mature and well tested implementation of a B+Tree stored in a a set of append-only (AO), Write-Ahead Log (WAL) files.  While other LSM storage engines are only recently adopting some transactional features JE has very mature support for ACID transactions and ARIES Recovery.

Replication: Where BantuDB stands apart from MongoDB is in how it manages data beyond a single server.  MongoDB has a replication protocol based on logical replication of operations.  Replica groups listen for and apply changes from the master as they are recorded by the master in the "oplog".  BantuDB takes a different approach, it uses the Berkeley DB High Availablity (HA) single-master multi-replica feature of Berkeley DB Java Edition.
