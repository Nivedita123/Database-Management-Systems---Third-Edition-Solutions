# Database Management Systems - Chapter 3 Solutions

### Exercise 3.1
Define the following terms: relation schema, relational database schema, domain, relation instance, relation cardinality, and relation degree.

### `Answer`

***
### Exercise 3.2
How many distinct tuples are in a relation instance with cardinality 22?

### `Answer`

***
### Exercise 3.3
Does the relational model, as seen by an SQL query writer, provide physical and logical data independence? Explain.

### `Answer`

***
### Exercise 3.4
What is the difference between a candidate key and the primary key for a given relation? What is a superkey?


### `Answer`

***
### Exercise 3.5
Consider the instance of the Students relation shown in Figure 3.1.
1. Give an example of an attribute (or set of attributes) that you can deduce is not a candidate key, based on this instance being legal.
2. Is there any example of an attribute (or set of attributes) that you can deduce is a candidate key, based on this instance being legal?

### `Answer`

***
### Exercise 3.6
What is a foreign key constraint? Why are such constraints important? What is referential integrity?

### `Answer`

***
### Exercise 3.7
Consider the relations Students, Faculty, Courses, Rooms, Enrolled, Teaches, and Meets_in defined in Section 1.5.2.
1. List all the foreign key constraints among these relations.
2. Give an example of a (plausible) constraint involving one or more of these relations that is not a primary key or foreign key constraint.

### `Answer`

***
### Exercise 3.8
Answer each of the following questions briefly. The questions are based On the following relational schema:  
Emp (eid: integer, ename: string, age: integer, sala1l1: real)  
Works (eid: integer, did: integer, peLtime: integer)  
Dept (did: integer, dname: string, budget: real, managerid: integer)

1. Give an example of a foreign key constraint that involves the Dept relation. What are the options for enforcing this constraint when a user attempts to delete a Dept tuple?
2. Write the SQL statements required to create the preceding relations, including appropriate versions of all primary and foreign key integrity constraints.
3. Define the Dept relation in SQL so that every department is guaranteed to have a manager.
4. Write an SQL statement to add John Doe as an employee with eid = 101, age = 32 and salary = 15,000.
5. Write an SQL statement to give every employee a 10 percent raise.
6. Write an SQL statement to delete the Toy department. Given the referential integrity constraints you chose for this schema, explain what happens when this statement is executed.

### `Answer`

***
### Exercise 3.9
Consider the SQL query whose answer is shown in Figure 3.6.
1. Modify this query so that only the login column is included in the answer.
2. If the clause WHERE S.gpa >= 2 is added to the original query, what is the set of tuples in the answer?

### `Answer`

***
### Exercise 3.10
Explain why the addition of NOT NULL constraints to the SQL definition of the Manages relation (in Section 3.5.3) would not enforce the constraint that each department must have a manager. What, if anything, is achieved by requiring that the S8n field of Manages be non-null?

### `Answer`

***
### Exercise 3.11
Suppose that we have a ternary relationship R between entity sets A, B,
and C such that A has a key constraint and total participation and B has a key constraint; these are the only constraints. A has attributes al and a2, with al being the key; Band C are similar. R has no descriptive attributes.   
Write SQL statements that create tables corresponding to this information so &s to capture as many of the constraints as possible. If
you cannot capture some constraint, explain why.

### `Answer`

***
### Exercise 3.12
Consider the scenario from Exercise 2.2, where you designed an ER diagram for a university database. Write SQL statements to create the corresponding relations and capture as many of the constraints as possible. If you cannot, capture some constraints, explain
why.

### `Answer`

***
### Exercise 3.13
Consider the university database from Exercise 2.3 and the ER diagram you designed. Write SQL statements to create the corresponding relations and capture as many of the constraints as possible. If you cannot capture some constraints, explain why.

### `Answer`

***
### Exercise 3.14
Consider the scenario from Exercise 2.4, where you designed am ER diagram for a company database. Write SQL statements to create the corresponding relations and capture as many of the constraints as possible. If you cannot capture some constraints, explain why.

### `Answer`

***
### Exercise 3.15
Consider the Notown database from Exercise 2.5. You have decided to recommend that Notown use a relational database system to store company data. Show the SQL statements for creating relations corresponding to the entity sets and relationship sets in your design. Identify any constraints in the ER diagram that you are unable to capture in
the SQL statements and briefly explain why you could not express them.

### `Answer`

***
### Exercise 3.16
Translate your ER diagram from Exercise 2.6 into a relational schema, and show the SQL statements needed to create the relations, using only key and null constraints. If your translation cannot capture any constraints in the ER diagram, explain why.  
In Exercise 2.6, you also modified the ER diagram to include the constraint that tests on a plane must be conducted by a technician who is an expert on that model. Can you modify the SQL statements defining the relations obtained by mapping the ER diagram to check this
constraint?

### `Answer`

***
### Exercise 3.17
Consider the ER diagram that you designed for the Prescriptions-R-X chain of pharmacies in Exercise 2.7. Define relations corresponding to the entity sets and relationship sets in your design using SQL.

### `Answer`

***
### Exercise 3.18
Write SQL statements to create the corresponding relations to the ER diagram you designed for Exercise 2.8. If your translation cannot capture any constraints in the ER diagram, explain why.

### `Answer`

***
### Exercise 3.19
Briefly answer the following questions based on this schema:  
Emp (eid: integer, ename: string, age: integer, salary: real)  
Works (eid: integer, did: integer, peLtime: integer)  
Dept (did: integer, budget: real, managerid: integer)  
1. Suppose you have a view SeniorEmp defined as follows:  
CREATE VIEW SeniorEmp (sname, sage, salary)  
AS SELECT E.ename, Kage, E.salary  
FROM Emp E  
WHERE Kage > 50  
Explain what the system will do to process the following query:
SELECT S.sname
FROM SeniorEmp S
WHERE S.salary > 100,000
2. Give an example of a view on Emp that could be automatically updated by updating Emp.
3. Give an example of a view on Emp that would be impossible to update (automatically) and explain why your example presents the update problem that it does.

### `Answer`

***
### Exercise 3.20
Consider the following schema:  
Suppliers (sid: integer, sname: string, address: string)  
Parts (pid: integer, pname: string, color: string)  
Catalog(sid: integer, pid: integer, cost: real)  

The Catalog relation lists the prices charged for parts by Suppliers. Answer the following questions:  
1. Give an example of an updatable view involving one relation.
2. Give an example of an updatable view involving two relations.
3. Give an example of an insertable-into view that is updatable.
4. Give an example of an insertable-into view that is not updatable.

### `Answer`

***
