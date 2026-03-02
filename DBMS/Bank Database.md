# Bank Database.
![Alternative text for the image](https://github.com/mca6969/mca1/blob/5817bb49ebb6a5b095aa2b242b9a1679033f3d4b/DBMS/ER_SR/Bank%20Database.png)

### Map the ER model to Relational schema and normalize the relations to 2NF.
![Alternative text for the image](https://github.com/mca6969/mca1/blob/5817bb49ebb6a5b095aa2b242b9a1679033f3d4b/DBMS/ER_SR/Bank%20RS.png)

### Create the tables & insert at least 8 tuples in each relation.
```
CREATE TABLE Bank (
 Bank_ID INT PRIMARY KEY,
 Name VARCHAR(30),
 Address VARCHAR(50),
 Phone VARCHAR(15)
);

CREATE TABLE Branch (
 Branch_ID INT PRIMARY KEY,
 Name VARCHAR(30),
 Address VARCHAR(50),
 Phone VARCHAR(15),
 Bank_ID INT,
 FOREIGN KEY (Bank_ID) REFERENCES Bank(Bank_ID)
);

CREATE TABLE Customer (
 SSN VARCHAR(15) PRIMARY KEY,
 Name VARCHAR(30),
 Address VARCHAR(50),
 Phone VARCHAR(15)
);

CREATE TABLE Account (
 Account_No INT PRIMARY KEY,
 Type VARCHAR(20),
 Balance DECIMAL(10,2),
 Branch_ID INT,
 FOREIGN KEY (Branch_ID) REFERENCES Branch(Branch_ID)
);

CREATE TABLE Loan (
 Loan_No INT PRIMARY KEY,
 Duration INT,
 Interest_Rate DECIMAL(4,2),
 Branch_ID INT,
 FOREIGN KEY (Branch_ID) REFERENCES Branch(Branch_ID)
);

CREATE TABLE Customer_Account (
 SSN VARCHAR(15),
 Account_No INT,
 PRIMARY KEY (SSN, Account_No),
 FOREIGN KEY (SSN) REFERENCES Customer(SSN),
 FOREIGN KEY (Account_No) REFERENCES Account(Account_No)
);

CREATE TABLE Customer_Loan (
 SSN VARCHAR(15),
 Loan_No INT,
 PRIMARY KEY (SSN, Loan_No),
 FOREIGN KEY (SSN) REFERENCES Customer(SSN),
 FOREIGN KEY (Loan_No) REFERENCES Loan(Loan_No)
);

INSERT INTO Bank VALUES (1, 'SBI', 'Bangalore', '080123456');
INSERT INTO Bank VALUES (2, 'ICICI', 'Mumbai', '022987654');
INSERT INTO Bank VALUES (3, 'HDFC', 'Delhi', '011765432');
INSERT INTO Bank VALUES (4, 'Axis', 'Chennai', '044876543');
INSERT INTO Bank VALUES (5, 'PNB', 'Kolkata', '033987654');
INSERT INTO Bank VALUES (6, 'Canara', 'Hyderabad', '040123987');
INSERT INTO Bank VALUES (7, 'Union', 'Pune', '020765432');
INSERT INTO Bank VALUES (8, 'BOI', 'Lucknow', '052212345');

INSERT INTO Branch VALUES (101, 'SBI-Bangalore', 'MG Road','080111111', 1);
INSERT INTO Branch VALUES (102, 'SBI-Mysore', 'Market St','082112345', 1);
INSERT INTO Branch VALUES (103, 'ICICI-Mumbai', 'Andheri','022222222', 2);
INSERT INTO Branch VALUES (104, 'HDFC-Delhi', 'Connaught Place', '011333333', 3);
INSERT INTO Branch VALUES (105, 'Axis-Chennai', 'T Nagar','044444444', 4);
INSERT INTO Branch VALUES (106, 'PNB-Kolkata', 'Park Street', '033555555', 5);
INSERT INTO Branch VALUES (107, 'Canara-Hyderabad', 'Banjara Hills', '040666666', 6);
INSERT INTO Branch VALUES (108, 'Union-Pune', 'FC Road', '020777777', 7);

INSERT INTO Customer VALUES ('C001', 'Raj', 'Bangalore', '9876543210');
INSERT INTO Customer VALUES ('C002', 'Ram', 'Mysore', '8765432109');
INSERT INTO Customer VALUES ('C003', 'Rahul', 'Mumbai', '7654321098');
INSERT INTO Customer VALUES ('C004', 'Rani', 'Delhi', '6543210987');
INSERT INTO Customer VALUES ('C005', 'Raghu', 'Chennai', '5432109876');
INSERT INTO Customer VALUES ('C006', 'Rekha', 'Kolkata', '4321098765');
INSERT INTO Customer VALUES ('C007', 'Ramesh', 'Hyderabad','3210987654');
INSERT INTO Customer VALUES ('C008', 'Rohit', 'Pune', '2109876543');

INSERT INTO Account VALUES (5001, 'Savings', 20000, 101);
INSERT INTO Account VALUES (5002, 'Current', 15000, 102);
INSERT INTO Account VALUES (5003, 'Savings', 30000, 103);
INSERT INTO Account VALUES (5004, 'Savings', 25000, 104);
INSERT INTO Account VALUES (5005, 'Current', 18000, 105);
INSERT INTO Account VALUES (5006, 'Savings', 22000, 106);
INSERT INTO Account VALUES (5007, 'Savings', 27000, 107);
INSERT INTO Account VALUES (5008, 'Current', 16000, 108);

INSERT INTO Loan VALUES (7001, 24, 8.5, 101);
INSERT INTO Loan VALUES (7002, 36, 9.0, 102);
INSERT INTO Loan VALUES (7003, 12, 7.5, 103);
INSERT INTO Loan VALUES (7004, 48, 10.0, 104);
INSERT INTO Loan VALUES (7005, 60, 11.0, 105);
INSERT INTO Loan VALUES (7006, 18, 8.0, 106);
INSERT INTO Loan VALUES (7007, 24, 9.5, 107);
INSERT INTO Loan VALUES (7008, 36, 9.2, 108);

INSERT INTO Customer_Account VALUES ('C001', 5001);
INSERT INTO Customer_Account VALUES ('C002', 5001); 
INSERT INTO Customer_Account VALUES ('C003', 5002);
INSERT INTO Customer_Account VALUES ('C004', 5003);
INSERT INTO Customer_Account VALUES ('C005', 5004);
INSERT INTO Customer_Account VALUES ('C006', 5005);
INSERT INTO Customer_Account VALUES ('C007', 5006);
INSERT INTO Customer_Account VALUES ('C008', 5007);

INSERT INTO Customer_Loan VALUES ('C001', 7001);
INSERT INTO Customer_Loan VALUES ('C002', 7002);
INSERT INTO Customer_Loan VALUES ('C003', 7003);
INSERT INTO Customer_Loan VALUES ('C004', 7004);
INSERT INTO Customer_Loan VALUES ('C005', 7005);
INSERT INTO Customer_Loan VALUES ('C006', 7006);
INSERT INTO Customer_Loan VALUES ('C007', 7007);
INSERT INTO Customer_Loan VALUES ('C008', 7008);
``` 
### List the details of customers who have joint account and also have at least oneloan.
```
SELECT DISTINCT c.*
FROM Customer c
JOIN Customer_Account ca ON c.SSN = ca.SSN
JOIN (
 SELECT Account_No
 FROM Customer_Account
 GROUP BY Account_No
 HAVING COUNT(SSN) > 1
) joint ON ca.Account_No = joint.Account_No
JOIN Customer_Loan cl ON c.SSN = cl.SSN;
```
### List the details of the branch that has given the maximum loan.
```
SELECT b.*
FROM Branch b
JOIN Loan l ON b.Branch_ID = l.Branch_ID
GROUP BY b.Branch_ID, b.Name, b.Address, b.Phone, b.Bank_ID
ORDER BY COUNT(l.Loan_No) DESC
FETCH FIRST 1 ROW ONLY;
```
### List the details of savings accounts opened in the SBI branches located at Bangalore.
```
SELECT a.*
FROM Account a
JOIN Branch br ON a.Branch_ID = br.Branch_ID
JOIN Bank bk ON br.Bank_ID = bk.Bank_ID
WHERE a.Type = 'Savings' AND bk.Name = 'SBI' AND br.Address
LIKE '%Bangalore%';
```

### List the name of branch along with its bank name and total amount of loan given by it.
```
SELECT br.Name AS Branch_Name, bk.Name AS Bank_Name, COUNT
(l.Loan_No) AS Total_Loans
FROM Branch br
JOIN Bank bk ON br.Bank_ID = bk.Bank_ID
JOIN Loan l ON br.Branch_ID = l.Branch_ID
GROUP BY br.Name, bk.Name;
```
### Retrieve the names of customers who have accounts in all the branches located in a specific city.
```
SELECT c.Name
FROM Customer c
WHERE NOT EXISTS (
 SELECT br.Branch_ID
 FROM Branch br
 WHERE br.Address LIKE '%Bangalore%'
 MINUS
 SELECT a.Branch_ID
 FROM Customer_Account ca
 JOIN Account a ON ca.Account_No = a.Account_No
 WHERE ca.SSN = c.SSN
);
```