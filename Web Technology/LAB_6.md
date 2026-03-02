## LAB 6--Analyze the components of Bootstrap
### Index.html
```
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>KLE College</title>

    <!-- Bootstrap CSS -->
    <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.2/dist/css/bootstrap.min.css" rel="stylesheet">
</head>
<body>

<!-- Navbar -->
<nav class="navbar navbar-expand-lg navbar-dark bg-primary">
    <div class="container">
        <a class="navbar-brand" href="#">KLE College</a>
        <div>
            <ul class="navbar-nav ms-auto">
                <li class="nav-item"><a class="nav-link" href="#">Home</a></li>
                <li class="nav-item"><a class="nav-link" href="#">Course</a></li>
                <li class="nav-item"><a class="nav-link" href="#">Placement</a></li>
                <li class="nav-item"><a class="nav-link" href="contact.html">Contact Us</a></li>
            </ul>
        </div>
    </div>
</nav>

<!-- Container -->
<div class="container mt-4">

    <!-- Alert -->
    <div class="alert alert-success text-center">
        Admissions Open for 2025 Batch!
    </div>

    <!-- Section Title -->
    <h2 class="text-center bg-light p-2">Courses We Offer</h2>

    <!-- Cards Section -->
    <div class="row mt-4">
        <div class="col-md-4">
            <div class="card">
                <img src="https://via.placeholder.com/300x150" class="card-img-top">
                <div class="card-body text-center">
                    <h5 class="card-title">MCA</h5>
                    <p>Master of Computer Applications with AI & ML focus.</p>
                </div>
            </div>
        </div>

        <div class="col-md-4">
            <div class="card">
                <img src="https://via.placeholder.com/300x150" class="card-img-top">
                <div class="card-body text-center">
                    <h5 class="card-title">BCA</h5>
                    <p>Bachelor of Computer Applications with strong programming base.</p>
                </div>
            </div>
        </div>

        <div class="col-md-4">
            <div class="card">
                <img src="https://via.placeholder.com/300x150" class="card-img-top">
                <div class="card-body text-center">
                    <h5 class="card-title">Integrated BCA-MCA</h5>
                    <p>5-year integrated program with advanced computing skills.</p>
                </div>
            </div>
        </div>
    </div>

    <!-- Placement Section -->
    <h2 class="text-center bg-light p-2 mt-5">Recent Placements in 2025</h2>
    <p class="text-center">19 students placed in Infosys</p>

    <!-- Progress Bar -->
    <div class="progress mb-5">
        <div class="progress-bar bg-success" style="width:78%">78% Placement</div>
    </div>

</div>

<!-- Footer -->
<footer class="bg-primary text-white text-center p-3">
    © 2025 KLE College | All Rights Reserved
</footer>

</body>
</html>
```
### Contact.html
```
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Contact Form</title>

    <!-- Bootstrap CSS -->
    <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.2/dist/css/bootstrap.min.css" rel="stylesheet">
</head>
<body>

<!-- Navbar Title -->
<nav class="navbar navbar-dark bg-primary">
    <div class="container">
        <span class="navbar-brand mx-auto">Contact Form</span>
    </div>
</nav>

<!-- Container -->
<div class="container mt-4">
    <form>
        <div class="mb-3">
            <label class="form-label">Email address</label>
            <input type="email" class="form-control" placeholder="Enter email">
        </div>

        <div class="mb-3">
            <label class="form-label">Feedback</label>
            <textarea class="form-control" rows="4" placeholder="Enter feedback"></textarea>
        </div>

        <button type="submit" class="btn btn-primary">Submit</button>
    </form>

    <!-- Pagination -->
    <nav class="mt-4">
        <ul class="pagination justify-content-center">
            <li class="page-item"><a class="page-link" href="index.html">Previous</a></li>
            <li class="page-item active"><a class="page-link" href="#">1</a></li>
            <li class="page-item"><a class="page-link" href="index.html">Next</a></li>
        </ul>
    </nav>
</div>

</body>
</html>
```