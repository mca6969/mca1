## LAB 5--Analyze the data types and operators of javascript
### Index.html
```
<!DOCTYPE html>
<html>
<head>
    <title>Lab 5 - JavaScript Data Types and Operators</title>
</head>

<body>

    <h2>LAB 5: JavaScript Data Types and Operators</h2>

    <button onclick="showData()">Show Output in Console</button>

    <script>
        function showData() {

            
            let name = "India";          
            let population = 140;        
            let isDeveloping = true;     
            let states = ["KA", "MH"];  
            let country = { capital: "Delhi" }; 

            let a = 10;  
            let b = 5;   

            let add = a + b;  
            let sub = a - b; 
            let mul = a * b;  
            let div = a / b;  
            
            let result =
                "String: " + name + "\n" +
                "Number: " + population + "\n" +
                "Boolean: " + isDeveloping + "\n" +
                "Array: " + states + "\n" +
                "Object Capital: " + country.capital + "\n\n" +

                "Operators Output:\n" +
                "Addition: " + add + "\n" +
                "Subtraction: " + sub + "\n" +
                "Multiplication: " + mul + "\n" +
                "Division: " + div;

            console.log(result);
        }
    </script>

</body>
</html>
```