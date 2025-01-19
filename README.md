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



#PRODIGY_WD_02

#HTML FILES
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Stopwatch</title>
    <link rel="stylesheet" href="styles1.css">
</head>
<body>
    <div class="stopwatch">
        <div class="display" id="display">00:00:00</div>
        <div class="controls">
            <button id="startStopBtn" onclick="startStop()">Start</button>
            <button onclick="reset()">Reset</button>
            <button onclick="lap()">Lap</button>
        </div>
        <ul id="laps"></ul>
    </div>
    <script src="script1.js"></script>
</body>
</html>

#CSS FILES

body {
    font-family: Arial, sans-serif;
    display: flex;
    justify-content: center;
    align-items: center;
    height: 100vh;
    margin: 0;
    background-color: #f0f0f0;
}

.stopwatch {
    text-align: center;
}

.display {
    font-size: 48px;
    margin-bottom: 20px;
}

.controls button {
    font-size: 16px;
    padding: 10px 20px;
    margin: 5px;
    cursor: pointer;
}

#laps {
    list-style: none;
    padding: 0;
}

#laps li {
    font-size: 18px;
    margin: 5px 0;
}

#JAVASCRPIT FILES

let timer;
let isRunning = false;
let startTime;
let elapsedTime = 0;
let lapCounter = 1;

function startStop() {
    const startStopBtn = document.getElementById('startStopBtn');
    
    if (isRunning) {
        clearInterval(timer);
        isRunning = false;
        startStopBtn.textContent = 'Start';
    } else {
        startTime = Date.now() - elapsedTime;
        timer = setInterval(updateDisplay, 10);
        isRunning = true;
        startStopBtn.textContent = 'Pause';
    }
}

function reset() {
    clearInterval(timer);
    isRunning = false;
    elapsedTime = 0;
    document.getElementById('display').textContent = '00:00:00';
    document.getElementById('startStopBtn').textContent = 'Start';
    document.getElementById('laps').innerHTML = '';
    lapCounter = 1;
}

function lap() {
    if (isRunning) {
        const lapTime = document.getElementById('display').textContent;
        const lapItem = document.createElement('li');
        lapItem.textContent = `Lap ${lapCounter}: ${lapTime}`;
        document.getElementById('laps').appendChild(lapItem);
        lapCounter++;
    }
}

function updateDisplay() {
    elapsedTime = Date.now() - startTime;
    const milliseconds = Math.floor((elapsedTime % 1000) / 10).toString().padStart(2, '0');
    const seconds = Math.floor((elapsedTime / 1000) % 60).toString().padStart(2, '0');
    const minutes = Math.floor((elapsedTime / 60000) % 60).toString().padStart(2, '0');
    document.getElementById('display').textContent = `${minutes}:${seconds}:${milliseconds}`;
}
