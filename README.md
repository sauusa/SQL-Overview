# SQL-Overview
An overview of SQL concepts and components.

## Components of SQL 

<img src="https://user-images.githubusercontent.com/67065902/99171443-1c53a500-26d7-11eb-86ba-f4fe6fad8389.jpg" />

An SQL - Structured Query Language is divided into 5 different categories:

1. DDL - Data Definition Langugae
2. DML - Data Manipulation Langugae
3. DQL - Data Query Language
4. DCL - Data Control Language
5. TCL - Transaction Control Language

### DDL - Data Definition Language

For creating and modifying Database objects such as table, indexes and users.
Examples:
  Create - To create DB or its objects(table, index, function, views, stored procedure and triggers)
  Drop   - To delete DB or its objects
  Alter  - To alter the structure of the DB (like deleting a column, or adding a constraint)
  Truncate - To remove all the records froam a table (& not table itself)
  Comment - To add comments to the data dictionary 
  Rename  - To rename as object existing in DB
  
### DDL - Data Manipulation Language

For inserting, modifying and deleting records in DB tables.
Examples:
    Insert - To insert data into a table
    Update - To update data existing data within a table
    Delete - To delete records from a DB table
    
### DQL - Data Query Language

  or Data Retrival Language
  Select - To rerive data from the DB.
  
### DCL - Data Control Langugae

  Deals with rights and permission , to control the aceess of data.
  Example:
  Grant   - To give priviledges to users to access database
  Revoke  - To withdraw priviledges given by Grant command

### TCL - Transaction Control Langugage 

  For controling the transaction within the DB.
  Example:
  Commit   - To commit a transaction
  Rollback - To rollback the transaction in case of errors
  SavePoint - To set a save point within a transaction
  SetTransaction - To specify characteristics for the transaction
  
  
