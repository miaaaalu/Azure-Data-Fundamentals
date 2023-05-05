# Learning Notes

## Table of Contents
- [Relational databases](#relational-databases)
- [Non-relational databases](#non-relational-databases)
- [Key-value databases](#key-value-databases)
- [Document databases](#document-databases)
- [Graph databases](#graph-databases)


### Relational databases 
Relational databases are commonly used to store and query `structured data`. 

* The data is stored in tables that represent `entities`, such as customers, products, or sales orders. 

* Each instance of an entity is assigned a `primary key` that uniquely identifies it; and \
* these keys(PK) are used to reference the entity instance in other tables. For example, *a customer's primary key can be referenced in a sales order record to indicate which customer placed the order.*

This use of keys to reference data entities enables a relational database to be normalized

![Link Name](https://learn.microsoft.com/en-us/training/wwl-data-ai/explore-core-data-concepts/media/relational-database.png)  

### Non-relational databases
Non-relational databases are data management systems that `don’t apply a relational schema` to the data. Non-relational databases are often referred to as `NoSQL database`.

There are four common types of Non-relational database commonly in use.

**Key-value databases**
* each record consists of a `unique key` and an associated value, which can be in any format.

![Link Name](https://learn.microsoft.com/en-us/training/wwl-data-ai/explore-core-data-concepts/media/key-value-store.png)  

**Document databases**
* a specific form of key-value database
* value is a JSON document (which the system is optimized to parse and query)

![](https://learn.microsoft.com/en-us/training/wwl-data-ai/explore-core-data-concepts/media/document-store.png)  

**Graph databases**
* store entities as nodes with links to define relationships between them.

![](https://learn.microsoft.com/en-us/training/wwl-data-ai/explore-core-data-concepts/media/graph.png)  

