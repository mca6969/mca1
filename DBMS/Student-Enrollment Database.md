# Student-Enrollment Database.
![Alternative text for the image](https://github.com/mca6969/mca1/blob/61d949b77ca92821a8ad80fdd14f900c94d1b528/DBMS/Screenshot%202026-03-01%20202146.png)

### Create the above tables by properly specifying all the integrity constraints.
```
CREATE TABLE Student (
 snum INT PRIMARY KEY,
 sname VARCHAR(50) NOT NULL,
 major VARCHAR(30),
 level VARCHAR(10),
 age INT 
);
CREATE TABLE Faculty (
 fid INT PRIMARY KEY,
 fname VARCHAR(50) ,
 deptid INT 
);
CREATE TABLE Class (
 name VARCHAR(50) PRIMARY KEY,
 meets_at VARCHAR(20),
 room VARCHAR(20),
 fid INT,
 FOREIGN KEY (fid) REFERENCES Faculty(fid)
);
CREATE TABLE Enrolled (
 snum INT,
 cname VARCHAR(50),
 PRIMARY KEY (snum, cname),
 FOREIGN KEY (snum) REFERENCES Student(snum),
 FOREIGN KEY (cname) REFERENCES Class(name)
);
```
### Insert at least five tuples into each table. 
```
INSERT INTO Student VALUES (1, 'Alice', 'CS', 'JR', 20);
INSERT INTO Student VALUES (2, 'Bob', 'Math', 'SR', 21);
INSERT INTO Student VALUES (3, 'Charlie', 'Physics', 'JR',22);
INSERT INTO Student VALUES (4, 'Diana', 'CS', 'FR', 18);
INSERT INTO Student VALUES (5, 'Ethan', 'Biology', 'PG', 25);

INSERT INTO Faculty VALUES (101, 'I.John', 10);
INSERT INTO Faculty VALUES (102, 'Dr. Johnson', 20);
INSERT INTO Faculty VALUES (103, 'Dr. Lee', 30);
INSERT INTO Faculty VALUES (104, 'Dr. Patel', 40);
INSERT INTO Faculty VALUES (105, 'Dr. Brown', 50);

INSERT INTO Class VALUES ('DBMS', 'Mon 10AM', 'R101', 101);
INSERT INTO Class VALUES ('Algorithms', 'Tue 2PM', 'R102',102);
INSERT INTO Class VALUES ('Networks', 'Wed 11AM', 'R103', 103);
INSERT INTO Class VALUES ('Biology', 'Thu 9AM', 'R104', 104);
INSERT INTO Class VALUES ('Physics', 'Fri 3PM', 'R105', 105);

INSERT INTO Enrolled VALUES (1, 'DBMS');
INSERT INTO Enrolled VALUES (2, 'Algorithms');
INSERT INTO Enrolled VALUES (3, 'Physics');
INSERT INTO Enrolled VALUES (3, 'DBMS');
INSERT INTO Enrolled VALUES (4, 'Networks');
```
### Find the names of all Juniors (level=JR) who are enrolled in a class taught by I.John.
```
SELECT * FROM Student ,faculty WHERE level='JR' and fname='i.john';
```
### For each level, print the level and the average age of students for that level.
``` 
SELECT level, AVG(age) AS avg_age
FROM Student
GROUP BY level;
```
### Find the names of students not enrolled in any class
```
SELECT s.sname
FROM Student s
WHERE s.snum NOT IN (
 SELECT e.snum FROM Enrolled e
);
```








