# Learning Notes
# Table of Contents

- [Explore file storage](#explore-file-storage)
- [Common File Format](#common-file-format)
  - [Delimited text files](#1-delimited-text-files)
  - [JavaScript Object Notation (JSON)](#2-javascript-object-notation-json)
  - [Extensible Markup Language (XML)](#extensible-markup-language-xml)
  - [Binary Large Object (BLOB)](#binary-large-object-blob)
  - [Optimized file formats](#optimized-file-formats)
    - [Avro](#avro)
    - [ORC (Optimized Row Columnar format)](#orc-optimized-row-columnar-format)
    - [Parquet](#parquet)

##  Explore file storage
The specific `file format` used to store data depends on a number of factors, including:
* The type of data being stored 
    * structured
    * semi-structured
    * unstructured
* The applications and services that will need to *read, write, and process the data.
* The need for the data files to be 
    * readable by humans
    * optimized for efficient storage and processing.

## Common File Format 

### 1. Delimited text files
Common Delimited data format 
* comma-separated values (CSV)
    * Fields delimited: `,` 
    * Rows are terminated by: `/` (new line)
* Tab-separated values (TSV)
    * Fields delimited: `space` / `tabs`

example (comma-delimited format)
```
FirstName,LastName,Email
Joe,Jones,joe@litware.com
Samir,Nadoy,samir@northwind.com
```

### 2. JavaScript Object Notation (JSON)
Json format file good for 
* structured data
* semi-structured data

* object, enclosed in braces: `{..}`
* collections, enclosed in square brackets: `([..])`
* attributes, represented by name: value pairs and separated by commas 
```json
{
  "customers":
  [
    {
      "firstName": "Joe",
      "lastName": "Jones",
      "contact":
      [
        {
          "type": "home",
          "number": "555 123-1234"
        },
        {
          "type": "email",
          "address": "joe@litware.com"
        }
      ]
    },
    {
      "firstName": "Samir",
      "lastName": "Nadoy",
      "contact":
      [
        {
          "type": "email",
          "address": "samir@northwind.com"
        }
      ]
    }
  ]
}
```
### Extensible Markup Language (XML)
XML largely been superseded by the less verbose JSON format, but there are still some systems that use XML to represent data. 

XML uses `tags` enclosed in angle-brackets (<../>) to define `elements` and `attributes`, as shown in this example:

```xml
<Customers>
  <Customer name="Joe" lastName="Jones">
    <ContactDetails>
      <Contact type="home" number="555 123-1234"/>
      <Contact type="email" address="joe@litware.com"/>
    </ContactDetails>
  </Customer>
  <Customer name="Samir" lastName="Nadoy">
    <ContactDetails>
      <Contact type="email" address="samir@northwind.com"/>
    </ContactDetails>
  </Customer>
</Customers>
```
### Binary Large Object (BLOB)
Ultimately, all files are stored as binary data (1's and 0's), but in the human-readable formats discussed above, the bytes of binary data are mapped to printable characters (typically through a character encoding scheme such as ASCII or Unicode). 

Some file formats however, particularly for unstructured data, store the data as raw binary that must be interpreted by applications and rendered. 

Common types of data stored as binary include images, video, audio, and application-specific documents.

### Optimized file formats
While human-readable formats for structured and semi-structured data can be useful, they're typically not optimized for storage space or processing. 

Over time, some specialized file formats that enable compression, indexing, and efficient storage and processing have been developed.

Some common optimized file formats you might see include `Avro`, `ORC`, and `Parquet`:

#### Avro 
a `row-based` format. Each record contains a header that describes the structure of the data in the record. This header is stored as JSON. 

Storage
* The data is stored as binary information. An application uses the information in the header to parse the binary data and extract the fields it contains. 

Benefit
* Avro is a good format for compressing data 
* minimizing storage and 
* network bandwidth requirements

Creation
* It was created by Apache.

####  ORC (Optimized Row Columnar format) 
organizes data into `columns` rather than rows. 

An ORC file contains stripes of data. Each stripe holds the data for a column or set of columns. A stripe contains an index into the rows in the stripe, the data for each row, and a footer that holds statistical information (count, sum, max, min, and so on) for each column.

Creation
* It was developed by HortonWorks for optimizing read and write operations in Apache Hive (Hive is a data warehouse system that supports fast data summarization and querying over large datasets). 

#### Parquet 
Parquet is another `columnar data format`.

A Parquet file contains row groups. Data for each column is stored together in the same row group. Each row group contains one or more chunks of data. 

A Parquet file includes metadata that describes the set of rows found in each chunk. An application can use this metadata to quickly locate the correct chunk for a given set of rows, and retrieve the data in the specified columns for these rows.

Benefit
* Parquet specializes in storing and processing nested data types efficiently. 
* It supports very efficient compression and encoding schemes.

Creation
* It was created by Cloudera and Twitter. 
