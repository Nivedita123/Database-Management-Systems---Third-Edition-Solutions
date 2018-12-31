# Database Management Systems - Third Edition Solutions

### Exercise 16.1 
Give brief answers to the following questions:
1. What is a transaction? In what ways is it different from an ordinary program (in a
language such as C)?
2. Define these terms: atomicity, consistency, isolation, durability, schedule, blind write,
dirty read, unrepeatable read, serializable schedule, recoverable schedule, avoidsvcascadingaborts
schedule.
3. Describe Strict 2PL.
4. What is the phantom problem? Can it occur in a database where the set of database
objects is fixed and only the values of objects can be changed?

#### `Answer`

***

### Exercise 16.2 
Consider the following actions taken by transaction T1 on database objects
X and Y:
R(X), W(X),R(Y), W(Y)
1. Give an example of another transaction T2 that, if run concurrently to transaction T
without some form of concurrency control, could interfere with T1.
2. Explain how the use of Strict 2PL would prevent interference between the two transactions.
3. Strict 2PL is used in many database systems. Give two reasons for its popularity.

#### `Answer`

***

### Exercise 16.3 
Consider a database with objects X and Y and assume that there are two
transactions Tl and T2. Transaction T1 reads objects X and Y and then writes object X.
Transaction T2 reads objects X and Y and then writes objects X and Y.
1. Give an example schedule with actions of transactions T1 and T2 on objects X and Y
that results in a write-read conflict.
2. Give an example schedule with actions of transactions T1 and T2 on objects X and Y
that results in a read-write conflict.
3. Give an example schedule with actions of transactions T1 and T2 on objects X and Y
that results in a write-write conflict.
4. For each of the three schedules, show that Strict 2PL disallows the schedule.

#### `Answer`

1. Write-read conflict (Reading uncommited data or Dirty Read) -   
T1 R(X)  
T1 R(Y)  
T1 W(X)  
T2 R(X) - Dirty Read  
...  

2. Read-Write Conflict (Unrepeatable reads) -  
T1 R(X)  
T1 R(Y)  
T2 R(X)
T2 R(Y)  
T1 W(X)  
...  
Now T2 will get unrepeatable read.  

3. Write-Write conflict (Overwriitng uncommited data) -  
T1 R(X)  
T1 R(Y)  
T2 R(X)  
T1 W(X)  - Step 4
T2 R(Y)  
T2 W(X) - Write-Write conflict  
...  

4. Write-read conflict - T2 will not get a Shared lock on X, untill T1 commits.  
Read-Write Conflict - T1 will not get Exclusive lock on X untill T2 commits.  
Write-Write conflict - T1 will not get Exclusive lock on X in Step 4, unitll T2 commits.  

***
### Exercise 16.4 
We call a transaction that only reads database object a read-only transaction,
otherwise the transaction is called a read-write transaction. Give brief answers to the
following questions:
1. What is lock thrashing and when does it occur?
2. What happens to the database system throughput if the number of read-write transactions
is increased?
3. What happens to the datbase system throughput if the number of read-only transactions
is increased?
4. Describe three ways of tuning your system to increase transaction throughput.

#### `Answer`

1. Lock thrashing occurs when a large number of active transactions get blocked while competing for locks.
2. Number of transactions waiting for locks , increases.  
3. No impact, multiple transactions can acquire Shared locks simultaneously.
4. Throughput can be increased by  -
   - Lock the smallest size objects possible.
   - Reduce the time for which a transaction holds locks.
   - Reduce number of hotspots (Objects that are frequently accessed and modified).


***

### Exercise 16.5 
Suppose that a DBMS recognizes increment, which increments an integervalued
object by 1, and decrement as actions, in addition to reads and writes. A transaction
that increments an object need not know the value of the object; increment and decrement
are versions of blind writes. In addition to shared and exclusive locks, two special locks are
supported: An object must be locked in I mode before incrementing it and locked in D mode
before decrementing it. An I lock is compatible with another I or D lock on the same object,
but not with S and X locks.
1. Illustrate how the use of I and D locks can increase concurrency. (Show a schedule
allowed by Strict 2PL that only uses S and X locks. Explain how the use of I and D
locks can allow more actions to be interleaved, while continuing to follow Strict 2PL.)
2. Informally explain how Strict 2PL guarantees serializability even in the presence of I
and D locks. (Identify which pairs of actions conflict, in the sense that their relative
order can affect the result, and show that the use of 5, X, I, and D locks according
to Strict 2PL orders all conflicting pairs of actions to be the same as the order in some
serial schedule.)

#### `Answer`

1. Take the following two transactions as example:  
T1: Increment A, Decrement B, Read C;  
T2: Increment B, Decrement A, Read C  
If using only strict 2PL, all actions are versions of blind writes, they have to obtain
exclusive locks on objects. Following strict 2PL, T1 gets an exclusive lock on A,
if T2 now gets an exclusive lock on B, there will be a deadlock. Even if T1 is fast
enough to have grabbed an exclusive lock on B first, T2 will now be blocked until
T1 finishes. This has little concurrency. If I and D locks are used, since I and
D are compatible, T1 obtains an I-Lock on A, and a D-Lock on B; T2 can still
obtain an I-Lock on B, a D-Lock on A; both transactions can be interleaved to
allow maximum concurrency.
2. The pairs of actions which conflicts are:  
RW, WW, WR, IR, IW, DR, DW  
We know that strict 2PL orders the first 3 conflicts pairs of actions to be the same
as the order in some serial schedule. We can also show that even in the presence
of I and D locks, strict 2PL also orders the latter 4 pairs of actions to be the
same as the order in some serial schedule. Think of an I (or D)lock under these
circumstances as an exclusive lock, since an I(D) lock is not compatible with S
and X locks anyway (ie. can’t get a S or X lock if another transaction has an I or
D lock). So serializability is guaranteed.

***

### Exercise 16.6 
Answer the following questions: SQL supports four isolation-levels and t.wo
access-modes, for a total of eight combinations of isolation-level and access-mode. Each
combination impiicitly defines a class of transactions; the following questions refer to these
eight classes:
1. Consider the four SQL isolation levels. Describe which of the plHmomena can occur at
each of these isolation levels: dirty read, unrepeatable read, phantom problem.
2. For each of the four isolation levels, give examples of transactions that could be run
safely at that level.
:.3. Why does the access mode of a transaction matter?

#### `Answer`

***

### Exercise 16.7 
Consider the university enrollment database schema:
Student(snurn: integer, snarne: string, majoT: string, level: string, age: integer)
Class(name: string, meets_at: time, Toom: string, fid"' integer)
Enrolled(snum: integer, cname: string)
Faculty(fid: integer, fname: string, deptid: integer)
The meaning of these relations is straightforward; for example, Enrolled has one record per
student-class pair such that the student is enrolled in the class.
For each of the following transactions, state the SQL isolation level you would use and explain
why you chose it.
1. Enroll a student identified by her snum into the class named 'Introduction to Database
Systems'.
2. Change enrollment for a student identified by her snum from one class to another class,
3. Assign a new faculty member identified by his fid to the class with the least number of
students.
4. For each class, show the number of students enrolled in the class.

#### `Answer`

***

### Exercise 16.8 
Consider the following schema:
Suppliers(sid: integer, sname: string, addTess: string)
Parts(pid: integer, pname: string, coloT: string)
Catalog(sid: integer, pid: integer, cost: real)
The Catalog relation lists the prices charged for parts by Suppliers.
For each of the following transactions, state the SQL isolation level that you would use and
explain why you chose it.
1. A transaction that adds a new part to a supplier's catalog.
2. A transaction that increases the price that a supplier charges for a part.
3. A transaction that determines the total number of items for a given supplier.
4. A transaction that shows, for each part, the supplier that supplies the part at the lowest
price.

#### `Answer`

***

### Exercise 16.9 
Consider a database with the following schema:
Suppliers(sid: integer, sname: string, addTess: string)
Parts(pid: integer, pname: string, coloT: string)
Catalog( sid: integer, pid: integer, cost: real)
The Catalog relation lists the prices charged for parts by Suppliers.
Consider three transactions 1'1,1'2, and 1'3; 1'1 always h8.o.'3 SQL isolation level SERIALIZABLE.
We first run 1'1 concurrently with 1'2 and then we run 1'1 concurrently with 1'2 but we change
the isolation level of 1'2 as specified below. Give a database instance and SQL statements for
1'1 and 1'2 such that result of running 1'2 with the first SQL isolation level is different from
running 1'2 with the second SQL isolation level. Also specify the common schedule of 1'1 and
1'2 and explain why the results are different.
1. SERIALIZABLE versus REPEATABLE READ.
2. REPEATABLE READ versus READ COMMITTED.
3. READ COMMITTED versus READ UNCOMMITTED

#### `Answer`

***
