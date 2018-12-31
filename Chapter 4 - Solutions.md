# Database Management Systems - Chapter 4 Solutions

### Exercise 4.1
Explain the statement that relational algebra operators can be composed. Why is the ability to compose operators important?
#### `Answer`
Every operator in relational algebra accepts one or more relation instances as arguments and the result is always an relation instance. So the argument
of one operator could be the result of another operator. This is important because,
this makes it easy to write complex queries by simply composing the relational algebra
operators.

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
In the answers below RA refers to Relational Algebra, TRC refers to
Tuple Relational Calculus and DRC refers to Domain Relational Calculus.

1. - **RA**   
π sname(π sid((π pid σ (color = 'red') Parts) X Catalog) X Suppliers)   
 - **TRC**   
{T | ∃T 1 ∈ Suppliers(∃X ∈ Parts(X.color = 'red' ∧ ∃Y ∈ Catalog
(Y.pid = X.pid ∧ Y.sid = T 1.sid)) ∧ T.sname = T 1.sname)}   
 - **DRC**   
{ <Y> | <X, Y, Z> ∈ Suppliers ∧ ∃P, Q, R( <P, Q, R> ∈ Parts
∧ (R = 'red') ∧ ∃I, J, K( <I, J, K> ∈ Catalog ∧ J = P ∧ I = X))}   
 - **SQL**   
SELECT S.sname
FROM Suppliers S, Parts P, Catalog C
WHERE P.color=’red’ AND C.pid=P.pid AND C.sid=S.sid

2.  - **RA**   
π sid(π pid(σ (color='red' v color='green') Parts) X catalog)   
  - **TRC**   
{T | ∃T 1 ∈ Catalog(∃X ∈ P arts((X.color = ‘red ∨ X.color = ‘green
)
∧X.pid = T 1.pid) ∧ T.sid = T 1.sid)}   
 - **DRC**   
{X|X, Y, Z ∈ Catalog ∧ ∃A, B, C(A, B, C ∈ P arts
∧(C = red ∨ C = green
) ∧ A = Y )}   
 - **SQL**   
SELECT C.sid
FROM Catalog C, Parts P
WHERE (P.color = ‘red’ OR P.color = ‘green’)
AND P.pid = C.pid

3. - **RA**   
ρ(R1, πsid((πpidσcolor=redP arts)  Catalog))
ρ(R2, πsidσaddress=221P ackerStreetSuppliers)
R1 ∪ R2   
 - **TRC**   
{T | ∃T 1 ∈ Catalog(∃X ∈ P arts(X.color = ‘red ∧ X.pid = T 1.pid)
∧T.sid = T 1.sid)
∨∃T 2 ∈ Suppliers(T 2.address = 221P ackerStreet ∧ T.sid = T 2.sid)}   
 - **DRC**   
{X|X, Y, Z ∈ Catalog ∧ ∃A, B, C(A, B, C ∈ P arts
∧C = red ∧ A = Y )
∨∃P, Q(X, P, Q ∈ Suppliers ∧ Q = 221P ackerStreet
)}   
 - **SQL**   
SELECT S.sid
FROM Suppliers S
WHERE S.address = ‘221 Packer street’
OR S.sid IN ( SELECT C.sid
FROM Parts P, Catalog C
WHERE P.color=’red’ AND P.pid = C.pid )

4. - **RA**    
ρ(R1, πsid((πpidσcolor=redP arts)  Catalog))
ρ(R2, πsid((πpidσcolor=greenP arts)  Catalog))
R1 ∩ R2   
 - **TRC**   
{T | ∃T 1 ∈ Catalog(∃X ∈ P arts(X.color = ‘red ∧ X.pid = T 1.pid)
∧∃T 2 ∈ Catalog(∃Y ∈ P arts(Y.color = green ∧ Y.pid = T 2.pid)
∧T 2.sid = T 1.sid) ∧ T.sid = T 1.sid)}   
 - **DRC**   
{X|X, Y, Z ∈ Catalog ∧ ∃A, B, C(A, B, C ∈ P arts
∧C = red ∧ A = Y )
∧∃P, Q, R(P, Q, R ∈ Catalog ∧ ∃E, F, G(E, F, G ∈ P arts
∧G = green ∧ E = Q) ∧ P = X)}   
 - **SQL**   
SELECT C.sid
FROM Parts P, Catalog C
WHERE P.color = ‘red’ AND P.pid = C.pid
AND EXISTS ( SELECT P2.pid
FROM Parts P2, Catalog C2
WHERE P2.color = ‘green’ AND C2.sid = C.sid
AND P2.pid = C2.pid )

5. - **RA**   
(πsid,pidCatalog)/(πpidP arts)   
 - **TRC**   
{T | ∃T 1 ∈ Catalog(∀X ∈ P arts(∃T 2 ∈ Catalog
(T 2.pid = X.pid ∧ T 2.sid = T 1.sid)) ∧ T.sid = T 1.sid)}   
 - **DRC**   
{X|X, Y, Z ∈ Catalog ∧ ∀A, B, C ∈ P arts
(∃P, Q, R ∈ Catalog(Q = A ∧ P = X))}   
 - **SQL**   
SELECT C.sid
FROM Catalog C
WHERE NOT EXISTS (SELECT P.pid
FROM Parts P
WHERE NOT EXISTS (SELECT C1.sid
FROM Catalog C1
WHERE C1.sid = C.sid
AND C1.pid = P.pid))

6. - **RA**   
(πsid,pidCatalog)/(πpidσcolor=redP arts)   
 - **TRC**   
{T | ∃T 1 ∈ Catalog(∀X ∈ P arts(X.color
= ‘red
∨∃T 2 ∈ Catalog(T 2.pid = X.pid ∧ T 2.sid = T 1.sid))
∧T.sid = T 1.sid)}   
 - **DRC**   
{X|X, Y, Z ∈ Catalog ∧ ∀A, B, C ∈ P arts
(C
= ‘red ∨ ∃P, Q, R ∈ Catalog(Q = A ∧ P = X))}   
 - **SQL**   
SELECT C.sid
FROM Catalog C
WHERE NOT EXISTS (SELECT P.pid
FROM Parts P
WHERE P.color = ‘red’
AND (NOT EXISTS (SELECT C1.sid
FROM Catalog C1
WHERE C1.sid = C.sid AND
C1.pid = P.pid)))

7. - **RA**   
(πsid,pidCatalog)/(πpidσcolor=red∨color=greenP arts)
TRC
{T | ∃T 1 ∈ Catalog(∀X ∈ P arts((X.color
= ‘red
∧X.color
= ‘green
) ∨ ∃T 2 ∈ Catalog
(T 2.pid = X.pid ∧ T 2.sid = T 1.sid)) ∧ T.sid = T 1.sid)}
 - **DRC**   
{X|X, Y, Z ∈ Catalog ∧ ∀A, B, C ∈ P arts
((C
= ‘red ∧ C
= ‘green
) ∨ ∃P, Q, R ∈ Catalog
(Q = A ∧ P = X))}
 - **SQL**   
SELECT C.sid
FROM Catalog C
WHERE NOT EXISTS (SELECT P.pid
FROM Parts P
WHERE (P.color = ‘red’ OR P.color = ‘green’)
AND (NOT EXISTS (SELECT C1.sid
FROM Catalog C1
WHERE C1.sid = C.sid AND
C1.pid = P.pid)))

8. - **RA**
ρ(R1,((πsid,pidCatalog)/(πpidσcolor=redP arts)))
ρ(R2,((πsid,pidCatalog)/(πpidσcolor=greenP arts)))
R1 ∪ R2
 - **TRC**   
{T | ∃T 1 ∈ Catalog((∀X ∈ P arts
(X.color
= ‘red ∨ ∃Y ∈ Catalog(Y.pid = X.pid ∧ Y.sid = T 1.sid))
∨∀Z ∈ P arts(Z.color
= ‘green ∨ ∃P ∈ Catalog
(P.pid = Z.pid ∧ P.sid = T 1.sid))) ∧ T.sid = T 1.sid)}
 - **DRC**   
{X|X, Y, Z ∈ Catalog ∧ (∀A, B, C ∈ P arts
(C
= ‘red ∨ ∃P, Q, R ∈ Catalog(Q = A ∧ P = X))
∨∀U, V, W ∈ P arts(W
= ‘green ∨ M,N,L ∈ Catalog
(N = U ∧ M = X)))}
 - **SQL**   
SELECT C.sid
FROM Catalog C
WHERE (NOT EXISTS (SELECT P.pid
FROM Parts P
WHERE P.color = ‘red’ AND
(NOT EXISTS (SELECT C1.sid
FROM Catalog C1
WHERE C1.sid = C.sid AND
C1.pid = P.pid))))
OR ( NOT EXISTS (SELECT P1.pid
FROM Parts P1
WHERE P1.color = ‘green’ AND
(NOT EXISTS (SELECT C2.sid
FROM Catalog C2
WHERE C2.sid = C.sid AND
C2.pid = P1.pid))))

9. - **RA**
ρ(R1, Catalog)
ρ(R2, Catalog)
πR1.sid,R2.sid(σR1.pid=R2.pid∧R1.sid=R2.sid∧R1.cost>R2.cost(R1 × R2))
 - **TRC**   
{T | ∃T 1 ∈ Catalog(∃T 2 ∈ Catalog
(T 2.pid = T 1.pid ∧ T 2.sid
= T 1.sid
∧T 2.cost < T 1.cost ∧ T.sid2 = T 2.sid)
∧T.sid1 = T 1.sid)}
 - **DRC**
{X, P|X, Y, Z ∈ Catalog ∧ ∃P, Q, R
(P, Q, R ∈ Catalog ∧ Q = Y ∧ P
= X ∧ R<Z)}
 - **SQL**   
SELECT C1.sid, C2.sid
FROM Catalog C1, Catalog C2
WHERE C1.pid = C2.pid AND C1.sid
= C2.sid
AND C1.cost > C2.cost

10. - **RA**
ρ(R1, Catalog)
ρ(R2, Catalog)
πR1.pidσR1.pid=R2.pid∧R1.sid=R2.sid(R1 × R2)

 - **TRC**
{T | ∃T 1 ∈ Catalog(∃T 2 ∈ Catalog
(T 2.pid = T 1.pid ∧ T 2.sid
= T 1.sid)
∧T.pid = T 1.pid)}
 - **DRC**
{X|X, Y, Z ∈ Catalog ∧ ∃A, B, C
(A, B, C ∈ Catalog ∧ B = Y ∧ A
= X)}
 - **SQL**   
SELECT C.pid
FROM Catalog C
WHERE EXISTS (SELECT C1.sid
FROM Catalog C1
WHERE C1.pid = C.pid AND C1.sid
= C.sid )

11. - **RA**   
ρ(R1, πsidσsname=Y osemiteShamSuppliers)
ρ(R2, R1  Catalog)
ρ(R3, R2)
ρ(R4(1 → sid, 2 → pid, 3 → cost), σR3.cost<R2.cost(R3 × R2))
πpid(R2 − πsid,pid,costR4)
 - **TRC**   
{T | ∃T 1 ∈ Catalog(∃X ∈ Suppliers
(X.sname = Y osemiteSham ∧ X.sid = T 1.sid) ∧ ¬(∃S ∈ Suppliers
(S.sname = Y osemiteSham ∧ ∃Z ∈ Catalog
(Z.sid = S.sid ∧ Z.cost > T 1.cost))) ∧ T.pid = T 1.pid)
 - **DRC**   
{Y |X, Y, Z ∈ Catalog ∧ ∃A, B, C
(A, B, C ∈ Suppliers ∧ C = Y osemiteSham ∧ A = X)
∧¬(∃P, Q, R(P, Q, R ∈ Suppliers ∧ R = Y osemiteSham
∧∃I, J, K(I, J, K ∈ Catalog(I = P ∧ K>Z))))}
 - **SQL**   
SELECT C.pid
FROM Catalog C, Suppliers S
WHERE S.sname = ‘Yosemite Sham’ AND C.sid = S.sid
AND C.cost ≥ ALL (Select C2.cost
FROM Catalog C2, Suppliers S2
WHERE S2.sname = ‘Yosemite Sham’
AND C2.sid = S2.sid)

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
1. - **RA**   
πeid(σaname=‘Boeing (Aircraf t  Certif ied))
 - **TRC**   
{C.eid | C ∈ Certif ied ∧
∃A ∈ Aircraf t(A.aid = C.aid ∧ A.aname = ‘Boeing
)}
 - **DRC**   
{Ceid|Ceid, Caid ∈ Certif ied ∧
∃Aid, AN, AR(Aid, AN, AR ∈ Aircraf t
∧Aid = Caid ∧ AN = ‘Boeing
)}
 - **SQL**   
SELECT C.eid
FROM Aircraft A, Certified C
WHERE A.aid = C.aid AND A.aname = ‘Boeing’
2. - **RA**   
πename(σaname=‘Boeing (Aircraf t  Certif ied  Employees))
 - **TRC**
{E.ename | E ∈ Employees ∧ ∃C ∈ Certif ied
(∃A ∈ Aircraf t(A.aid = C.aid ∧ A.aname = ‘Boeing ∧ E.eid = C.eid))}
 - **DRC**   
{EN|Eid, EN, ES ∈ Employees∧
∃Ceid, Caid(Ceid, Caid ∈ Certif ied∧
∃Aid, AN, AR(Aid, AN, AR ∈ Aircraf t∧
Aid = Caid ∧ AN = ‘Boeing ∧ Eid = Ceid)}
 - **SQL**   
SELECT E.ename
FROM Aircraft A, Certified C, Employees E
WHERE A.aid = C.aid AND A.aname = ‘Boeing’ AND E.eid = C.eid
3.  - **RA**   
ρ(BonnT oM adrid, σf rom=‘Bonn∧to=‘Madrid (Flights))
πaid(σcruisingrange>distance(Aircraf t × BonnT oM adrid))
 - **TRC**   
{A.aid | A ∈ Aircraf t ∧ ∃F ∈ Flights
(F.from = ‘Bonn ∧ F.to = ‘M adrid ∧ A.cruisingrange > F.distance)}
 - **DRC**   
{Aid | Aid, AN, AR ∈ Aircraf t∧
(∃F N, F F, F T, FDi, FDe, F A(F N, F F, F T, FDi, FDe, F A ∈ Flights∧
F F = ‘Bonn ∧ F T = ‘M adrid ∧ F Di < AR))}
 - **SQL**   
SELECT A.aid
FROM Aircraft A, Flights F
WHERE F.from = ‘Bonn’ AND F.to = ‘Madrid’ AND
A.cruisingrange > F.distance
4.  - **RA**   
πf lno(σdistance<cruisingrange∧salary>100,000(Flights  Aircraf t 
Certif ied  Employees)))
 - **TRC**    {F.flno | F ∈ Flights ∧ ∃A ∈ Aircraf t∃C ∈ Certif ied
∃E ∈ Employees(A.cruisingrange > F.distance ∧ E.salary > 100, 000∧
A.aid = C.
40 Chapter 4
5.  - **RA**    ρ(R1, πeid(σcruisingrange>3000(Aircraf t  Certif ied)))
πename(Employees  (R1 − πeid(σaname=‘Boeing (Aircraf t  Certif ied))))
 - **TRC**   
{E.ename | E ∈ Employees ∧ ∃C ∈ Certif ied(∃A ∈ Aircraf t
(A.aid = C.aid ∧ E.eid = C.eid ∧ A.cruisingrange > 3000))∧
¬(∃C2 ∈ Certif ied(∃A2 ∈ Aircraf t(A2.aname = ‘Boeing ∧ C2.aid =
A2.aid ∧ C2.eid = E.eid)))}
 - **DRC**   
{EN|Eid, EN, ES ∈ Employees∧
∃Ceid, Caid(Ceid, Caid ∈ Certif ied∧
∃Aid, AN, AR(Aid, AN, AR ∈ Aircraf t∧
Aid = Caid ∧ Eid = Ceid ∧ AR > 3000))∧
¬(∃Aid2, AN2, AR2(Aid2, AN2, AR2 ∈ Aircraf t∧
∃Ceid2, Caid2(Ceid2, Caid2 ∈ Certif ied
∧Aid2 = Caid2 ∧ Eid = Ceid2 ∧ AN2=‘Boeing
)))}
 - **SQL**   
SELECT E.ename
FROM Certified C, Employees E, Aircraft A
WHERE A.aid = C.aid AND E.eid = C.eid AND A.cruisingrange > 3000
AND E.eid NOT IN ( SELECT C2.eid
FROM Certified C2, Aircraft A2
WHERE C2.aid = A2.aid AND A2.aname = ‘Boeing’ )
6.  - **RA**   
The approach to take is first find all the employees who do not have the
highest salary. Subtract these from the original list of employees and what
is left is the highest paid employees.
ρ(E1, Employees)
ρ(E2, Employees)
ρ(E3, πE2.eid(E1 E1.salary>E2.salary E2)
(πeidE1) − E3
 - **TRC**   
{E1.eid | E1 ∈ Employees∧¬(∃E2 ∈ Employees(E2.salary > E1.salary))}
 - **DRC**   
{Eid1|Eid1,EN1,ES1 ∈ Employees∧
¬(∃Eid2,EN2,ES2(Eid2,EN2,ES2 ∈ Employees ∧ ES2 > ES1))}
 - **SQL**   
SELECT E.eid
FROM Employees E
WHERE E.salary = ( Select MAX (E2.salary)
FROM Employees E2 )
7.  - **RA**   
The approach taken is similar to the solution for the previous exercise. First
find all the employees who do not have the highest salary. Remove these from
the original list of employees and what is left is the highest paid employees.
Remove the highest paid employees from the original list. What is left is the
second highest paid employees together with the rest of the employees. Then
find the highest paid employees of this new list. This is the list of the second
highest paid employees.
ρ(E1, Employees)
ρ(E2, Employees)
ρ(E3, πE2.eid(E1 E1.salary>E2.salary E2)
ρ(E4, E2  E3)
ρ(E5, E2  E3)
ρ(E6, πE5.eid(E4 E1.salary>E5.salary E5)
(πeidE3) − E6
 - **TRC**   
{E1.eid | E1 ∈ Employees ∧ ∃E2 ∈ Employees(E2.salary > E1.salary
∧¬(∃E3 ∈ Employees(E3.salary > E2.salary)))}
 - **DRC**   
{Eid1|Eid1,EN1,ES1 ∈ Employees∧
∃Eid2,EN2,ES2(Eid2,EN2,ES2 ∈ Employees(ES2 > ES1)
∧¬(∃Eid3,EN3,ES3(Eid3,EN3,ES3 ∈ Employees(ES3 > ES2))))}
 - **SQL**   
SELECT E.eid
FROM Employees E
WHERE E.salary = (SELECT MAX (E2.salary)
FROM Employees E2
WHERE E2.salary
= (SELECT MAX (E3.salary)
FROM Employees E3 ))
42 Chapter 4
8. This cannot be expressed in relational algebra (or calculus) because there is no
operator to count, and this query requires the ability to count up to a number
that depends on the data. The query can however be expressed in SQL as follows:   
SELECT Temp.eid
FROM ( SELECT C.eid AS eid, COUNT (C.aid) AS cnt,
FROM Certified C
GROUP BY C.eid) AS Temp
WHERE Temp.cnt = ( SELECT MAX (Temp.cnt)
FROM Temp)
9.  - **RA**   
The approach behind this query is to first find the employees who are certified
for at least three aircraft (they appear at least three times in the Certified
relation). Then find the employees who are certified for at least four aircraft.
Subtract the second from the first and what is left is the employees who are
certified for exactly three aircraft.
ρ(R1, Certif ied)
ρ(R2, Certif ied)
ρ(R3, Certif ied)
ρ(R4, Certif ied)
ρ(R5, πeid(σ(R1.eid=R2.eid=R3.eid)∧(R1.aid=R2.aid=R3.aid) (R1 × R2 × R3)))
ρ(R6, πeid(σ(R1.eid=R2.eid=R3.eid=R4.eid)∧(R1.aid=R2.aid=R3.aid=R4.aid)
(R1 × R2 × R3 × R4)))
R5 − R6
 - **TRC**   
{C1.eid | C1 ∈ Certif ied ∧ ∃C2 ∈ Certif ied(∃C3 ∈ Certif ied
(C1.eid = C2.eid ∧ C2.eid = C3.eid∧
C1.aid
= C2.aid ∧ C2.aid
= C3.aid ∧ C3.aid
= C1.aid∧
¬(∃C4 ∈ Certif ied
(C3.eid = C4.eid ∧ C1.aid
= C4.aid∧
C2.aid
= C4.aid ∧ C3.aid
= C4.aid))))}
 - **DRC**   
{CE1|CE1,CA1 ∈ Certif ied∧
∃CE2,CA2(CE2,CA2 ∈ Certif ied∧
∃CE3,CA3(CE3,CA3 ∈ Certif ied∧
(CE1 = CE2 ∧ CE2 = CE3∧
CA1
= CA2 ∧ CA2
= CA3 ∧ CA3
= CA1∧
¬(∃CE4,CA4(CE4,CA4 ∈ Certif ied∧
(CE3 = CE4 ∧ CA1
= CA4∧
CA2
= CA4 ∧ CA3
= CA4))))}
 - **SQL**   
SELECT C1.eid
FROM Certified C1, Certified C2, Certified C3
WHERE (C1.eid = C2.eid AND C2.eid = C3.eid AND
C1.aid
= C2.aid AND C2.aid
= C3.aid AND C3.aid
= C1.aid)
EXCEPT
SELECT C4.eid
FROM Certified C4, Certified C5, Certified C6, Certified C7,
WHERE (C4.eid = C5.eid AND C5.eid = C6.eid AND C6.eid = C7.eid AND
C4.aid
= C5.aid AND C4.aid
= C6.aid AND C4.aid
= C7.aid AND
C5.aid
= C6.aid AND C5.aid
= C7.aid AND C6.aid
= C7.aid )
This could also be done in SQL using COUNT.
10. This cannot be expressed in relational algebra (or calculus) because there is no
operator to sum values. The query can however be expressed in SQL as follows:
SELECT SUM (E.salaries)
FROM Employees E
11. This cannot be expressed in relational algebra or relational calculus or SQL. The
problem is that there is no restriction on the number of intermediate flights. All
of the query methods could find if there was a flight directly from Madison to
Timbuktu and if there was a sequence of two flights that started in Madison and
ended in Timbuktu. They could even find a sequence of n flights that started in
Madison and ended in Timbuktu as long as there is a static (i.e., data-independent)
upper bound on the number of intermediate flights. (For large n, this would of
course be long and impractical, but at least possible.) In this query, however, the
upper bound is not static but dynamic (based upon the set of tuples in the Flights
relation).
In summary, if we had a static upper bound (say k), we could write an algebra
or SQL query that repeatedly computes (upto k) joins on the Flights relation. If
the upper bound is dynamic, then we cannot write such a query because k is not
known when writing the query

***
### Exercise 4.6
What is relational completeness? If a query language is relationally complete, can you write any desired query in that language?

#### `Answer`

***
### Exercise 4.7
What is an unsafe query? Give an example and explain why it is important
to disallow such queries.

#### `Answer`
An unsafe query is a query in relational calculus that has an infinite
number of results. An example of such a query is:   
{S | ¬(S ∈ Sailors)}   
The query is for all things that are not sailors which of course is everything else. Clearly
there is an infinite number of answers, and this query is unsafe. It is important to
disallow unsafe queries because we want to be able to get back to users with a list of
all the answers to a query after a finite amount of time.


***
