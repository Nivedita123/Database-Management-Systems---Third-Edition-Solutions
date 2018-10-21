# Database Management Systems - Chapter 6 Solutions

### Exercise 6.1
Briefly answer the following questions.
1. Explain the following terms: Cursor, Embedded SQL, JDBC, SQLJ, stored procedure.
2. What are the differences between JDBC and SQLJ? \Nhy do they both exist?
3. Explain the term stored procedure, and give examples why stored procedures are useful.
#### `Answer`

### Exercise 6.2
Explain how the following steps are performed in JDBC:
1. Connect to a data source.
2. Start, commit, and abort transactions.
3. Call a stored procedure.
How are these steps performed in SQLJ?
#### `Answer`

### Exercise 6.3
Compare exception handling and handling of warnings ill embedded SQL, dynamic SQL, .IDBC, and SQL.I.
#### `Answer`

### Exercise 6.4
Answer the following questions.
1. Why do we need a precompiler to translate embedded SQL and SQL.J? Why do we not need a precompiler for .IDBC?
2. SQL.J and embedded SQL use variables in the host language to pass parameters to SQL queries, whereas .JDBC uses placeholders marked with a ''1'. Explain the difference, and why the different mechanisms are needed.
#### `Answer`

### Exercise 6.5
A dynamic web site generates HTML pages from information stored in a
database. Whenever a page is requested, is it dynamically assembled from static data and data in a database, resulting in a database access. Connecting to the database is usually a time-consuming process, since resources need to be allocated, and the user needs to be authenticated. Therefore, connection pooling--setting up a pool of persistent database connections and then reusing them for different requests can significantly improve the performance
of database-backed websites. Since servlets can keep information beyond single requests, we can create a connection pool, and allocate resources from it to new requests.

Write a connection pool class that provides the following methods:
- Create the pool with a specified number of open connections to the database system.
- Obtain an open connection from the pool.
- Release a connection to the pool.
- Destroy the pool and close all connections.

#### `Answer`
