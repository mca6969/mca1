# Student-Enrollment Database.
```
Consider the following relations:
Student(snum: integer, sname: string, major: string, level: string, age: integer)
Class(name: string, meets at: string, room: string, fid: integer)
Enrolled(snum: integer, cname: string)
Faculty(fid: integer, fname: string, deptid: integer)
Enrolled has one record per Student-class pair such that the student is enrolled in the
class. Develop an ER schema by reverse engineering from the above relational schema.
Write the following queries in SQL.
1. Create the above tables by properly specifying all the integrity constraints.
2. Insert at least five tuples into each table. 
3. Find the names of all Juniors (level=JR) who are enrolled in a class taught by I.John.
4. For each level, print the level and the average age of students for that level.
5. Find the names of students not enrolled in any class
```

# Insurance Database.
```
Consider the insurance database given below.
PERSON (driverid: String, name: String, address: String)
CAR (regno: String, model: String, year: Int)
ACCIDENT (repno: Int, dat: Date, location: String)
OWNS (driverid: String, regno: String)
PARTICIPATED (driverid: String, regno: String, repno: Int,damageamt: Int)
Develop an ER schema by reverse engineering from the above relational schema. Write
the following queries in SQL.
1. Create the above tables by properly specifying the integrity constraints.
2. Enter at least five tuples for each relation.
3. Demonstrate how you
• Update the damage amount for the car with a specific Regno in the accident with
report number 12 to 25000
• Add a new accident to the database
4. Find the total number of people who owned cars that were involved in accidents in
2002.
5. Find the number of accidents in which cars belonging to a specific model were
involved.
```
# Movie Database
```
• Each movie is identified by title and year of release. Each movie has length in
minutes and classified under one genres (like action, horror etc.). Each movie has a
plot outline.
• Production companies are identified by name and each has an address. A production
company produces one or more movies.
• Actors are identified by id. Other details like name and date of birth of actors are
also stored. Each actor acts in one or more movies. Each actor has a role in movie.
• Directors are identified by id. Other details like name and date of birth of directors
are also stored. A Director can act in a movie (including the one that he or she may
also direct). Each director directs one or more movies.
• Each movie has one or more actors and one or more directors and is produced by a
production company.
Draw an ER diagram that captures the preceding information. Identify any constraints
not captured by the ER diagram.
1. Map the ER model to Relational schema and normalize the relations to 2NF.
2. Create the tables & insert at least 8 tuples in each relation.
3. Solve the following queries in SQL:-
a. List the details of horror movies released in 2012 and directed by more than 2
directors.
b. List the details of actors who acted in movies having same titles but released
before 2000 and after 2010.
c. List the details of production companies producing maximum movies.
d. List the details of movies where director and actor have same date of birth.
e. Retrieve the names of directors directed all the movies produced by any one
production company.
```

# Bank Database.
```
Address and phone for each bank are also stored. Each branch is identified by its bank.
Branch has name address and phone. A customer can open different kinds of accounts
with the branches. An account can belong to more than one customer. Customers are
identified by their SSN, name, address and phone number. There are different types of
loans, each identified by a loan number. A customer can take more than one type of
loan and a loan can be given to more than one customer. Loans have a duration and
interest rate. Make suitable assumptions and use them in showing maximum and
minimum cardinality ratios.
1. Draw an ER diagram that captures the preceding information. Identify any
constraints not captured by the ER diagram.
2. Map the ER model to Relational schema and normalize the relations to 2NF.
3. Create the tables & insert at least 8 tuples in each relation.
4. Solve the following queries in SQL:-
a. List the details of customers who have joint account and also have at least one
loan.
b. List the details of the branch that has given the maximum loan.
c. List the details of savings accounts opened in the SBI branches located at
Bangalore.
d. List the name of branch along with its bank name and total amount of loan
given by it.
e. Retrieve the names of customers who have accounts in all the branches located
in a specific city.
```
# Pharmacy Database.
```
The Prescriptions-R-X chain of pharmacies has offered to give you a free lifetime
supply of medicine if you design its database. Given the rising cost of health care, you
agree. Here’s the information that you gather:
• Patients are identified by an SSN, and their names, addresses, and ages must be
recorded.
• Doctors are identified by an SSN. For each doctor, the name, specialty, and years
of experience must be recorded.
• Each pharmaceutical company is identified by name and has a phone number.
• For each drug, the trade name and formula must be recorded. Each drug is sold by
a given pharmaceutical company, and the trade name identifies a drug uniquely
from among the products of that company. If a pharmaceutical company is deleted,
you need not keep track of its products any longer.
• Each pharmacy has a name, address, and phone number.
• Every patient has a primary physician. Every doctor has at least one patient.
• Each pharmacy sells several drugs and has a price for each. A drug could be sold
at several pharmacies, and the price could vary from one pharmacy to another.
• Doctors prescribe drugs for patients. A doctor could prescribe one or more drugs
for several patients, and a patient could obtain prescriptions from several doctors.
• Each prescription has a date and a quantity associated with it. You can assume that,
if a doctor prescribes the same drug for the same patient more than once, only the
last such prescription needs to be stored.
• Pharmaceutical companies have long-term contracts with pharmacies. A
pharmaceutical company can contract with several pharmacies, and a pharmacy
can contract with several pharmaceutical companies. For each contract, you have
to store a start date, an end date, and the text of the contract.
• Pharmacies appoint a supervisor for each contract. There must always be a
supervisor for each contract, but the contract supervisor can change over the
lifetime of the contract.
1. Draw an ER diagram that captures the preceding information. Identify any
constraints not captured by the ER diagram.
2. Map the ER model to Relational schema and normalize the relations to 2NF.
3. Create the tables & insert at least 8 tuples in each relation.
4. Solve the following queries in SQL:-
a. For each patient list out the patient’s name, patient’s doctor’s name &
prescription details. b. For each pharmacy list out the drugs that it sells,
containing Paracetemol as one of the ingredient in its formula along with its
Pharmaceutical Company.
b. Produce a listing Pharmacy name, Pharmaceutical company, Drug trade name,
contract start date & end date, supervisor for each contract between a Pharmacy
& Pharmaceutical Company.
c. For each doctor display the doctor’s name and the count of prescriptions given
by doctor containing the drugs made by NAVYYA LABS.
d. For each patient display the patient’s name, drug name & the pharmacy name
from where the patient bought the drug.
```




