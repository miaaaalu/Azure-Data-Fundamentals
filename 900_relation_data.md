# Learning Notes

Table of Contents
1. [normalization](#normalization)
2. [SQL Statement](#sql-statement)
3. [Term](#term)


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
use DDL (Data Definition Language) statements to create, modify, and remove tables and other objects in a database (table, stored procedures, views, and so on).

| Statement | Description                                                                                             |
|-----------|---------------------------------------------------------------------------------------------------------|
| CREATE    | Create a new object, such as a table/view.                                          |
| ALTER     | Modify the structure of an object. For instance, altering a table to add a new column.                   |
| DROP      | Remove an object from the database.                                                                      |
| RENAME    | Rename an existing object.                                                                               |
> **Note:** The DROP statement is very powerful. When you drop a table, all the rows in that table are lost.

<div class="my-box">
Your message here.
</div>

## Term
- Entity: table
- attribute: column
- instance of entity: row

## 
