<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Simple Cookie Clicker</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            text-align: center;
            margin-top: 50px;
        }
        .cookie-container {
            margin: 20px;
        }
        .cookie-button {
            padding: 20px 40px;
            font-size: 24px;
            cursor: pointer;
            background-color: #ffcc00;
            border: none;
            border-radius: 8px;
            box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
        }
        .cookie-button:hover {
            background-color: #ffb300;
        }
        .cookie-count {
            font-size: 32px;
            font-weight: bold;
            margin-top: 20px;
        }
    </style>
</head>
<body>

    <h1>Cookie Clicker Game</h1>
    
    <div class="cookie-container">
        <button class="cookie-button" onclick="collectCookie()">Click me to collect a cookie!</button>
        <div class="cookie-count">
            Cookies: <span id="cookieCount">0</span>
        </div>
    </div>

    <script>
        let cookieCount = 0;

        // Function to update the cookie count
        function collectCookie() {
            cookieCount++;
            document.getElementById("cookieCount").textContent = cookieCount;
        }
    </script>

</body>
</html>
