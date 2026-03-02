# Movie Database
![Alternative text for the image](https://github.com/mca6969/mca1/blob/5817bb49ebb6a5b095aa2b242b9a1679033f3d4b/DBMS/ER_SR/Movie%20database.png)

### Map the ER model to Relational schema and normalize the relations to 2NF.
![Alternative text for the image](https://github.com/mca6969/mca1/blob/5817bb49ebb6a5b095aa2b242b9a1679033f3d4b/DBMS/ER_SR/Movie%20RS.png)

### Create the tables & insert at least 8 tuples in each relation.
```
CREATE TABLE Production (
 name VARCHAR(50) PRIMARY KEY,
 address VARCHAR(100),
 no_of_movies INT
);

CREATE TABLE Movie (
 title VARCHAR(100),
 year INT,
 length INT,
 genre VARCHAR(30),
 plot TEXT,
 prod_name VARCHAR(50),
 PRIMARY KEY (title, year),
 FOREIGN KEY (prod_name) REFERENCES Production(name)
);

CREATE TABLE Actor (
 act_id INT PRIMARY KEY,
 name VARCHAR(50),
 dob DATE
);

CREATE TABLE Director (
 dir_id INT PRIMARY KEY,
 name VARCHAR(50),
 dob DATE
);

CREATE TABLE Acts_in (
 act_id INT,
 title VARCHAR(100),
 year INT,
 role VARCHAR(50),
 PRIMARY KEY (act_id, title, year),
 FOREIGN KEY (act_id) REFERENCES Actor(act_id),
 FOREIGN KEY (title, year) REFERENCES Movie(title, year)
);

CREATE TABLE Directs (
 dir_id INT,
 title VARCHAR(100),
 year INT,
 PRIMARY KEY (dir_id, title, year),
 FOREIGN KEY (dir_id) REFERENCES Director(dir_id),
 FOREIGN KEY (title, year) REFERENCES Movie(title, year)
);

CREATE TABLE Also_act (
 dir_id INT,
 title VARCHAR(100),
 year INT,
 role VARCHAR(50),
 PRIMARY KEY (dir_id, title, year),
 FOREIGN KEY (dir_id) REFERENCES Director(dir_id),
 FOREIGN KEY (title, year) REFERENCES Movie(title, year)
);

INSERT INTO Production VALUES ('Yash Raj Films','Mumbai',2);
INSERT INTO Production VALUES ('Dharma Productions','Mumbai',1);
INSERT INTO Production VALUES ('Hombale Films','Bengaluru',2);
INSERT INTO Production VALUES ('Red Chillies','Delhi',1);
INSERT INTO Production VALUES ('Rajkumar Films','Bengaluru',1);
INSERT INTO Production VALUES ('UTV Motion Pictures','Mumbai',1);
INSERT INTO Production VALUES ('Balaji Motion Pictures','Mumbai',0);
INSERT INTO Production VALUES ('Annapurna Studios','Hyderabad',0);

INSERT INTO Movie VALUES ('Dark Shadows',2012,120,'Horror','Vampire plot','Yash Raj Films');
INSERT INTO Movie VALUES ('Scary Night',2012,110,'Horror','Haunted house','Dharma Productions');
INSERT INTO Movie VALUES ('KGF',2018,155,'Action','Rise ofRocky','Hombale Films');
INSERT INTO Movie VALUES ('KGF',2022,170,'Action','Rocky rules','Hombale Films');
INSERT INTO Movie VALUES ('Love Story',1999,140,'Romance','Classic love','Rajkumar Films');
INSERT INTO Movie VALUES ('Love Story',2015,125,'Romance','Modern love','Red Chillies');
INSERT INTO Movie VALUES ('Lagaan',2001,224,'Drama','Cricket against British','UTV Motion Pictures');
INSERT INTO Movie VALUES ('Dreamscape',2020,145,'Fantasy','Dream adventures','Yash Raj Films');

INSERT INTO Actor VALUES (1,'Yash','1986-01-08');
INSERT INTO Actor VALUES (2,'Srinidhi Shetty','1992-10-21');
INSERT INTO Actor VALUES (3,'Amitabh Bachchan','1942-10-11');
INSERT INTO Actor VALUES (4,'Hema Malini','1948-10-16');
INSERT INTO Actor VALUES (5,'Shah Rukh Khan','1965-11-02');
INSERT INTO Actor VALUES (6,'Kajol','1974-08-05');
INSERT INTO Actor VALUES (7,'Aamir Khan','1965-03-14');
INSERT INTO Actor VALUES (8,'Preity Zinta','1975-01-31');

INSERT INTO Director VALUES (101,'Tim Burton','1958-08-25');
INSERT INTO Director VALUES (102,'James Wan','1977-02-26');
INSERT INTO Director VALUES (103,'Steven Spielberg','1946-12-18');
INSERT INTO Director VALUES (104,'Christopher Nolan','1970-07-30');
INSERT INTO Director VALUES (105,'Karan Johar','1972-05-25');
INSERT INTO Director VALUES (106,'Ashutosh Gowariker','1964-02-15');
INSERT INTO Director VALUES (107,'Kajol','1974-08-05');
INSERT INTO Director VALUES (108,'Prashanth Neel','1980-06-04');

INSERT INTO Acts_in VALUES (1,'KGF',2018,'Lead');
INSERT INTO Acts_in VALUES (2,'KGF',2018,'Heroine');
INSERT INTO Acts_in VALUES (1,'KGF',2022,'Lead');
INSERT INTO Acts_in VALUES (2,'KGF',2022,'Heroine');
INSERT INTO Acts_in VALUES (3,'Love Story',1999,'Lead');
INSERT INTO Acts_in VALUES (4,'Love Story',1999,'Heroine');
INSERT INTO Acts_in VALUES (5,'Love Story',2015,'Lead');
INSERT INTO Acts_in VALUES (6,'Love Story',2015,'Heroine');

INSERT INTO Directs VALUES (101,'Dark Shadows',2012);
INSERT INTO Directs VALUES (102,'Dark Shadows',2012);
INSERT INTO Directs VALUES (103,'Dark Shadows',2012);
INSERT INTO Directs VALUES (104,'Scary Night',2012);
INSERT INTO Directs VALUES (107,'Love Story',1999);
INSERT INTO Directs VALUES (105,'Love Story',2015);
INSERT INTO Directs VALUES (108,'KGF',2018);
INSERT INTO Directs VALUES (108,'KGF',2022);

INSERT INTO Also_act VALUES (101,'Dark Shadows',2012,'Cameo');
INSERT INTO Also_act VALUES (102,'Scary Night',2012,'Villager');
INSERT INTO Also_act VALUES (103,'Love Story',2015,'Guest');
INSERT INTO Also_act VALUES (104,'Lagaan',2001,'Coach cameo');
INSERT INTO Also_act VALUES (105,'Love Story',2015,'Spy cameo');
INSERT INTO Also_act VALUES (106,'Love Story',1999,'Fathercameo');
INSERT INTO Also_act VALUES (107,'Love Story',2015,'Heroinecameo');
INSERT INTO Also_act VALUES (108,'KGF',2018,'Villager cameo');
```

### List the details of horror movies released in 2012 and directed by more than 2 directors.
```
SELECT m.title, m.year, m.length, m.genre, COUNT(d.dir_id)
AS director_count
FROM movie m
JOIN directs d ON m.title = d.title AND m.year = d.year
WHERE m.genre = 'Horror' AND m.year = 2012
GROUP BY m.title, m.year, m.length, m.genre
HAVING COUNT(d.dir_id) > 2;
```
### List the details of actors who acted in movies having same titles but released before 2000 and after 2010.
```
SELECT DISTINCT a.*
FROM actor a
JOIN acts_in ai1 ON a.act_id = ai1.act_id
JOIN acts_in ai2 ON a.act_id = ai2.act_id
WHERE ai1.title = ai2.title
 AND ai1.year < 2000
 AND ai2.year > 2010;
 ```

### List the details of production companies producing maximum movies.
```
SELECT p.*
FROM production p
JOIN movie m ON p.name = m.prod_name
GROUP BY p.name, p.address, p.no_of_movies
ORDER BY COUNT(m.title) DESC
LIMIT 1;
```

### List the details of movies where director and actor have same date of birth.
```
SELECT DISTINCT m.title, m.year, d.name AS director_name,
a.name AS actor_name
FROM movie m
JOIN directs di ON m.title = di.title AND m.year = di.year
JOIN director d ON di.dir_id = d.dir_id
JOIN acts_in ai ON m.title = ai.title AND m.year = ai.year
JOIN actor a ON ai.act_id = a.act_id
WHERE d.dob = a.dob;
```
### Retrieve the names of directors directed all the movies produced by any one production company.
```
SELECT d.name
FROM director d
Sunil’s notion:DBMS JOURNAL 15
WHERE NOT EXISTS (
 SELECT m.title, m.year
 FROM movie m
 WHERE m.prod_name = 'Warner Bros'
 AND NOT EXISTS (
 SELECT 1
 FROM directs di
 WHERE di.dir_id = d.dir_id
 AND di.title = m.title
 AND di.year = m.year
 )
);
```