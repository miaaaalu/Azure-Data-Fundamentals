# Learning Notes
- [Normalization](#normalization)
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
