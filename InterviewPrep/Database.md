DBs Summaries

* CouchDB: Written in Erlang, schema free, can define MapReduce functions
* MongoDB: is not done over HTTP,  no style views, master/slave replication consistent, partition-tolerant. Always get back the same data. Documents are partitioned through sharing, each partition will have a subset of the records, shards are created based on the key you choose. database(for app)/collections(use for grouping records)/records
* Cassandra: not over HTTP, cross between key-value/tabular DB available, partition-tolerant
* Riak: Written in Erlang like CouchDB, available, partition-tolerant database, similar to Lucene full text search engine. Mapreduce, key filters
* Redis: native drivers, key/value store, master/slave replication, always the same data can store lists, sets(non-repeating), hashes of strings

DB partitioning: uses a consistent method, like a hash function  
Horizontal partitioning: diff rows on diff partitions (key/value, document, tabular)  
Vertical partitioning: diff cols on diff partitions (tabular)  


* Consistency: DB clients see the same data, even with concurrent updates.
* Availability: all DB clients are able to access some version of data.
* Partition tolerance: DB can be split over multiple servers.

CAP Theorem: consistency, availability, partition tolerance
* relational: consistency and availability
* nosql: partition-tolerance
* couchdb: AP

SQL: relational dbs are usually table-based. Uses rows/columns  
noSQL: records can have their own unique fields, can nest values.


NoSQL:

* document stores, usually in XML or JSON. Individual documents have unique structures.
* key/value stores, used along relational DBs for caching
* BigTable/tabular, each row can have different set of columns, designed for large numbers of columns in each row, and each row is typically versioned.
* Graph databases: best for interconnected nodes
* Object DB: tight integration with OOLs, persistence layer, store objects directly. link objects through pointers

NoSQL vs SQL

* customizable fields
* caching layer
* binary files
* serve full web apps

Referential Integrity

DB Normalization

* 1st Normal Form: Every column/field contains only one value.
* 2nd Normal Form: Only have things that are not dependent on the primary key (like course and course title). Issue with Composite keys.
* 3rd Normal Form: All non-keys should not be depended on other non-keys. (Room number and capacity)

Clustered vs non-clustered index

* Clustered: Refers to how the table is sorted. Usually the primary key. Secondary value is needed if the clustered index is not the primary key.
* Clustered Index
    * Only one per table
    * Faster to read than non clustered as data is physically stored in index order
* Non Clustered Index
    * Can be used many times per table
    * Quicker for insert and update operations than a clustered index
* Both types of index will improve performance when select data with fields that use the index but will slow down update and insert operations.
* Because of the slower insert and update clustered indexes should be set on a field that is normally incremental ie Id or Timestamp.


Multithreaded Databases
* pessimistic locking: lock everything that is being accessed
* optimistic locking: dirty reads that roll back transactions. 

Comparing DB Technologies

* MongoDB
	* C++, SQL properties, Sharding, 
	* Best used: 
* Riak
	* Erlang, C, some JS, transitioning to LevelDB
	* Fault tolerance, HTTP/REST or custom library
	* Map/Reduce in JS/Erlang
	* Fill-text search, indexing, querying with Riak Search
	* Masterless multi-site replication