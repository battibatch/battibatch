# Designing Data-Intensive Applications 
Kleppmann
2017

## Chapter 01: Reliable Scalable and Maintainable Apps
Apps today are data intensive instead of Compute intensive
- they need to store data so they or another app can find it (DB) 
- Remember the result fo expensive operation (cache) 
- ALlow users to search data by keyword of filter it in various ways (search indexes) 
- send messages to another process to be handled async (stream)
- periodically crunch a large amount of accumulated data (batch)

![alt text](image.png)

during design, tricky questions
- how do you ensure data remains correct and complete, even during errors?
- how do you provide good performance, even when degraded
- how do you scale
- what does good API look like

Reliability
- software expectations
    - app performs the functions
    - it can tolerate the user making mistakes or used in unexpected ways
    - performs good enough, despite load
    - prevents unauthz and abuse
- fault != failure
    - fault is 1 component deviating from its spec
    - failure is system as a who stops
    - increase rate of faults to test a fault tolerant system
    - Hardware faults
        - Disk crash, RAM, power outage
        - Mean time to failure (MTTR)
        - used to solve bu adding redundancy, but with cloud scale, it is expensive
    - software errors
        - bugs cause crash
        - runaway processes 
        - service becomes unresponsive
        - cascading failures 
    - Human errors
- How to design for reliability
    - minimized opportunities for errors: well designed abstractions, APIs, interfaces without over designing forcing human to work around
    - decouple
    - add sandboxes for experiments
    - Test thoroughly
    - allow for easy recovery
    - detailed and clear monitoring
    - training


Scalability
- reliable today doesn't mean reliable tomorrow
- ability to cope with increased load
- Describing Load (load parameters)
    - depends on the architecture of ths system
        - requests per sec, ration of reads to writes, num active users, etc.
        - it is what matters, or the bottleneck
- describing performance
    - with load described, you investigate what happens when load increases
        - when a load param increases and resources are unchanged, how is system affected?
        - when load param increases, how do resources need to increase to prevent performance drop
    - throughput: number of items per sec
    - response time: time between request and response
        - common to look for averages, then median
- Approach to cope with load
    - horizontal scaling - add machines
    - vertical scaling - add resources to the same machine
    - often a few medium/large machines is better for cont and load than many small machines
    - auto or elastic scaling
    - Architecture depends on the application
        - 100k requests/s each 1kb is different than 3 requests/s of 2GB even though throughput is the same.

Maintainability
- Design software for maintainability
    - Operability: easy for ops to keep system running
        - provide good visibility into runtime behavior
        - prod good support for automation and integration
        - avoid dependency on individual machines
        - provide good docs
        - provide good defaults
        - self healing
        - predictable
    - simplicity: easy for new engineers to understand
        - add good abstractions
    - Evolvability: easy to change
        - refactor as needed

## Chapter 02: Data Models and Query Languages
data models are most important part of software dev
Relational vs Document models
- NoSQL and document arrived to b/c
    - need more scalability
    - open sources
    - specialized query operations
    - too much restriction in relational
- Object oriented apps require transition layers between objs, adding code. This is called impedance mismatch
    - adding JSON models reduced the mismatch
    - try and avoid duplicated relationships
        - many to 1; many to many 
        - removing the duplications is called normalization
        - normalization doesn't fit well in Document DBs
- Document is hierarchial model wrt storing nested records (1-to-many)
- Today the data in the app helps determine which model is used.
    - document has poor joins, but good flexibility
    - Relational has great structure and joins, but schema updates are hard
    - Document typically has data locality for performance
    - modern relational support JSON and XML now
    - some documents support joins
Query languages
- declarative
    - typically more concise and readable
    - lend to better parallel
- Imperative
    - 
- MapReduce Querying
    - somewhere between declarative and imperative

Graph-like Data models
- good for many-to-many relationships
- graphs have 2 kinds of objects
    - vertices (also known as nodes or entities)
    - edges (also known as relationships or arcs)
- examples of data modeled as a graph
    - social graphs- vertices are people, edges indicate which people know each other
    - web graph - vertices are webpages, edges indicate links to other pages
    - road or rail networks - vertices are junctions, edges are road/rails between them
- not limited to homogeneous data
- many ways to structure data in a graph
    - property graphs
        - Graph Queries in SQL: can be done, but hard
        - Triple-Stores - same as property graphs, but different words
        - SPARQL is a query language for Triple stores

## Chapter 03: Storage and Retrieval
Data structures that power your Database
- Key value data (dictionaries)
- Hash tables
- Sorted String Tables (SSTables)
- Log Structure Merge Trees (LSM Trees)
    - have lower write amplification
    - can be compressed better
    - compactions will impact performance
    - becoming increasingly popular
- B Trees
    - LSM faster for writes; B-trees faster for reads
    - B trees must write everything twice, once to write ahead and once to the tree
- Others
    - primary index
    - secondary index
    - multi column index
    - full-text search and fuzzy indexes

Transaction processing or Analytics
![alt text](image-1.png)
- Data warehousing
![alt text](image-2.png)
- Stars and Snowflakes: schemas for analytics
![alt text](image-3.png)

Column-Oriented Storage
- tables may be 100s of columns wide, but often, we only need 4-5 of them.
- idea here is don't store all the values from from 1 row together, but store all the values from each column together. If each column is a file, then you only need to read the files for the columns that you need.
- Can be compressed too
- Sort order doesn't matter; usually stored in the order they were written
    - then can be ordered: C-store
- Writing uses LSM-trees
- Data cubes and Materialized Views

## Chapter 04: Encoding and Evolution
Formats for encoding data
- in mem, data in objects, struct, lists, arrays, hash tables, trees, etc.
- when written to a file, encoded i.e. JSON]
- translation is needed
- Each language has specific in memory formats, but prefer standardized encodings
    - JSON, XML, CSV: all textual formats
        - subtle problems
            - JSON cannot distinguish between integer and float
            - bad for binary strings
            - JSON rarely uses schema
            - No schema for CSV
- when data is in terabytes, it really matters, binary encoding like messagepack can help: 
![alt text](image-4.png)
- Thrift and Protocol Buffers
    - binary encoding libs based on the same principle
    - required a schema for data that is encoded
    - schema evolves over time via field tag
    - add new fields to the schema
- Avro
    - another binary encoding
    - uses a schema, has 2 dif languages: 1 for human editing (IDL); 1 for machine (based on JSON)
    - no tag numbers
    - schema evolves with writes and reader schemas - they do not have to be the same. Avro resolve
    - null is not valid type; 
    - This enables dynamic generated schemas

Modes of Dataflow
- Dataflow through Databases
- Dataflow via service calls
- Dataflow via async messages passing

## Chapter 05: Replication

Leaders and Followers
- 


## Chapter 06: Partitioning

## Chapter 07: Transactions

## Chapter 08: The Trouble with Distributes systems

## Chapter 09: Consistency and Consensus

## Chapter 10: Batch Processing

## Chapter 11: Stream Processing

## Chapter 12: The Future of Data Systems


