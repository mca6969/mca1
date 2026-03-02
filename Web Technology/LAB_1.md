## LAB 1--Apply different HTML5 Tags to create rich user interface design
### Index.html
```
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>KLE College of BCA & MCA</title>
    <link rel="stylesheet" href="style.css">
</head>
<body>

<header>
    <h1>KLE College of BCA & MCA</h1>
    <p>Belagavi, Karnataka</p>
</header>

<nav>
    <ul>
        <li><a href="index.html">Home</a></li>
        <li><a href="#">Courses</a></li>
        <li><a href="campus.html">Campus</a></li>
    </ul>
</nav>

<section>
    <h2>Courses Offered by the College</h2>

    <article>
        <h3>BCA Program</h3>
        <p>
            BCA provides strong foundations in programming, databases,
            web development, and software engineering
        </p>
    </article>

    <article>
        <h3>MCA Program</h3>
        <p>
            MCA focuses on advanced computing, AI, machine learning,
            and modern software technologies.
        </p>
    </article>

    <figure>
        <figcaption>KLE Campus – Belagavi</figcaption>
    </figure>
</section>

<footer>
    © 2025 KLE College of BCA & MCA
</footer>

</body>
</html>
```
### Campus.html
```
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>College Campus</title>
    <link rel="stylesheet" href="style.css">
</head>
<body>

<header>
    <h1>College Campus</h1>
</header>

<nav>
    <ul>
        <li><a href="index.html">Home</a></li>
        <li><a href="campus.html">Campus</a></li>
        <li><a href="index.html">Courses</a></li>
    </ul>
</nav>

<section>
    <h2>Campus Tour Video</h2>
    <figure>
        <video width="400" controls>
            <source src="C:\Users\bhush\Desktop\MCA1\lab1\audio.mp4" type="video/mp4">
        </video>
        <figcaption>College Campus Tour</figcaption>
    </figure>

    <h2>College Anthem</h2>
    <figure>
        <audio controls>
            <source src="sunflower-street-drumloop-85bpm-163900.mp3" type="audio/mpeg">
        </audio>
        <figcaption>Campus Ambience</figcaption>
    </figure>

    <h2>Campus Image</h2>
    <figure>
        <img src="C:\Users\bhush\Desktop\MCA1\lab1\image.webp" width="400" alt="Campus Image">
        <figcaption>Our Beautiful Campus</figcaption>
    </figure>
</section>

<footer>
    © 2025 KLE College
</footer>

</body>
</html>
```
### Style.css
```

* {
    margin: 0;
    padding: 0;
    font-family: Arial;
}


body {
    background: #f2f4f8;
    color: #333;
}


header, footer {
    background: #004080;
    color: white;
    text-align: center;
    padding: 15px;
}


nav {
    background: #0066cc;
    text-align: center;
}

nav li {
    display: inline-block;
}

nav a {
    color: white;
    text-decoration: none;
    padding: 10px 15px;
    display: inline-block;
    font-weight: bold;
}

nav a:hover {
    background: #004080;
}


section {
    width: 80%;
    margin: 30px auto;
    background: white;
    padding: 20px;
    border-radius: 8px;
}

h2 {
    text-align: center;
    color: #004080;
    margin-bottom: 15px;
}

article {
    margin-bottom: 15px;
}

figure {
    text-align: center;
    margin-top: 20px;
}

figcaption {
    font-style: italic;
    color: #666;
}
```