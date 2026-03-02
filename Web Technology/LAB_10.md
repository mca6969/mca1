## LAB 10--Build web pages that can add dynamic data to the web pages using PHP and MySQL.

### Step 1: Create Database and Table (phpMyAdmin / MySQL)
```
CREATE DATABASE Lab10;
CREATE TABLE employees (
    id INT AUTO_INCREMENT PRIMARY KEY,  
    ename VARCHAR(50),                  
    eno VARCHAR(20),                    
    department VARCHAR(50)              
);
```

### Step 3: Database Connection File (db.php)
```
$servername = "localhost";   
$username = "root";          
$password = "";             
$database = "lab10";        

$conn = new mysqli($servername, $username, $password, $database);

if ($conn->connect_error) {
    die("Connection failed: " . $conn->connect_error);
}
?>
```

### Step 4: Insert Employee Data (insert.php)
```
<?php
include 'db.php';

if ($_POST) {

    $sql = "INSERT INTO employees (ename, eno, department)
            VALUES ('$_POST[ename]', '$_POST[eno]', '$_POST[department]')";

    $conn->query($sql);

    echo "Employee Inserted Successfully";
}
?>
<form method="post">

    Name:
    <input type="text" name="ename" required><br><br>

    Employee No:
    <input type="text" name="eno" required><br><br>

    Department:
    <input type="text" name="department" required><br><br>

    <input type="submit" value="Insert Employee">
</form>

<br>
<a href="display.php">View Employees</a>
```

### Step 5: Display Employee Data (display.php)
```
<?php
include 'db.php'; 

$result = $conn->query("SELECT * FROM employees");

echo '<table border="1">
<tr>
<th>ID</th>
<th>Name</th>
<th>Employee No</th>
<th>Department</th>
<th>Action</th>
</tr>';

while ($r = $result->fetch_assoc()) {

    echo "<tr>
    <td>".$r['id']."</td>              
    <td>".$r['ename']."</td>           
    <td>".$r['eno']."</td>             
    <td>".$r['department']."</td>     
    <td>
        <a class='delete-btn' href='delete.php?id=".$r['id']."'>Delete</a>
    </td>
    </tr>";
}

echo '</table>';
?>
<br>
<a href="insert.php">Add Employee</a>
```

### Step 6: Delete Employee (delete.php)
```
<?php
include 'db.php'; 

$conn->query("DELETE FROM employees WHERE id = $_GET['id']");

echo "Employee Deleted Successfully";
?>
<br>
<a href="display.php">Back to Employee List</a>

```