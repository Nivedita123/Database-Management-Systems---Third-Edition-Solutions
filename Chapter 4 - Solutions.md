# Database Management Systems - Chapter 4 Solutions

### Exercise 4.1
Explain the statement that relational algebra operators can be composed. Why is the ability to compose operators important?
#### `Answer`

***
### Exercise 4.2
Given two relations R1 and R2, where R1 contains N1 tuples, R2 contains N2 tuples, and N2 > N1 > 0, give the minimum and maximum possible sizes (in tuples) for the resulting relation produced by each of the following relational algebra expressions. In each case, state any assumptions about the schemas for R1 and R2 needed to make the expression meaningful:
1. R1 U R2,
2. R1 n R2,
3. R1 ~ R2,
4. R1 x R2,
5. (Ta=5(R1),
6. 7Ta(R1), and
7. R1/R2

#### `Answer`

***
### Exercise 4.3
Consider the following schema:  
Suppliers (sid: integer, sname: string, address: string)  
Parts (pid: integer, pname: string, color: string)  
Catalog (sid: integer, pid: integer, cost: real)  

The key fields are underlined, and the domain of each field is listed after the field name. Therefore sid is the key for Suppliers, pid is the key for Parts, and sid and pid together form the key for Catalog. The Catalog relation lists the prices charged for parts by Suppliers. Write
the following queries in relational algebra, tuple relational calculus, and domain relational calculus:  
1. Find the narnes of suppliers who supply some red part.
2. Find the sids of suppliers who supply some red or green part.
3. Find the sids of suppliers who supply some red part or are at 221 Packer Ave.
4. Find the sids of suppliers who supply some rcd part and some green part.
5. Find the sids of suppliers who supply every part.
6. Find the sids of suppliers who supply every red part.
7. Find the sids of suppliers who supply every red or green part.
8. Find the sids of suppliers who supply every red part or supply every green part.
9. Find pairs of sids such that the supplier with the first sid charges more for some part than the supplier with the second sid.
10. Find the pids of parts supplied by at least two different suppliers.
11. Find the pids of the most expensive parts supplied by suppliers named Yosemite Sham.
12. Find the pids of parts supplied by every supplier at less than $200. (If any supplier either does not supply the part or charges more than $200 for it, the part is not selected.)

#### `Answer`

***
### Exercise 4.4
Consider the Supplier-Parts-Catalog schema from the previous question. State what the following queries compute:
1. π sname (π sid( σ color='red' Parts) X (σ cost < 100 Catalog) X Suppliers)
2. π sname (1f S id ( σ color='red' Parts) X ( σ cost < 100 Catalog) X Suppliers))
3. (π sname ((σ color'='red' Parts) [X] ( σ cost < 100 Catalog) X Suppliers)) ∩ (π sname(( σ color = 'green' Parts) X (σ cost < 100 Catalog ) X Suppliers)
4. (π sid((color='red' Parts) X ( σ cost < 100 Catalog) X Suppliers)) n
( π sid ((σ color='green' Parts) X ( σ cost < 100 Catalog) X Suppliers))
(π sid,sname ((σ color='green' Parts) X (σ cost < 100 Catalog) X Suppliers)))  


#### `Answer`

***
### Exercise 4.5
Consider the following relations containing airline flight information:

Flights (fino: integer, from: string, to: string, distance: integer, departs: time, arrives: time)  
Aircraft( aid: integer, aname: string, cTuisingrange: integer)  
Certified( eid: integer, aid: integer)  
Employees( eid: integer, ename: string, salary: integer)  

Note that the Employees relation describes pilots and other kinds of employees as well; every pilot is certified for some aircraft (otherwise, he or she would not qualify as a pilot), and only
pilots are certified to fly.  

Write the following queries in relational algebra, tuple relational calculus, and domain relational calculus. Note that some of these queries may not be expressible in relational algebra (and, therefore, also not expressible in tuple and domain relational calculus). For such queries, informally explain why they cannot be expressed. (See the exercises at the end of Chapter 5 for additional queries over the airline schema.)
1. Find the eids of pilots certified for some Boeing aircraft.
2. Find the names of pilots certified for some Boeing aircraft.
~).
3. Find the aids of all aircraft that. can be used on non-stop flights from Bonn to Madras.
4. Identify the flights that can be piloted by every pilot whose salary is more than $100,000.
5. Find the names of pilots who can operate planes with a range greater than 3,000 miles
but are not certified on any Boeing aircraft.
6. Find the eids of employees who make the highest salary.
7. Find the eids of employees who make the second highest salary.
8. Find the eids of employees who are certified for the largest number of aircraft.
9. Find the eids of employees who are certified for exactly three aircraft.
10. Find the total amount paid to employees as salaries.
11. Is there a sequence of flights from Madison to Timbuktu? Each flight in the sequence is required to depart from the city that is the destination of the previous flight; the first flight must leave Madison, the last flight must reach Timbuktu, and there is no restriction
on the number of intermediate flights. Your query must determine whether a sequence of flights from Madison to Timbuktu exists for any input Flights relation instance.

#### `Answer`

***
### Exercise 4.6
What is relational completeness? If a query language is relationally complete, can you write any desired query in that language?

#### `Answer`

***
### Exercise 4.7
What is an unsafe query? Give an example and explain why it is important
to disallow such queries.



***
