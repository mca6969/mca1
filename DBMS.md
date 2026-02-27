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


