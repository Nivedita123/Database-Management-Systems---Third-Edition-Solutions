# Database Management Systems - Chapter 5 Solutions

Online material is available for all exercises in this chapter on the book's webpage at -  
http://www.cs.wisc.edu/-dbbook  
This includes scripts to create tables for each exercise for use with Oracle, IBM DB2, Microsoft SQL Server, and MySQL.
### Exercise 5.1
Consider the following relations:  
Student (snum: integer, sname: string, major: string, level: string, age: integer)  
Class( name: string, meets_at: time, room: string, fid: integer)  
Enrolled(snum: integer, cname: string)  
Faculty (fid: integer, fnarne: string, deptid: integer)  

The meaning of these relations is straightforward; for example, Enrolled has one record per student-class pair such that the student is enrolled in the class.

Write the following queries in SQL. No duplicates should be printed in any of the answers.
1. Find the nari1es of all Juniors (level = JR) who are enrolled in a class taught by 1. Teach.
2. Find the age of the oldest student who is either a History major or enrolled in a course
taught by I. Teach.
3. Find the names of all classes that either meet in room R128 or have five or more students
enrolled.
4. Find the names of all students who are enrolled in two classes that meet at the same time.
5. Find the names of faculty members who teach in every room in which some class is taught.
6. Find the names of faculty members for whom the combined enrollment of the courses that they teach is less than five.
7. Print the level and the average age of students for that level, for each level.
8. Print the level and the average age of students for that level, for all levels except JR.
9. For each faculty member that has taught classes only in room R128, print the faculty member's name and the total number of classes she or he has taught.
10. Find the names of students enrolled in the maximum number of classes.
11. Find the names of students not enrolled in any class.
12. For each age value that appears in Students, find the level value that appears most often. For example, if there are more FR level students aged 18 than SR, JR, or SO students aged 18, you should print the pair (18, FR).

#### `Answer`

***
### Exercise 5.2
Consider the following schema:  
Suppliers( sid: integer, sname: string, address: string)  
Parts(pid: integer, pname: string, color: string)  
Catalog( sid: integer, pid: integer, cost: real)  
The Catalog relation lists the prices charged for parts by Suppliers.

Write the following queries in SQL:
1. Find the pnames of parts for which there is some supplier.
2. Find the snames of suppliers who supply every part.
3. Find the snames of suppliers who supply every red part.
4. Find the pnames of parts supplied by Acme Widget Suppliers and no one else.
5. Find the sids of suppliers who charge more for some part than the average cost of that part (averaged over all the suppliers who supply that part).
6. For each part, find the sname of the supplier who charges the most for that part.
7. Find the sids of suppliers who supply only red parts.
8. Find the sids of suppliers who supply a red part and a green part.
9. Find the sids of suppliers who supply a red part or a green part.
10. For every supplier that only supplies green parts, print the name of the supplier and the total number of parts that she supplies.
11. For every supplier that supplies a green part and a reel part, print the name and price of the most expensive part that she supplies.

#### `Answer`

***
### Exercise 5.3
The following relations keep track of airline flight information:  
Flights(.flno: integer, from: string, to: string, distance: integer,
departs: time, arrives: time, price: integer)  
Aircraft( aid: integer, aname: string, cruisingrange: integer)  
Certified( eid: integer, aid: integer)  
Employees( eid: integer I ename: string, salary: integer)  

Note that the Employees relation describes pilots and other kinds of employees as well; every pilot is certified for some aircraft, and only pilots are certified to fly. Write each of the following queries in SQL. (Additional queries using the same schema are listed in the exercises for Chapter 4)

1. Find the names of aircraft such that all pilots certified to operate them earn more than $80,000.
2. For each pilot who is certified for more than three aircraft, find the eid and the maximum cruisingrange of the aircraft for which she or he is certified.
3. Find the names of pilots whose salary is less than the price of the cheapest route from Los Angeles to Honolulu.
4. For all aircraft with cruisingrange over 1000 miles, find the name of the aircraft and the average salary of all pilots certified for this aircraft.
5. Find the names of pilots certified for some Boeing aircraft.
6. Find the aids of all aircraft that can be used on routes from Los Angeles to Chicago.
7. Identify the routes that can be piloted by every pilot who makes more than $100,000.
8. Print the enames of pilots who can operate planes with cruisingrange greater than 3000 miles but are not certified on any Boeing aircraft.
9. A customer wants to travel from Madison to New York with no more than two changes of flight. List the choice of departure times from Madison if the customer wants to arrive in New York by 6 p.m.
10. Compute the difference between the average salary of a pilot and the average salary of all employees (including pilots).
11. Print the name and salary of every nonpilot whose salary is more than the average salary for pilots.
12. Print the names of employees who are certified only on aircrafts with cruising range longer than 1000 miles.
13. Print the names of employees who are certified only on aircrafts with cruising range longer than 1000 miles, but on at least two such aircrafts.
14. Print the names of employees who are certified only on aircrafts with cruising range longer than 1000 miles and who are certified on some Boeing aircraft.

#### `Answer`

***
### Exercise 5.4
Consider the following relational schema. An employee can work in more than one department; the pct_time field of the Works relation shows the percentage of time that a given employee works in a given department.

Emp(eid: integer, ename: string, age: integer, salary: real)  
Works(eid: integer, did: integer, pct_time: integer)  
Dept(did.· integer, budget: real, managerid: integer)  

Write the following queries in SQL:
1. Print the names and ages of each employee who works in both the Hardware department
and the Software department.
2. For each department with more than 20 full-time-equivalent employees (i.e., where the part-time and full-time employees add up to at least that many full-time employees), print the did together with the number of employees that work in that department.
3. Print the name of each employee whose salary exceeds the budget of all of the departments that he or she works in.
4. Find the managerids of managers who manage only departments with budgets greater than $1 million.
5. Find the enames of managers who manage the departments with the largest budgets.
6. If a manager manages more than one department, he or she controls the sum of all the budgets for those departments. Find the managerids of managers who control more than $5 million.
7. Find the managerids of managers who control the largest amounts.
8. Find the enames of managers who manage only departments with budgets larger than $1 million, but at least one department with budget less than $5 million.

#### `Answer`

***
### Exercise 5.5
Consider the instance of the Sailors relation shown in Figure 5.22.
1. Write SQL queries to compute the average rating, using AVG;  the sum of the ratings, using SUM; and the number of ratings, using COUNT.
2. If you divide the sum just computed by the count, would the result be the same as the average? How would your answer change if these steps were carried out with respect to the age field instead of rating?
3. Consider the following query: Find the names of sailors with a higher rating than all sailors with age < 21. The following two SQL queries attempt to obtain the answer to this question. Do they both compute the result? If not, explain why. Under what conditions would they compute the same result?

SELECT S.sname  
FROM Sailors S  
WHERE NOT EXISTS ( SELECT *  
FROM Sailors S2  
WHERE S2.age < 21  
AND S.rating <= S2.rating )  

SELECT *  
FROM Sailors S  
WHERE S.rating > ANY  
SELECT S2.rating  
FROM Sailors S2  
WHERE S2.age < 21  


4. Consider the instance of Sailors shown in Figure 5.22. Let us define instance Sl of Sailors to consist of the first two tuples, instance S2 to be the last two tuples, and S to be the given instance.

(a) Show the left outer join of S with itself, with the join condition being sid=sid.  
(b) Show the right outer join of S ,vith itself, with the join condition being sid=sid.  
(c) Show the full outer join of S with itself, with the join condition being Sid=sid.  
(d) Show the left outer join of Sl with S2, with the join condition being sid=sid.  
(e) Show the right outer join of Sl with S2, with the join condition being sid=sid.  
(f) Show the full outer join of 81 with S2, with the join condition being sid=sid.  

#### `Answer`

***
### Exercise 5.6
Answer the following questions:
1. Explain the term impedance mismatch in the context of embedding SQL commands in a host language such as C.
2. How can the value of a host language variable be passed to an embedded SQL command?
3. Explain the WHENEVER command's use in error and exception handling.
4. Explain the need for cursors.
5. Give an example of a situation that calls for the use of embedded SQL; that is, interactive use of SQL commands is not enough, and some host language capabilities are needed.
6. Write a C program with embedded SQL commands to address your example in the previous answer.
7. Write a C program with embedded SQL commands to find the standard deviation of sailors' ages.
8. Extend the previous program to find all sailors whose age is within one standard deviation of the average age of all sailors.
9. Explain how you would write a C program to compute the transitive closure of a graph, represented as an 8QL relation Edges(jrom, to), using embedded SQL commands. (You need not write the program, just explain the main points to be dealt with.)
10. Explain the following terms with respect to cursors: 'updatability, sensitivity, and scrollability.
11. Define a cursor on the Sailors relation that is updatable, scrollable, and returns answers sorted by age. Which fields of Sailors can such a cursor not update? Why?
12. Give an example of a situation that calls for dynamic 8QL; that is, even embedded SQL is not sufficient.

#### `Answer`

***
### Exercise 5.7
Consider the following relational schema and briefly answer the questions that follow:  
Emp (eid: integer, cname: string, age: integer, salary: real)  
Works (eid: integer, did: integer, pet-time: integer)  
Dept (did.' integer, budget: real, managerid: integer)  
1. Define a table constraint on Emp that will ensure that ever)' employee makes at least $10,000.
2. Define a table constraint on Dept that will ensure that all managers have age> 30.
3. Define an assertion on Dept that will ensure that all managers have age> 30. Compare this assertion with the equivalent table constraint. Explain which is better.
4. Write SQL statements to delete all information about employees whose salaries exceed that of the manager of one or more departments that they work in. Be sure to ensure that all the relevant integrity constraints are satisfied after your updates.

#### `Answer`

***
### Exercise 5.8
Consider the following relations:  

Student (snum: integer, sname: string, major: string, level: string, age: integer)  
Class(name: string, meets_at: time, room: string, fid: integer)
Enrolled(snurn: integer, cnarne: string)  
Faculty(fid: integer, fnarne: string, deptid: integer)  

The meaning of these relations is straightforward; for example, Enrolled has one record per student-class pair such that the student is enrolled in the class.
1. Write the SQL statements required to create these relations, including appropriate versions of all primary and foreign key integrity constraints.
2. Express each of the following integrity constraints in SQL unless it is implied by the primary and foreign key constraint; if so, explain how it is implied. If the constraint cannot be expressed in SQL, say so. For each constraint, state what operations (inserts,
deletes, and updates on specific relations) must be monitored to enforce the constraint.
 1. Every class has a minimum enrollment of 5 students and a maximum enrollment of 30 students.
 2. At least one dass meets in each room.
 3. Every faculty member must teach at least two courses.
 4. Only faculty in the department with deptid=33 teach more than three courses.
 5. Every student must be enrolled in the course called Mathl0l.
 6. The room in which the earliest scheduled class (i.e., the class with the smallest meets_at value) meets should not be the same as the room in which the latest scheduled class meets.
 7. Two classes cannot meet in the same room at the same time.
 8. The department with the most faculty members must have fewer than twice the number of faculty members in the department with the fewest faculty members.
 9. No department can have more than 10 faculty members.
 10. A student cannot add more than two courses at a time (i.e., in a single update).
 11. The number of CS majors must be more than the number of Math majors.
 12. The number of distinct courses in which CS majors are enrolled is greater than the number of distinct courses in which Math majors are enrolled.
 13. The total enrollment in courses taught by faculty in the department with deptid is greater than the number of Math majors.
 14. There mUst be at least one CS major if there are any students whatsoever.
 15. Faculty members from different departments cannot teach in the same room.


#### `Answer`

***
### Exercise 5.9
Discuss the strengths and weaknesses of the trigger mechanism. Contrast triggers with other integrity constraints supported by SQL.

#### `Answer`

***
### Exercise 5.10
Consider the following relational schema. An employee can work in more than one department; the pct_time field of the Works relation shows the percentage of time that a given employee works in a given department.  

Emp (eid: integer, ename: string, age: integer, salary: real)  
Works (eid: integer, did: integer, pct_time: integer)  
Dept (did: integer, budget: real, managerid: integer)  

Write SQL-92 integrity constraints (domain, key, foreign key, or CHECK constraints; or assertions) or SQL:1999 triggers to ensure each of the following requirements, considered independently.
1. Employees must make a minimum salary of $1000.
2. Every manager must be also be an employee.
3. The total percentage of all appointments for an employee must be under 100%.
4. A manager must always have a higher salary than any employee that he or she manages.
5. Whenever an employee is given a raise, the manager's salary must be increased to be at least as much.
6. Whenever an employee is given a raise, the manager's salary must be increased to be at least as much. Further, whenever an employee is given a raise, the department's budget must be increased.


#### `Answer`

***
