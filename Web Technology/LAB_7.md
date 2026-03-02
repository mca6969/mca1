## LAB 7--PHP Operators and CURD operations
### 7 A--PHP Operators
```
<!DOCTYPE html>
<html>
<head>
    <title>LAB 7 - PHP Operators</title>
</head>
<body>

<h2>LAB 7 : PHP Operators</h2>

<?php

$a = 10;
$b = 5;

echo "<h3>Arithmetic Operators</h3>";
echo "Addition: " . ($a + $b) . "<br>";
echo "Subtraction: " . ($a - $b) . "<br>";
echo "Multiplication: " . ($a * $b) . "<br>";
echo "Division: " . ($a / $b) . "<br>";


echo "<h3>Comparison Operators</h3>";
echo "a > b : " . (($a > $b) ? "True" : "False") . "<br>";
echo "a < b : " . (($a < $b) ? "True" : "False") . "<br>";
echo "a == b : " . (($a == $b) ? "True" : "False") . "<br>";

echo "<h3>Logical Operators</h3>";
echo "AND (a>5 && b<10) : " . (($a > 5 && $b < 10) ? "True" : "False") . "<br>";
echo "OR (a<5 || b<10) : " . (($a < 5 || $b < 10) ? "True" : "False") . "<br>";

$c = 20;

echo "<h3>Assignment Operators</h3>";
$c += 5;
echo "c += 5 : " . $c . "<br>";

$c -= 10;
echo "c -= 10 : " . $c . "<br>";

echo "<h3>Operator Precedence</h3>";
$result = 10 + 5 * 2;
echo "10 + 5 * 2 = " . $result;

?>

</body>
</html>
```
### 7 B--CURD Operations
```
part b : DB crteation in mysql
Step1:Create db
CREATE DATABASE studentdb;

Step2:Use db
USE studentdb;

Step3: Create table 
CREATE TABLE Students(
RollNo INT PRIMARY KEY,
Name VARCHAR(50),
Course VARCHAR(50),
City VARCHAR(50)
);

Step4:Insert records 
INSERT INTO Students VALUES
(1,'Ravi','MCA','Belagavi'),
(2,'Sneha','BCA','Hubli'),
(3,'Kiran','BCA','Dharwad');

Step5:View op
SELECT * FROM Students;

Step6:Update op
UPDATE Students SET City='Bengaluru' WHERE RollNo=3;

Step7:Delete op
DELETE FROM Students 
WHERE RollNo=2;

Step8: Final view 
SELECT * FROM Students;
```
