# Database Management Systems - Chapter 1 Solutions

### Exercise 1.1

Why would you choose a database system instead of simply storing data in
operating system files? When would it make sense not to use a database system?

### `Answer`
A database is an integrated collection of data, usually so large that it
has to be stored on secondary storage devices such as disks or tapes. This data can
be maintained as a collection of operating system files, or stored in a DBMS (database
management system). The advantages of using a DBMS are:
- Data independence and efficient access. Database application programs are independent
of the details of data representation and storage. The conceptual and
external schemas provide independence from physical storage decisions and logical
design decisions respectively. In addition, a DBMS provides efficient storage and
retrieval mechanisms, including support for very large files, index structures and
query optimization.
- Reduced application development time. Since the DBMS provides several important
functions required by applications, such as concurrency control and crash
recovery, high level query facilities, etc., only application-specific code needs to
be written. Even this is facilitated by suites of application development tools
available from vendors for many database management systems.
- Data integrity and security. The view mechanism and the authorization facilities
of a DBMS provide a powerful access control mechanism. Further, updates to the
data that violate the semantics of the data can be detected and rejected by the
DBMS if users specify the appropriate integrity constraints.
- Data administration. By providing a common umbrella for a large collection of
data that is shared by several users, a DBMS facilitates maintenance and data
administration tasks. A good DBA can effectively shield end-users from the chores
of fine-tuning the data representation, periodic back-ups etc.
- Concurrent access and crash recovery. A DBMS supports the notion of a transaction,
which is conceptually a single user’s sequential program. Users can write
transactions as if their programs were running in isolation against the database.
The DBMS executes the actions of transactions in an interleaved fashion to obtain
good performance, but schedules them in such a way as to ensure that conflicting
operations are not permitted to proceed concurrently. Further, the DBMS maintains
a continuous log of the changes to the data, and if there is a system crash,
it can restore the database to a transaction-consistent state. That is, the actions
of incomplete transactions are undone, so that the database state reflects only the
actions of completed transactions. Thus, if each complete transaction, executing
alone, maintains the consistency criteria, then the database state after recovery
from a crash is consistent.   

If these advantages are not important for the application at hand, using a collection of
files may be a better solution because of the increased cost and overhead of purchasing
and maintaining a DBMS.

***
### Exercise 1.2
What is logical data independence and why is it important?

### `Answer`

***
### Exercise 1.3
Explain the difference between logical and physical data independence.

### `Answer`

Logical data independence means that users are shielded from changes
in the logical structure of the data, while physical data independence insulates users
from changes in the physical storage of the data. We saw an example of logical data
independence in the answer to Exercise 1.2. Consider the Students relation from that
example (and now assume that it is not replaced by the two smaller relations). We
could choose to store Students tuples in a heap file, with a clustered index on the
sname field. Alternatively, we could choose to store it with an index on the gpa field,
or to create indexes on both fields, or to store it as a file sorted by gpa. These storage
alternatives are not visible to users, except in terms of improved performance, since
they simply see a relation as a set of tuples. This is what is meant by physical data
independence

***
### Exercise 1.4
Explain the difference between external, internal, and conceptual schemas. How are these different schema layers related to the concepts of logical and physical data independence?

### `Answer`

***
### Exercise 1.5
What are the responsibilities of a DBA? If we assume that the DBA is never interested in running his or her own queries, does the DBA still need to understand query optimization? Why?

### `Answer`

The DBA is responsible for:
- Designing the logical and physical schemas, as well as widely-used portions of the
external schema.
- Security and authorization.
- Data availability and recovery from failures.
- Database tuning: The DBA is responsible for evolving the database, in particular
the conceptual and physical schemas, to ensure adequate performance as user
requirements change.   
   
A DBA needs to understand query optimization even if s/he is not interested in running
his or her own queries because some of these responsibilities (database design
and tuning) are related to query optimization. Unless the DBA understands the performance
needs of widely used queries, and how the DBMS will optimize and execute
these queries, good design and tuning decisions cannot be made.

***
### Exercise 1.6

Scrooge McNugget wants to store information (names, addresses, descriptions of embarrassing moments, etc.) about the many ducks on his payroll. Not surprisingly, the volume of data compels him to buy a database system. To save money, he wants to buy one with the fewest possible features, and he plans to run it as a stand-alone application on his PC clone. Of course, Scrooge does not plan to share his list with anyone. Indicate which of the following DBMS features Scrooge should pay for; in each case, also indicate why Scrooge should (or should not) pay for that feature in the system he buys.
1. A security facility.
2. Concurrency control.
3. Crash recovery.
4. A view mechanism.
5. A query language.


### `Answer`

***
### Exercise 1.7
Which of the following plays an important role in representing information about the real world in a database'? Explain briefly.
1. The data definition language.
2. The data manipulation language.
3. The buffer manager.
4. The data model.


### `Answer`

Let us discuss the choices in turn.
- The data definition language is important in representing information because it
is used to describe external and logical schemas.
- The data manipulation language is used to access and update data; it is not
important for representing the data. (Of course, the data manipulation language
must be aware of how data is represented, and reflects this in the constructs that
it supports.)
- The buffer manager is not very important for representation because it brings
arbitrary disk pages into main memory, independent of any data representation.
- The data model is fundamental to representing information. The data model
determines what data representation mechanisms are supported by the DBMS.
- The data definition language is just the specific set of language constructs available
to describe an actual application’s data in terms of the data model.

***
### Exercise 1.8
Describe the structure of a DBMS. If your operating system is upgraded to
support some new functions on as files (e.g., the ability to force some sequence of bytes to
disk), which layer(s) of the DBMS would you have to rewrite to take advantage of these new
functions?


### `Answer`

***
### Exercise 1.9
Answer the following questions:
1. What is a transaction?
2. Why does a DBMS interleave the actions of different transactions instead of executing
transactions one after the other?
3. What must a user guarantee with respect to a transaction and database consistency?
What should a DBMS guarantee with respect to concurrent execution of several transactions
and database consistency'?
4. Explain the strict two-phase locking protocol.
5. What is the WAL property, and why is it important?

### `Answer`

1. A transaction is any one execution of a user program in a DBMS. This is the basic
unit of change in a DBMS.
2. A DBMS is typically shared among many users. Transactions from these users
can be interleaved to improve the execution time of users’ queries. By interleaving
queries, users do not have to wait for other user’s transactions to complete
fully before their own transaction begins. Without interleaving, if user A begins
a transaction that will take 10 seconds to complete, and user B wants to begin
a transaction, user B would have to wait an additional 10 seconds for user
A’s transaction to complete before the database would begin processing user B’s
request.
3. A user must guarantee that his or her transaction does not corrupt data or insert
nonsense in the database. For example, in a banking database, a user must guarantee
that a cash withdraw transaction accurately models the amount a person
removes from his or her account. A database application would be worthless if
a person removed 20 dollars from an ATM but the transaction set their balance
to zero! A DBMS must guarantee that transactions are executed fully and independently
of other transactions. An essential property of a DBMS is that a
transaction should execute atomically, or as if it is the only transaction running.
Also, transactions will either complete fully, or will be aborted and the database
returned to it’s initial state. This ensures that the database remains consistent.
4. Strict two-phase locking uses shared and exclusive locks to protect data. A transaction
must hold all the required locks before executing, and does not release any
lock until the transaction has completely finished.
5. The WAL property affects the logging strategy in a DBMS. The WAL, WriteAhead
Log, property states that each write action must be recorded in the log
(on disk) before the corresponding change is reflected in the database itself. This
protects the database from system crashes that happen during a transaction’s
execution. By recording the change in a log before the change is truly made, the
database knows to undo the changes to recover from a system crash. Otherwise,
if the system crashes just after making the change in the database but before
the database logs the change, then the database would not be able to detect his
change during crash recovery.

***
