<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Cookie Clicker Game</title>
    <style>
        body {
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: center;
            height: 100vh;
            background-color: #f7f7f7;
            font-family: Arial, sans-serif;
        }
        #cookie {
            width: 200px;
            height: 200px;
            background-color: #d2b48c;
            border-radius: 50%;
            border: 5px solid #8b4513;
            display: flex;
            align-items: center;
            justify-content: center;
            cursor: pointer;
            font-size: 24px;
            color: #fff;
        }
        #score {
            margin-top: 20px;
            font-size: 24px;
        }
        #upgrade {
            margin-top: 20px;
            padding: 10px 20px;
            font-size: 16px;
            cursor: pointer;
        }
    </style>
</head>
<body>

    <div id="cookie">🍪</div>
    <div id="score">Cookies: 0</div>
    <button id="upgrade">Upgrade (Cost: 50 cookies)</button>

    <script>
        let cookies = 0;
        let cookiePerClick = 1;
        let upgradeCost = 50;

        const cookieElement = document.getElementById("cookie");
        const scoreElement = document.getElementById("score");
        const upgradeButton = document.getElementById("upgrade");

        cookieElement.addEventListener("click", () => {
            cookies += cookiePerClick;
            updateScore();
        });

        upgradeButton.addEventListener("click", () => {
            if (cookies >= upgradeCost) {
                cookies -= upgradeCost;
                cookiePerClick++;
                upgradeCost = Math.floor(upgradeCost * 1.5); // Increase cost for next upgrade
                upgradeButton.innerText = `Upgrade (Cost: ${upgradeCost} cookies)`;
                updateScore();
            } else {
                alert("Not enough cookies!");
            }
        });

        function updateScore() {
            scoreElement.innerText = `Cookies: ${cookies}`;
        }
    </script>

</body>
</html>
