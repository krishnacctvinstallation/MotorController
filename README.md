<!DOCTYPE html>
<html>
<head>
    <meta charset="UTF-8">
    <title>Internet Motor Control</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            background: #f1f1f1;
            text-align: center;
            margin-top: 50px;
        }
        .box {
            background: white;
            max-width: 400px;
            margin: auto;
            padding: 30px;
            border-radius: 10px;
            box-shadow: 0 0 10px rgba(0,0,0,0.1);
        }
        input, button {
            padding: 10px;
            margin: 10px 0;
            width: 100%;
            border-radius: 5px;
            border: 1px solid #ccc;
        }
        button {
            background-color: #007bff;
            color: white;
            border: none;
        }
        button:hover {
            background-color: #0056b3;
        }
        #controlPanel, #changePassPanel {
            display: none;
        }
    </style>
</head>
<body>
    <div class="box" id="loginPanel">
        <h2>Login</h2>
        <input type="text" id="username" placeholder="Enter Username">
        <input type="password" id="password" placeholder="Enter Password">
        <button onclick="login()">Login</button>
    </div>

    <div class="box" id="controlPanel">
        <h2>Motor Control</h2>
        <button onclick="motorControl('ON')">Motor ON</button>
        <button onclick="motorControl('OFF')">Motor OFF</button>
    </div>

    <div class="box" id="changePassPanel">
        <h2>Change Username/Password</h2>
        <input type="text" id="newUsername" placeholder="New Username">
        <input type="password" id="newPassword" placeholder="New Password">
        <button onclick="changeCredentials()">Change</button>
    </div>

    <script>
        let storedUsername = "admin";
        let storedPassword = "1234";

        function login() {
            const user = document.getElementById("username").value;
            const pass = document.getElementById("password").value;
            if (user === storedUsername && pass === storedPassword) {
                document.getElementById("loginPanel").style.display = "none";
                document.getElementById("controlPanel").style.display = "block";
                document.getElementById("changePassPanel").style.display = "block";
            } else {
                alert("Incorrect username or password!");
            }
        }

        function motorControl(status) {
            alert("Motor turned " + status);
            // Here you can make a request to ESP IP using fetch()
        }

        function changeCredentials() {
            const newU = document.getElementById("newUsername").value;
            const newP = document.getElementById("newPassword").value;
            if (newU && newP) {
                storedUsername = newU;
                storedPassword = newP;
                alert("Username and Password updated. Please login again.");
                location.reload();
            } else {
                alert("Please fill both fields.");
            }
        }
    </script>
</body>
</html>
