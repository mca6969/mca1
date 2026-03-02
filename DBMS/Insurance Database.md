# Insurance Database.
![Alternative text for the image](https://github.com/mca6969/mca1/blob/5817bb49ebb6a5b095aa2b242b9a1679033f3d4b/DBMS/ER_SR/Insurance%20Database.png)

![Alternative text for the image](https://github.com/mca6969/mca1/blob/5817bb49ebb6a5b095aa2b242b9a1679033f3d4b/DBMS/ER_SR/Insurance%20RS.png)

### Create the above tables by properly specifying the integrity constraints.
```
CREATE TABLE PERSON (
 DRIVERID VARCHAR(10) PRIMARY KEY,
 NAME VARCHAR(50),
 ADDRESS VARCHAR(100)
);
CREATE TABLE CAR (
 REGNO VARCHAR(10) PRIMARY KEY,
 MODEL VARCHAR(50),
 YEAR INT
);
CREATE TABLE ACCIDENT (
 REPNO INT PRIMARY KEY,
 DATEOFACCIDENT DATE,
 LOCATION VARCHAR(50)
Sunil’s notion:DBMS JOURNAL 5
);
CREATE TABLE OWNS (
 DRIVERID VARCHAR(10),
 REGNO VARCHAR(10),
 FOREIGN KEY (DRIVERID) REFERENCES PERSON(DRIVERID),
 FOREIGN KEY (REGNO) REFERENCES CAR(REGNO)
);
CREATE TABLE PARTICIPATED (
 DRIVERID VARCHAR(10),
 REGNO VARCHAR(10),
 REPNO INT,
 DAMAGEAMT INT,
 FOREIGN KEY (DRIVERID) REFERENCES PERSON(DRIVERID),
 FOREIGN KEY (REGNO) REFERENCES CAR(REGNO),
 FOREIGN KEY (REPNO) REFERENCES ACCIDENT(REPNO)
);
```
### Enter at least five tuples for each relation.
```
INSERT INTO PERSON VALUES
('D001','Ravi','Bangalore'),
('D002','Sunil','Belgaum'),
('D003','Priya','Mysore'),
('D004','Arjun','Hubli'),
('D005','Meena','Dharwad');

INSERT INTO CAR VALUES
('KA01AB1234','Swift',2002),
('KA02CD5678','i20',2002),
('KA03EF9012','Baleno',2003),
('KA04GH3456','Creta',2002),
('KA05IJ7890','Innova',2004);

INSERT INTO ACCIDENT VALUES
(11,'2002-05-12','MG Road'),
(12,'2002-06-20','NH4'),
(13,'2003-07-15','Ring Road'),
(14,'2002-08-05','Airport Road'),
(15,'2004-09-10','Railway Station');

INSERT INTO OWNS VALUES
('D001','KA01AB1234'),
('D002','KA02CD5678'),
('D003','KA03EF9012'),
('D004','KA04GH3456'),
('D005','KA05IJ7890');

INSERT INTO PARTICIPATED VALUES
('D001','KA01AB1234',11,15000),
('D002','KA02CD5678',12,20000),
('D003','KA03EF9012',13,12000),
('D004','KA04GH3456',14,25000),
('D005','KA05IJ7890',15,18000);
```

### Update the damage amount for the car with a specific Regno in the accident with report number 12 to 25000.
```
UPDATE PARTICIPATED
SET DAMAGEAMT = 25000
Sunil’s notion:DBMS JOURNAL 7
WHERE REGNO = 'KA02CD5678' AND REPNO = 12;
```
### Add a new accident to the database
```
INSERT INTO ACCIDENT VALUES(16,'2005-01-22','College Road');
```
### Find the total number of people who owned cars that were involved in accidents in 2002.
```
SELECT COUNT(DISTINCT DRIVER_ID) AS TOTAL_PEOPLE
FROM PARTICIPATED
WHERE REPORT_NO IN (
 SELECT REPORT_NO
 FROM ACCIDENT
 WHERE DATE = '05-Aug-2002'
);
```
### Find the number of accidents in which cars belonging to a specific model were involved.
```
SELECT COUNT(DISTINCT A.REPNO) AS AccidentCount
FROM ACCIDENT A
JOIN PARTICIPATED PA ON A.REPNO = PA.REPNO
JOIN CAR C ON PA.REGNO = C.REGNO
WHERE C.MODEL = 'Swift';
```
