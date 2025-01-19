# PRODIGY_WD_01
# HTML FILES

<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Interactive Navigation Menu</title>
    <link rel="stylesheet" href="styles.css">
</head>
<body>
    <nav class="navbar" id="navbar">
        <ul class="nav-list">
            <li class="nav-item"><a href="#home">Home</a></li>
            <li class="nav-item"><a href="#about">About</a></li>
            <li class="nav-item"><a href="#services">Services</a></li>
            <li class="nav-item"><a href="#contact">Contact</a></li>
        </ul>
    </nav>
    <div class="content">
      
    </div>
    <script src="script.js"></script>
</body>
</html>

#CSS FILES

body {
    font-family: Arial, sans-serif;
    margin: 0;
    padding: 0;
}

.navbar {
    position: fixed;
    top: 0;
    width: 100%;
    background-color: #333;
    color: white;
    text-align: center;
    transition: background-color 0.3s;
}

.nav-list {
    list-style: none;
    margin: 0;
    padding: 0;
    display: flex;
    justify-content: center;
}

.nav-item {
    margin: 0 15px;
}

.nav-item a {
    color: white;
    text-decoration: none;
    font-size: 18px;
    transition: color 0.3s;
}

.nav-item a:hover {
    color: #ff6347; /* Highlight color when hovered */
}

.content {
    padding: 100px 20px; /* Adjust as needed */
}

.scrolled {
    background-color: #222; /* Background color when scrolled */
}

# JAVASCRIPT FILES

window.addEventListener('scroll', function() {
    const navbar = document.getElementById('navbar');
    if (window.scrollY > 50) {
        navbar.classList.add('scrolled');
    } else {
        navbar.classList.remove('scrolled');
    }
});
