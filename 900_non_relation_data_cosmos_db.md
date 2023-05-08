# Learning Note
## Table of Contents

- [Azure Cosmos DB for NoSQL](#azure-cosmos-db-for-nosql)
- [Azure Cosmos DB for MongoDB](#azure-cosmos-db-for-mongodb)
- [Azure Cosmos DB for PostgreSQL](#azure-cosmos-db-for-postgresql)
- [Azure Cosmos DB for Table](#azure-cosmos-db-for-table)
- [Azure Cosmos DB for Apache Cassandra](#azure-cosmos-db-for-apache-cassandra)
- [Azure Cosmos DB for Apache Gremlin](#azure-cosmos-db-for-apache-gremlin)

![Azure Cosmos DB](https://learn.microsoft.com/en-us/training/wwl-data-ai/explore-non-relational-data-stores-azure/media/azure-cosmos-db.png)

## Azure Cosmos DB for `NoSQL`
- **for NoSQL**: Microsoft’s native non-relational service for working with the document data model.
- **Data Management**: It manages data in JSON document format.
- **SQL Syntax**: Despite being a NoSQL data storage solution, it uses SQL syntax to work with the data.


Input
```sql
--A SQL query for an Azure Cosmos DB database containing customer data might look similar to this--
SELECT *
FROM customers c
WHERE c.id = "joe@litware.com"
```
Output
```JSON
// The result of this query consists of one or more JSON documents, as shown here//
{
   "id": "joe@litware.com",
   "name": "Joe Jones",
   "address": {
        "street": "1 Main St.",
        "city": "Seattle"
    }
}
```

## Azure Cosmos DB for `MongoDB`
MongoDB is a popular open source database in which data is stored in Binary JSON (BSON) format. 

For example, the following query uses the find method to query the products collection in the db object:

```JavaScript
db.products.find({id: 123})
```
The results of this query consist of JSON documents, similar to this:

```JSON
{
   "id": 123,
   "name": "Hammer",
   "price": 2.99
}
```

## Azure Cosmos DB for `PostgreSQL`

for example you might define a table of products like this:

| ProductID | ProductName  | Price |
| --------- | ------------ | ----- |
| 123       | Hammer       | 2.99  |
| 162       | Screwdriver  | 3.49  |

Input
```SQL
SELECT ProductName, Price 
FROM Products
WHERE ProductID = 123;
```

Output
| ProductName | Price |
| ----------- | ----- |
| Hammer      | 2.99  |


## Azure Cosmos DB for `Table`
Azure Cosmos DB for Table is used to work with data in key-value tables, similar to Azure Table Storage. 

Example - Customer Table

| PartitionKey | RowKey | Name        | Email               |
| ------------ | ------ | ----------- | ------------------- |
| 1            | 123    | Joe Jones   | joe@litware.com     |
| 1            | 124    | Samir Nadoy | samir@northwind.com |

Input
```text
You can then use the Table API through one of the language-specific SDKs to make calls to your service endpoint to retrieve data from the table. 
```

Output
```text
https://endpoint/Customers(PartitionKey='1',RowKey='124')
```

## Azure Cosmos DB for `Apache Cassandra`
Azure Cosmos DB for Apache Cassandra is compatible with Apache Cassandra, which is a popular open source database that uses a column-family storage structure. Column families are tables, similar to those in a relational database, with the exception that it's not mandatory for every row to have the same columns.

Example - Employees table

| ID  | Name      | Manager    |
| --- | --------- | ---------- |
| 1   | Sue Smith |            |
| 2   | Ben Chan  | Sue Smith  |

Output

```SQL
--Cassandra supports a syntax based on SQL, so a client application could retrieve the record for Ben Chan like this--

SELECT * FROM Employees WHERE ID = 2
```

### Azure Cosmos DB for `Apache Gremlin`
Azure Cosmos DB for Apache Gremlin is used with data in a graph structure; in which entities are defined as vertices that form nodes in connected graph. Nodes are connected by edges that represent relationships, like this:

Example - Employee & Department 

*The example in the image shows two kinds of vertex (employee and department) and edges that connect them (employee "Ben" reports to employee "Sue", and both employees work in the "Hardware" department)*

![A graph showing employees and departments and the connections between them](https://learn.microsoft.com/en-us/training/wwl-data-ai/explore-non-relational-data-stores-azure/media/graph.png)

Input
```sql
--add a new employee named Alice that reports to the employee with ID 1 (Sue)--
g.addV('employee').property('id', '3').property('firstName', 'Alice')
g.V('3').addE('reports to').to(g.V('1'))
```
Output
```sql
--returns all of the employee vertices, in order of ID--

g.V().hasLabel('employee').order().by('id')
```

## Resource 
[Identify Azure Cosmos DB APIs
](https://learn.microsoft.com/en-us/training/modules/explore-non-relational-data-stores-azure/3-cosmos-db-apis)
