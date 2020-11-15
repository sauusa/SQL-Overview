# SQL-Overview
An overview of SQL concepts and components.

## Components of SQL 

<img src="https://user-images.githubusercontent.com/67065902/99171443-1c53a500-26d7-11eb-86ba-f4fe6fad8389.jpg" />

An SQL - Structured Query Language is divided into 5 different categories:

  1. <b>DDL</b> - Data Definition Langugae
  2. <b>DML</b> - Data Manipulation Langugae
  3. <b>DQL</b> - Data Query Language
  4. <b>DCL</b> - Data Control Language
  5. <b>TCL</b> - Transaction Control Language

### DDL - Data Definition Language

For creating and modifying Database objects such as table, indexes and users.

  Examples:
  
  <b>Create</b> - To create DB or its objects(table, index, function, views, stored procedure and triggers)
  
    CREATE DATABASE sample_db;
    
    CREATE TABLE if not exist sample_table (field_1 varchar(50) PRIMARY KEY, field_2 int NOT NULL, field_3 numeric(5,2));
      
  <b>Drop</b>   - To delete DB or its objects
  
     DROP DATABASE if exist sample_db;
     
     DROP TABLE if exist sample_table [RESTRICT | CASCADE];
     
   <i>CASCADE => Automatically drop objects that depend on the table (such as views).</i>
   
   <i>RESTRICT => Refuse to drop the table if any objects depend on it. This is the default.</i>
     
  <b>Alter</b>  - To alter the structure of the DB (like deleting a column, or adding a constraint)
  
    ALTER TABLE table_1 DROP COLUMN field_1 [ CASCADE | RESTRICT ];
    
    ALTER TABLE table_1 add constraint constraint_name FOREIGN KEY (field_1) REFERENCES table_2(field_1);
    
  <b>Truncate</b> - To remove all the records froam a table (& not table itself) -faster than Delete
  
    TRUNCATE TABLE big_table CASCADE;
    
  <b>Comment</b> - To add comments to the data dictionary 
  
    COMMENT ON TABLE my_table IS "This is My Table";
    
    COMMENT ON TABLE my_table IS NULL;
    
  <b>Rename</b>  - To rename as object existing in DB
  
    ALTER TABLE table_1 RENAME COLUMN notes TO sample_notes;
    
  
### DDL - Data Manipulation Language

  For inserting, modifying and deleting records in DB tables.

  Examples:
  
  <b>Insert</b> - To insert data into a table
  
    INSERT INTO movie (movie_id, title, director_id, release_date, category)
    VALUES ('T_101', 'Titanic', 105, '1997-12-14', 'Drama');
    
  <b>Update</b> - To update data existing data within a table
  
    UPDATE employees SET salary = salary + (salary * .5)
     WHERE employees.dept_no = 40 AND employees.grade IN (20,30,40);
  
  <b>Delete</b> - To delete records from a DB table
  
    DELETE FROM films WHERE category = 'Musical2';
    
    
### DQL - Data Query Language

  or Data Retrival Language
  
  <b>Select</b> - To rerive data from the DB.
  
    SELECT * from movie;
    
    SELECT DISTINCT (category) FROM movie;
    
    SELECT film_id, title, release_date
    FROM films WHERE extract(year from release_date) between 1995 and 2000;
    
    SELECT d.first_name, d.last_name, sum(r.domestic_takings + r.international_takings) as sum_rev
      FROM directors d, movie m, revenues r
	   WHERE d.director_id = m.director_id
	     AND m.movie_id    = r.movie_id
	     AND r.domestic_takings is not null
	     AND r.international_takings is not null
	   GROUP BY d.first_name, d.last_name
     HAVING sum_rev > 500
	   ORDER BY sum_rev desc
	   LIMIT 10;
  
### DCL - Data Control Language

  Deals with rights and permission , to control the aceess of data.
  
  Example:
  
  <b>Grant</b>   - To give priviledges to users to access database
  
    GRANT INSERT ON movie TO PUBLIC;
  
    GRANT ALL PRIVILEGES ON revenue TO saurabh;
    
    GRANT admins TO ffid012345;
    
  <b>Revoke</b>  - To withdraw priviledges given by Grant command
  
    REVOKE INSERT ON movie FROM PUBLIC;
    
    REVOKE ALL PRIVILEGES ON revenue FROM saurabh;
    
    REVOKE admins FROM ffid012345;

### TCL - Transaction Control Langugage 

  For controling the transaction within the DB.
  
  Example:
  
  <b>Commit</b>   - To commit a transaction
  
    <Perform a transaction>
    COMMIT;
    
  <b>Rollback</b> - To rollback the transaction in case of errors
  
    <after the transaction>
    ROLLBACK;
    
    SAVEPOINT s1;
        <Perform a transaction>
    ROLLBACK to SAVEPOINT s1;
  
  <b>SavePoint</b> - To set a save point within a transaction
  
    BEGIN;
      INSERT INTO table1 VALUES (3);
      SAVEPOINT my_savepoint;
      INSERT INTO table1 VALUES (4);
      RELEASE SAVEPOINT my_savepoint;
    COMMIT;
  
  <b>SetTransaction</b> - To specify characteristics for the transaction
  
  <b>AutoCommit</b> - To set commit on by default for a particular session
  
    SET AUTOCOMMIT ON;
