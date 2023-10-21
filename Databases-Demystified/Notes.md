## Databases Demystified

### Introduction to databases 

There are different types/paradigms of DBs, specific to different user cases; with different types of pros and cons (e.g. optimized for a specific use) 

* Analytical Vs Transactional
  * Analytical: Analyzing large amounts of data to answer business questions through analysis (e.g. Redshift, Snowflake, BigQuery, etc.)
  * Transactional: Managing state for other software applications - you keep track which user is logged in/logged out/ orders shipped or not shipped (e.g. PostgreSQL, mySQL, Oracle DB, etc.) 

* Relational Vs Non-Ralational 
  * Relational DB: Data are stored in independent tables, which can be ‘joined’ together e.g. MySQL, PostgreSQL, Redshift, BigQuery 
  * Non-Relational: Data stored in one big block (“document”) without a fixed schema. In one document you may have a set of attributes, while in another document another set  e.g. MongoDB, Redis, etc. 

* Distributed Vs Single-Node
  * Distributed: Data are distributed across multiple computers that make up the database (i.e. different locations)
  * Single-Node: Entire DB runs on a single computer 

* In-Memory Vs On-Disk: this describes how data are stored or accessed by the computer:
  * In-Memory: The entire database is loaded into RAM  (e.g. Redis, MemSQL, etc.)
  * On-Disk: DB is saved on hard-disk storage - ability to save more data, since computers tend to have more hardware space than RAM PostgreSQL, MySQL, data warehouses, etc.

### Analytical Vs Transactional

#### Analytical workloads 

* Processing large amounts of information for creating aggregates
* (Almost) read-only queries: read data out of the DB 
* Occasionally batch-write data loads, e.g. moving data from a data system to a DB / DW
* Supporting complex queries with multiple steps of data processing, join conditions, and filtering
* Highly variable ad-hock queries, many of which may only be run once, ever

#### Transactional workloads

* Manipulating one "object" at a time (e.g. user, order, patient; depending on the system)
* 
