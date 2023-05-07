# Learning Notes

- [Normalization](#normalization)
- [Database Objects](#database-objects)
  - [View](#view)
  - [Stored Procedure](#stored-procedure)
  - [Index](#index)
- [SQL Statement](#sql-statement)
  - [DDL statements](#ddl-statements)
  - [DCL statements](#dcl-statements)
  - [DML statements](#dml-statements)
- [Term](#term)

## normalization
Use in: 
- schema design process

benefit:  
- minimizes data duplication. 
    - e.g. For example, to change a customer's address, you need only modify the value in a single row.
- enforces data integrity

purpose for: 
1. Separate each `entity` into its own table.
2. Separate each `discrete attribute` into its own column.
3. Uniquely identify each entity instance (row) using a `primary key`.
4. Use `foreign key` columns to link related entities.

Example 

non-nomarlised            |  nomarlised
:-------------------------:|:-------------------------:
![](https://learn.microsoft.com/en-us/training/wwl-data-ai/explore-relational-data-offerings/media/unnormalized-data.png)  |  ![](https://learn.microsoft.com/en-us/training/wwl-data-ai/explore-relational-data-offerings/media/normalized-data.png)

## Database Objects 
### View 
A view is a virtual table based on the results of a SELECT query. 

```SQL
CREATE VIEW Deliveries
AS
SELECT o.OrderNo, o.OrderDate,
       c.FirstName, c.LastName, c.Address, c.City
FROM Order AS o JOIN Customer AS c
ON o.Customer = c.ID;
```
### Stored procedure
 the following stored procedure could be defined to change the name of a product based on the specified product ID.

```sql
-------------------------------------------
---Create stored procedure RenameProduct---
-------------------------------------------
CREATE PROCEDURE RenameProduct
	@ProductID INT,
	@NewName VARCHAR(20)
AS
UPDATE Product
SET Name = @NewName
WHERE ID = @ProductID;

-------------------------------------------
---------Execute stored procedure----------
-------------------------------------------
EXEC RenameProduct 201, 'Spanner';
```


### Index
- When you create an index in a database, you specify a `column` from the table.
- For a table containing few rows, using the index is probably not any more efficient - the query optimizer will ignore the index). 
- However, when a table has many rows, indexes can dramatically improve the performance of queries.
- indexes aren't free. An index `consumes storage space`, and each time you insert, update, or delete data in a table, the indexes for that table must be maintained. This additional work can slow down insert, update, and delete operation

```sql
CREATE INDEX idx_ProductName
ON Product(Name);
```

## SQL Statement
### DDL statements 
use to create, modify, and remove `tables and other objects` in a database, including
- table
- stored procedures 
- views 
- ...

Common DDL statements:
| Statement | Description                                                                                             |
|-----------|---------------------------------------------------------------------------------------------------------|
| CREATE    | Create a new object, such as a table/view.                                          |
| ALTER     | Modify the structure of an object. For instance, altering a table to add a new column.                   |
| DROP      | Remove an object from the database.                                                                      |
| RENAME    | Rename an existing object.                                                                               |
> **Note:** The DROP statement is very powerful. When you drop a table, all the rows in that table are lost.

### DCL statements 
to `manage access` to objects in a database by granting, denying, or revoking permissions to specific users or groups. For example:
| Statement | Description                                           |
|-----------|-------------------------------------------------------|
| GRANT     | Grant permission to perform specific actions.         |
| DENY      | Deny permission to perform specific actions.          |
| REVOKE    | Remove a previously granted permission.               |

### DML statements 
-  use DML statements to `manipulate the rows`in tables.
- to retrieve (query) data, insert new rows, or modify existing rows. You can also delete rows if you don't need them anymore. For example: 
    - SELECT
    - UPDATE 
    - INSERT 
    - DELETE 

## Term
- Entity: table
- attribute: column
- instance of entity: row
- DDL: Data Definition Language
- DCL: Data Control Language
- DML Data Manipulation Language

| Term                   | Definition                                      |
|------------------------|------------------------------------------------|
| Entity                 | Table                                          |
| Attribute              | Column                                         |
| Instance               | Row                                            |
| DDL| Data Definition Language |
| DCL| Data Control Language|
| DML| Data Manipulation Language |
