# Database Management Systems - Chapter 2 Solutions

### Exercise 2.1
Explain the following terms briefly: attribute, domain, entity, relationship, entity set, relationship set, one-to-many relationship, many-to-many relationship, participation constraint, overlap constraint, covering constraint, weak entity set, aggregation, and role
indicator.

### `Answer`

***


### Exercise 2.2
A university database contains information about professors (identified by social security number, or SSN) and courses (identified by course id). Professors teach courses; each of the following situations concerns the Teaches relationship set. For each situation, draw an ER diagram that describes it (assuming no further constraints hold).
1. Professors can teach the same course in several semesters, and each offering must be recorded.
2. Professors can teach the same course in several semesters, and only the most recent such offering needs to be recorded. (Assume this condition applies in all subsequent questions. )
3. Every professor must teach some course.
4. Every professor teaches exactly one course (no more, no less).
5. Every professor teaches exactly one course (no more, no less), and every course must be taught by some professor.
6. Now suppose that certain courses can be taught by a team of professors jointly, but it is possible that no one professor in a team can teach the course. Model this situation, introducing additional entity sets and relationship sets if necessary.


### `Answer`

***


### Exercise 2.3
Consider the following information about a university database:
1. Professors have an SSN, a name, an age, a rank, and a research specialty.
2. Projects have a project number, a sponsor name (e.g., NSF), a starting date, an ending date, and a budget.
3. Graduate students have an SSN, a name, an age, and a degree program (e.g., M.S. or Ph.D.).
4. Each project is managed by one professor (known as the project's principal investigator).
5. Each project is worked on by one or more professors (known as the project's co-investigators).
6. Professors can manage and/or work on multiple projects.
7. Each project is worked on by one or more graduate students (known as the project's research assistants).
8. When graduate students >'lark on a project, a professor must supervise their work on the project. Graduate students can work on multiple projects, in which case they will have a (potentially different) supervisor for each one.
9. Departments have a department number, a department name, and a main office.
10. Departments have a professor (known as the chairman) who runs the department.
11. Professors work in one or more departments, and for each department that they work
in, a time percentage is associated with their job.
12. Graduate students have one major department in which they are working on their degree.
13. Each graduate student has another, more senior graduate student (known as a student advisor) who advises him or her on what courses to take.

Design and draw an ER diagram that captures the information about the university. Use only the basic ER model here; that is, entities, relationships, and attributes. Be sure to indicate any key and participation constraints.

### `Answer`

***
### Exercise 2.4
A company database needs to store information about employees (identified by SSN, with salary and phone as attributes), departments (identified by DNA, with dname and budget as attributes), and children of employees (with name and age as attributes). Employees work in departments; each department is managed by an employee; a child must be identified uniquely by name when the parent (who is an employee; assume that only one parent works for the company) is known. We are not interested in information about a child once the parent leaves the company.  

Draw an ER diagram that captures this information.

### `Answer`

***


### Exercise 2.5
Notown Records has decided to store information about musicians who perform on its albums (as well as other company data) in a database. The company has wisely chosen to hire you as a database designer (at your usual consulting fee of $2500/day).
1. Each musician that records at Notown has an SSN, a name, an address, and a phone number. Poorly paid musicians often share the same address, and no address has more than one phone.
2. Each instrument used in songs recorded at Notown has a name (e.g., guitar, synthesizer, flute) and a musical key (e.g., C, B-flat, E-flat).
3. Each album recorded on the Notown label has a title, a copyright date, a format (e.g., CD or MC), and an album identifier.
4. Each song recorded at Notown has a title and an author.
5. Each musician may play several instruments, and a given instrument may be played by several musicians.
6. Each album has a number of songs on it, but no song may appear on more than one album.
7. Each song is performed by one or more musicians, and a musician may perform a number of songs.
8. Each album has exactly one musician who acts as its producer. A musician may produce several albums, of course.

Design a conceptual schema for Notown and draw an ER diagram for your schema. The preceding information describes the situation that the Notown database must model. Be sure to indicate all key and cardinality constraints and any assumptions you make. Identify any constraints you are unable to capture in the ER diagram and briefly explain why you could not express them.

### `Answer`

***
### Exercise 2.6
Computer Sciences Department frequent fliers have been complaining to Dane County Airport officials about the poor organization at the airport. As a result, the officials decided that all information related to the airport should be organized using a DBMS, and you have been hired to design the database. Your first task is to organize the information about all the airplanes stationed and maintained at the airport. The relevant information is as follows:
1. Every airplane has a registration number, and each airplane is of a specific model.
2. The airport accommodates a number of airplane models, and each model is identified by a model number (e.g., DC-lO) and has a capacity and a weight.
3. A number of technicians work at the airport. You need to store the name, SSN, address, phone number, and salary of each technician.
4. Each technician is an expert on one or more plane model(s), and his or her expertise may overlap with that of other technicians. This information about technicians must also be recorded.
5. Traffic controllers must have an annual medical examination. For each traffic controller, you must store the date of the most recent exam.
6. All airport employees (including technicians) belong to a union. You must store the union membership number of each employee. You can assume that each employee is uniquely identified by a social security number.
7. The airport has a number of tests that are used periodically to ensure that airplanes are still airworthy. Each test has a Federal Aviation Administration (FAA) test number, a name, and a maximum possible score.
8. The FAA requires the airport to keep track of each time a given airplane is tested by a given technician using a given test. For each testing event, the information needed is the date, the number of hours the technician spent doing the test, and the score the airplane
received on the test.
9. Draw an ER diagram for the airport database. Be sure to indicate the various attributes of each entity and relationship set; also specify the key and participation constraints for each relationship set. Specify any necessary overlap and covering constraints as well (in
English).
10. The FAA passes a regulation that tests on a plane must be conducted by a technician who is an expert on that model. How would you express this constraint in the ER diagram? If you cannot express it, explain briefly.

### `Answer`

***

### Exercise 2.7
The Prescriptions-R-X chain of pharmacies has offered to give you a free lifetime supply of medicine if you design its database. Given the rising cost of health care, you agree. Here's the information that you gather:
1. Patients are identified by an SSN, and their names, addresses, and ages must be recorded.
2. Doctors are identified by an SSN. For each doctor, the name, specialty, and years of experience must be recorded.
3. Each pharmaceutical company is identified by name and has a phone number.
4. For each drug, the trade name and formula must be recorded. Each drug is sold by a given pharmaceutical company, and the trade name identifies a drug uniquely from among the products of that company. If a pharmaceutical company is deleted, you need not keep track of its products any longer.
5. Each pharmacy has a name, address, and phone number.
6. Every patient has a primary physician. Every doctor has at least one patient.
7. Each pharmacy sells several drugs and has a price for each. A drug could be sold at several pharmacies, and the price could vary from one pharmacy to another.
8. Doctors prescribe drugs for patients. A doctor could prescribe one or more drugs for several patients, and a patient could obtain prescriptions from several doctors. Each prescription has a date and a quantity associated with it. You can assume that, if a doctor prescribes the same drug for the same patient more than once, only the last such prescription needs to be stored.
9. Pharmaceutical companies have long-term contracts with pharmacies. A pharmaceutical company can contract with several pharmacies, and a pharmacy can contract with several pharmaceutical companies. For each contract, you have to store a start date, an end date, and the text of the contract.
10. Pharmacies appoint a supervisor for each contract. There must always be a supervisor
for each contract, but the contract supervisor can change over the lifetime of the contract.

Questions -
- Draw an ER diagram that captures the preceding information. Identify any constraints not captured by the ER diagram.
- How would your design change if each drug must be sold at a fixed price by all pharmacies?
- How would your design change if the design requirements change as follows: If a doctor prescribes the same drug for the same patient more than once, several such prescriptions may have to be stored.

### `Answer`

***
### Exercise 2.8
Although you always wanted to be an artist, you ended up being an expert on databases because you love to cook data and you somehow confused database with data baste. Your old love is still there, however, so you set up a database company, ArtBase, that builds a
product for art galleries. The core of this product is a database with a schema that captures all the information that galleries need to maintain. Galleries keep information about artists, their names (which are unique), birthplaces, age, and style of art. For each piece of artwork, the artist, the year it was made, its unique title, its type of art (e.g., painting, lithograph, sculpture, photograph), and its price must be stored. Pieces of artwork are also classified into
groups of various kinds, for example, portraits, still lifes, works by Picasso, or works of the 19th century; a given piece may belong to more than one group. Each group is identified by a name (like those just given) that describes the group. Finally, galleries keep information
about customers. For each customer, galleries keep that person's unique name, address, total amount of dollars spent in the gallery (very important!), and the artists and groups of art that the customer tends to like.  
Draw the ER diagram for the database.

### `Answer`

***
### Exercise 2.9
Answer the following questions.
- Explain the following terms briefly: UML, use case diagrams, statechart diagrams, class diagrams, database diagrams, component diagrams, and deployment diagrams.
- Explain the relationship between ER diagrams and UML.
### `Answer`

***
