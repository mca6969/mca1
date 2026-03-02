## LAB 9--Design and implement mathematical operations using Math library of Java Script
```
<!DOCTYPE html>
<html>
<head>
    <title>Math Functions in JavaScript</title>
</head>
<body>

    <h2>JavaScript Math Library</h2>

    <label>Enter a Number:</label><br><br>
    <input type="number" id="num"><br><br>

    <button onclick="mathOperations()">Calculate</button>

    <p id="result"></p>

    <script>
        function mathOperations() {
            var n = document.getElementById("num").value;

            document.getElementById("result").innerHTML =
                "Square Root: " + Math.sqrt(n) + "<br>" +
                "Power (n²): " + Math.pow(n, 2) + "<br>" +
                "Round: " + Math.round(n) + "<br>" +
                "Ceil: " + Math.ceil(n) + "<br>" +
                "Floor: " + Math.floor(n) + "<br>" +
                "Absolute: " + Math.abs(n);
        }
    </script>

</body>
</html>
```
