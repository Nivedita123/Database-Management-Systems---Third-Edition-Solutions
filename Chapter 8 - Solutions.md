# Database Management Systems - Chapter 8 Solutions

### Exercise 8.1
Answer the following questions about data on external storage in a DBMS:
1. Why does a DBMS store data on external storage?
2. Why are I/O costs important in a DBMS?
3. What is a record id? Given a record's id, how many I/Os are needed to fetch it into
main memory?
4. What is the role of the buffer manager in a DBMS? What is the role of the disk space
manager? How do these layers interact with the file and access methods layer?

#### `Answer`

***
### Exercise 8.2 Answer the following questions about files and indexes:
1. What operations arc supported by the file of records abstraction?
2. What is an index on a file of records? What is a search key for an index? Why do we
need indexes?
3. What alternatives are available for the data entries in an index?
4. What is the difference between a primary index and a secondary index? What is a duplicate data entry in an index? Can a primary index contain duplicates?
5. What is the difference between a clustered index and an unclustered index? If an index contains data records as 'data entries,' can it be unclustered?
6. How many clustered indexes can you create on a file? Would you always create at least one clustered index for a file?
7. Consider Alternatives (1), (2) and (3) for 'data entries' in an index, as discussed in Section 8.2 . Are all of them suitable for secondary indexes? Explain.

#### `Answer`

***
### Exercise 8.3
Consider a relation stored as a randomly ordered file for which the only index is an unclustered index on a field called sal. If you want to retrieve all records with sal> 20, is using the index always the best alternative? Explain.
#### `Answer`

***
### Exercise 8.4
Consider the instance of the Students relation shown in Figure 8.6, sorted by age: For the purposes of this question, assume that these tuples are stored in a sorted file in the order shown; the first tuple is on page 1 the second tuple is also on page 1; and so on. Each page can store up to three data records; so the fourth tuple is on page 2. Explain what the data entries in each of the following indexes contain. If the order of entries is significant, say so and explain why. If such all index cannot be constructed, say so and explain why.
1. An unclustered index on age using Alternative (1).
2. An unclustered index on age using Alternative (2).
3. An unclustered index on age using Alternative (3).
4. A clustered index on age using Alternative (1).
5. A clustered index on age using Alternative (2).
6. A clustered index on age using Alternative (3).
7. An unclustered index on gpa using Alternative (1).
8. An unclustered index on gpa using Alternative (2).
9. An unclustered index on gpa using Alternative (3).
10. A clustered index on gpa using Alternative (1).
11. A clustered index on gpa using Alternative (2).
12. A clustered index on gpa using Alternative (3).

#### `Answer`

***
### Exercise 8.5
Explain the difference between Hash indexes and B+-tree indexes. In particular, discuss how equality and range searches work, using an example.
#### `Answer`

***
### Exercise 8.6
Fill in the I/O costs in Figure 8.7.
#### `Answer`

***
### Exercise 8.7
If you were about to create an index on a relation, what considerations would guide your choice? Discuss:
1. The choice of primary index.
2. Clustered versus unclustered indexes.
3. Hash versus tree indexes.
4. The use of a sorted file rather than a tree-based index.
5. Choice of search key for the index. What is a composite search key, and what considerations are made in choosing composite search keys? What are index-only plans, and what is the influence of potential index-only evaluation plans on the choice of search key
for an index?

#### `Answer`

***
### Exercise 8.8
Consider a delete specified using an equality condition. For each of the five file organizations, what is the cost if no record qualifies? What is the cost if the condition is not on a key?
#### `Answer`

***
### Exercise 8.9
What main conclusions can you draw from the discussion of the five basic file organizations discussed in Section 8.4? Which of the five organizations would you choose for a file where the most frequent operations are as follows?
1. Search for records based on a range of field values.
2. Perform inserts and scans, where the order of records docs not matter.
3. Search for a record based on a particular field value.

#### `Answer`

***
### Exercise 8.10 Consider the following relation:
Emp( eid: integer, sal: integer l age: real, did: integer)
There is a clustered index on cid and an llnclustered index on age.
1. How would you use the indexes to enforce the constraint that eid is a key?
2. Give an example of an update that is definitely speeded 1lJi because of the available
indexes. (English description is sufficient.)
3. Give an example of an update that is definitely slowed down because of the indexes.
(English description is sufficient.)
4. Can you give an example of an update that is neither speeded up nor slowed down by the indexes?

#### `Answer`

***
### Exercise 8.11
Consider the following relations:  

Emp( eid: integer, ename: varchar, sal: integer, age: integer, did: integer)  
Dept(did: integer, budget: integer, floor: integer, mgr_eid: integer)  

Salaries range from $10,000 to $100,000, ages vary from 20 to 80, each department has about five employees on average, there are 10 floors, and budgets vary from $10,000 to $1 million. You can assume uniform distributions of values. For each of the following queries, which of the listed index choices would you choose to speed up the query? If your database system does not consider index-only plans (i.e., data records are always retrieved even if enough information is available in the index entry), how would
your answer change? Explain briefly.
1. Query: Print ename, age, and sal for all employees.
(a) Clustered hash index on (ename, age, sal) fields of Emp.  
(b) Unclustered hash index on (ename, age, sal) fields of Emp.  
(c) Clustered B+ tree index on (ename, age, sal) fields of Emp.  
(d) Unclustered hash index on (eid, did) fields of Emp.  
(e) No index.  

2. Query: Find the dids of departments that are on the 10th floor and have a budget of less than $15,000.
(a) Clustered hash index on the floor field of Dept.  
(b) Unclustered hash index on the floor' field of Dept.  
(c) Clustered B+ tree index on (floor, budget) fields of Dept.  
(d) Clustered B+ tree index on the budget: field of Dept.  
(e) No index.  

#### `Answer`

***
