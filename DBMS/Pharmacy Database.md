# Pharmacy Database.
![Alternative text for the image](https://github.com/mca6969/mca1/blob/5817bb49ebb6a5b095aa2b242b9a1679033f3d4b/DBMS/ER_SR/Phram.png)

### Map the ER model to Relational schema and normalize the relations to 2NF.
![Alternative text for the image](https://github.com/mca6969/mca1/blob/5817bb49ebb6a5b095aa2b242b9a1679033f3d4b/DBMS/ER_SR/Phrama%20RS.png)

### Create the tables & insert at least 8 tuples in each relation.
```
CREATE TABLE Patient (
 ssn INT PRIMARY KEY,
 name VARCHAR(50),
 address VARCHAR(100),
 age INT,
 doctor_ssn INT
);

CREATE TABLE Doctor (
 ssn INT PRIMARY KEY,
 name VARCHAR(50),
 specialty VARCHAR(50),
 experience INT
);

CREATE TABLE PharmaCompany (
 name VARCHAR(50) PRIMARY KEY,
 phone VARCHAR(15)
);

CREATE TABLE Drug (
 trade_name VARCHAR(50) PRIMARY KEY,
 formula VARCHAR(100),
 company_name VARCHAR(50),
 FOREIGN KEY (company_name) REFERENCES PharmaCompany(name)
);

CREATE TABLE Pharmacy (
 pharm_id INT PRIMARY KEY,
 name VARCHAR(50),
 address VARCHAR(100),
 phone VARCHAR(15)
);

CREATE TABLE Prescription (
 presc_id INT PRIMARY KEY,
 date DATE,
 quantity INT,
 patient_ssn INT,
 doctor_ssn INT,
 trade_name VARCHAR(50),
 pharm_id INT,
 FOREIGN KEY (patient_ssn) REFERENCES Patient(ssn),
 FOREIGN KEY (doctor_ssn) REFERENCES Doctor(ssn),
 FOREIGN KEY (trade_name) REFERENCES Drug(trade_name),
 FOREIGN KEY (pharm_id) REFERENCES Pharmacy(pharm_id)
);

CREATE TABLE Contract (
 contract_id INT PRIMARY KEY,
 company_name VARCHAR(50),
 pharm_id INT,
 start_date DATE,
 end_date DATE,
 supervisor VARCHAR(50),
 FOREIGN KEY (company_name) REFERENCES PharmaCompany(name),
 FOREIGN KEY (pharm_id) REFERENCES Pharmacy(pharm_id)
);

INSERT INTO Patient VALUES
(1,'Sunil','Belgaum',25,101),
(2,'Priya','Bangalore',30,102),
(3,'Rahul','Mumbai',28,103),
(4,'Sneha','Delhi',35,104),
(5,'Arjun','Chennai',40,105),
(6,'Kavya','Kolkata',32,106),
(7,'Ramesh','Pune',29,107),
(8,'Meera','Hyderabad',27,108);

INSERT INTO Doctor VALUES
(101,'Dr. Rao','Cardiology',15),
(102,'Dr. Mehta','Pediatrics',10),
(103,'Dr. Singh','Orthopedic',12),
(104,'Dr. Sharma','Dermatology',8),
(105,'Dr. Das','Neurology',20),
(106,'Dr. Iyer','General',25),
(107,'Dr. Khan','ENT',18),
(108,'Dr. Roy','Oncology',22);

INSERT INTO PharmaCompany VALUES
('NAVYYA LABS','111111111'),
('CIPLA','222222222'),
('SUN PHARMA','333333333'),
('DR REDDYS','444444444'),
('LUPIN','555555555'),
('ZYDUS','666666666'),
('GLENMARK','777777777'),
('TORRENT','888888888');

INSERT INTO Drug VALUES
('Dolo650','Paracetamol + excipients','NAVYYA LABS'),
('Crocin','Paracetamol + caffeine','CIPLA'),
('NeuroAid','Vitamin B complex','SUN PHARMA'),
('SkinCare','Aloe + Vitamin E','DR REDDYS'),
('HeartSafe','Aspirin + statin','LUPIN'),
('ColdRelief','Paracetamol + antihist','ZYDUS'),
('PainAway','Ibuprofen','GLENMARK'),
('CancerMed','Chemo formula','TORRENT');

INSERT INTO Pharmacy VALUES
(201,'MedPlus-BLR','Bangalore','999111111'),
(202,'Apollo-MUM','Mumbai','999222222'),
(203,'Guardian-DEL','Delhi','999333333'),
(204,'MedLife-CHN','Chennai','999444444'),
(205,'Apollo-KOL','Kolkata','999555555'),
(206,'MedPlus-PUNE','Pune','999666666'),
(207,'Apollo-HYD','Hyderabad','999777777'),
(208,'Guardian-BLR','Bangalore','999888888');

INSERT INTO Prescription VALUES
(301,'2025-01-01',10,1,101,'Dolo650',201),
(302,'2025-01-02',5,2,102,'Crocin',201),
(303,'2025-01-03',15,3,103,'NeuroAid',202),
(304,'2025-01-04',20,4,104,'SkinCare',203),
(305,'2025-01-05',25,5,105,'HeartSafe',204),
(306,'2025-01-06',30,6,106,'ColdRelief',205),
(307,'2025-01-07',12,7,107,'PainAway',206),
(308,'2025-01-08',18,8,108,'CancerMed',207);

INSERT INTO Contract VALUES
(401,'NAVYYA LABS',201,'2025-01-01','2026-01-01','Mr. Kumar'),
(402,'CIPLA',202,'2025-02-01','2026-02-01','Ms. Rani'),
(403,'SUN PHARMA',203,'2025-03-01','2026-03-01','Mr. Das'),
(404,'DR REDDYS',204,'2025-04-01','2026-04-01','Ms. Meera'),
(405,'LUPIN',205,'2025-05-01','2026-05-01','Mr. Arjun'),
(406,'ZYDUS',206,'2025-06-01','2026-06-01','Ms. Sneha'),
(407,'GLENMARK',207,'2025-07-01','2026-07-01','Mr. Rahul'),
(408,'TORRENT',208,'2025-08-01','2026-08-01','Ms. Priya');
```
### For each patient list out the patient’s name, patient’s doctor’s name & prescription details. 
``` 
SELECT p.name AS patient, d.name AS doctor, pr.trade_name,
pr.date, pr.quantity
FROM Patient p
JOIN Doctor d ON p.doctor_ssn = d.ssn
JOIN Prescription pr ON p.ssn = pr.patient_ssn;
```
### For each pharmacy list out the drugs that it sells,containing Paracetemol as one of the ingredient in its formula along with its Pharmaceutical Company.
```
SELECT p.name AS patient, d.name AS doctor, pr.trade_name,
pr.date, pr.quantity
FROM Patient p
JOIN Doctor d ON p.doctor_ssn = d.ssn
JOIN Prescription pr ON p.ssn = pr.patient_ssn;
```
### Produce a listing Pharmacy name, Pharmaceutical company, Drug trade name,contract start date & end date, supervisor for each contract between a Pharmacy & Pharmaceutical Company.

### For each doctor display the doctor’s name and the count of prescriptions given by doctor containing the drugs made by NAVYYA LABS.
```
SELECT d.name AS doctor_name, COUNT(pr.presc_id) AS prescri
ption_count
FROM Doctor d
JOIN Prescription pr ON d.ssn = pr.doctor_ssn
JOIN Drug dr ON pr.trade_name = dr.trade_name
WHERE dr.company_name = 'NAVYYA LABS'
GROUP BY d.name;
```
### For each patient display the patient’s name, drug name & the pharmacy name from where the patient bought the drug.
```
SELECT p.name AS patient_name, pr.trade_name AS drug_name,
ph.name AS pharmacy_name
FROM Patient p
JOIN Prescription pr ON p.ssn = pr.patient_ssn
JOIN Pharmacy ph ON pr.pharm_id = ph.pharm_id;
```
