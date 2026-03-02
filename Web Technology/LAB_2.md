## LAB 2--Work with HTML tags and create web pages for application 
### Index.html
```
<!DOCTYPE html>
<html>
<head>
    <title>India - Static Web Application</title>
    <link rel="stylesheet" href="style.css">
</head>

<body>

    <h1>India - Static Web Application</h1>

    <!-- Navigation Bar -->
    <nav>
        <a href="#">Home</a>
        <a href="#">About India</a>
        <a href="#">Geography</a>
        <a href="#">Map</a>
        <a href="#">Contact</a>
    </nav>

    <hr>

    <h2>About India</h2>
    <p>
        India is a country in South Asia known for its rich culture, history,
        and geographical diversity. It is the seventh-largest country by area
        and the most populous democracy in the world.
    </p>

    <p>
        India is known for <span>Unity in Diversity</span>,
        <br>Ancient civilization,
        <br>and strong democratic values.
        <br>
        Visit the 
        <a href="https://www.india.gov.in">Official Government Portal</a>.
    </p>

    <hr>

    <h2>Geo Location Information</h2>
    <ul>
        <li>Latitude: 20.5937° N</li>
        <li>Longitude: 78.9629° E</li>
        <li>Region: South Asia</li>
    </ul>

    <hr>

    <h2>Literacy Rate</h2>
    <label>Literacy Rate (77%)</label><br>
    <meter value="77" min="0" max="100">77%</meter>

    <hr>

    <h2>Major States</h2>
    <ol>
        <li>Karnataka</li>
        <li>Maharashtra</li>
        <li>Goa</li>
        <li>Uttar Pradesh</li>
        <li>Kerala</li>
    </ol>

    <hr>

    <h2>Development Indicators of India</h2>
    <p>
        India has shown significant growth in education, technology,
        infrastructure, and digital services in recent years.
    </p>

    <hr>

    <h2>India Map</h2>
    <p>Below is the Google Map showing India:</p>

    <iframe
        src="https://www.google.com/maps/embed?"
        width="400"
        height="450"
        style="border:0;"
        allowfullscreen
        loading="lazy">
    </iframe>

    <hr>

    <p>© Web Technology Lab - India Page</p>

</body>
</html>
```
### Style.css
```
/* Page styling */
body {
    font-family: Arial, sans-serif;
    margin: 20px;
    background-color: #f4f6f7;
}

/* Navigation bar */
nav {
    background-color: #154360;
    padding: 12px;
    text-align: center;
}

nav a {
    color: white;
    margin: 0 15px;
    text-decoration: none;
    font-weight: bold;
}

nav a:hover {
    color: #f1c40f;
    text-decoration: underline;
}

/* Main heading */
h1 {
    text-align: center;
    color: #2c3e50;
}

/* Section headings */
h2 {
    color: #1a5276;
}

/* Paragraph text */
p {
    font-size: 14px;
    line-height: 1.6;
}

/* Highlighted text */
span {
    color: #c0392b;
    font-weight: bold;
}

/* Google Map iframe */
iframe {
    border: 2px solid #7b8c8d;
    margin-top: 10px;
}

/* Footer */
p:last-of-type {
    text-align: center;
    margin-top: 20px;
}
```
