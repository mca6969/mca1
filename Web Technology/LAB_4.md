## LAB 4--Inline , Internal and External CSS 
### Index.html
```
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Lab 4</title>

    <!-- Internal CSS -->
    <style>
        .internal-box {
            padding: 20px;
            border: 3px solid blue;
            text-align: center;
            background-color: #e6f0ff;
        }
    </style>

    <!-- External CSS -->
    <link rel="stylesheet" href="style.css">
</head>

<body>

<header>
    <h2>CSS3 Demonstrations</h2>
</header>

<nav>
    <a href="#css-types">CSS Types</a>
</nav>

<section id="css-types">
    <h3 style="text-align:center; color:blue;">CSS Methods</h3>

    <div class="row">

        <!-- Inline CSS -->
        <div class="col">
            <div style="padding:20px; border:3px solid red; text-align:center; background:#ffe6e6;">
                Inline CSS
                <p>CSS written directly in the element using style attribute.</p>
            </div>
        </div>

        <!-- Internal CSS -->
        <div class="col">
            <div class="internal-box">
                Internal CSS
                <p>CSS placed inside style tag in HTML head.</p>
            </div>
        </div>

        <!-- External CSS -->
        <div class="col">
            <div class="external-box">
                External CSS
                <p>CSS written in a separate file and linked with &lt;code&gt;.</p>
            </div>
        </div>

    </div>
</section>

<!-- Box Model Section -->
<section id="box-model">
    <h3 style="text-align:center; color:blue; margin-top:50px;">CSS Box Model</h3>

    <div class="box-model">
        <h4>Box Model Example</h4>
        <p><b>Content:</b> Actual text or data inside the element.</p>
        <p><b>Padding:</b> Space between content and border.</p>
        <p><b>Border:</b> Surrounds the padding and content.</p>
        <p><b>Margin:</b> Space outside the border.</p>
    </div>
</section>

<footer>
    © 2025 MCA Lab
</footer>

</body>
</html>
```
### Style.css
```
/* Body */
body {
    font-family: Arial, sans-serif;
    background-color: #f5f5f5;
    margin: 0;
}

/* Header */
header {
    background-color: #0d6efd;
    color: white;
    text-align: center;
    padding: 20px;
}

/* Navigation */
nav {
    background-color: #333;
    text-align: center;
    padding: 10px;
}

nav a {
    color: white;
    text-decoration: none;
    font-weight: bold;
}

/* Container */
.container {
    width: 90%;
    margin: auto;
}

/* Row and Columns using float */
.row {
    width: 100%;
}

.col {
    width: 30%;
    float: left;
    margin: 1.5%;
}

.row::after {
    content: "";
    display: block;
    clear: both;
}

/* Boxes */
.external-box {
    padding: 20px;
    border: 3px solid green;
    background-color: #eaffea;
    text-align: center;
}

.box-model {
    width: 400px;
    margin: 50px auto;
    padding: 30px;
    border: 4px solid black;
    background-color: #fff3cd;
    text-align: center;
    font-size: 16px;
}

/* Footer */
footer {
    background-color: #0d6efd;
    color: white;
    text-align: center;
    padding: 15px;
    margin-top: 30px;
}
```
