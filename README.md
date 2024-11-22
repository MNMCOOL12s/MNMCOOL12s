<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Quiz Game</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            background-color: #f4f4f4;
            text-align: center;
            padding: 50px;
        }
        #quiz-container {
            display: none;
            background: white;
            border-radius: 8px;
            padding: 20px;
            box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
            width: 300px;
            margin: auto;
        }
        #result {
            margin-top: 20px;
        }
        button {
            padding: 10px 20px;
            margin: 5px;
            border: none;
            border-radius: 5px;
            background-color: #007BFF;
            color: white;
            cursor: pointer;
        }
        button:hover {
            background-color: #0056b3;
        }
        #timer {
            font-size: 20px;
            color: red;
        }
    </style>
</head>
<body>

    <h1>Welcome to the Quiz Game!</h1>
    <button id="start-btn">Start Game</button>

    <div id="quiz-container">
        <h2 id="question"></h2>
        <div id="options"></div>
        <div id="timer">Time Left: <span id="time-left">10</span> seconds</div>
        <button id="next-btn" style="display: none;">Next Question</button>
        <div id="result"></div>
    </div>

    <script>
        const questions = [
            {
                question: "What is the capital of France?",
                options: ["Berlin", "Madrid", "Paris", "Lisbon"],
                answer: 2
            },
            {
                question: "What is 2 + 2?",
                options: ["3", "4", "5", "6"],
                answer: 1
            },
            {
                question: "What is the color of the sky?",
                options: ["Blue", "Green", "Red", "Yellow"],
                answer: 0
            },
            {
                question: "Which planet is known as the Red Planet?",
                options: ["Earth", "Mars", "Jupiter", "Saturn"],
                answer: 1
            },
            {
                question: "What is the largest ocean on Earth?",
                options: ["Atlantic Ocean", "Indian Ocean", "Arctic Ocean", "Pacific Ocean"],
                answer: 3
            }
        ];

        let currentQuestionIndex = 0;
        let score = 0;
        let timer;
        const timeLimit = 10;

        document.getElementById('start-btn').addEventListener('click', startGame);
        document.getElementById('next-btn').addEventListener('click', nextQuestion);

        function startGame() {
            document.getElementById('start-btn').style.display = 'none';
            document.getElementById('quiz-container').style.display = 'block';
            currentQuestionIndex = 0;
            score = 0;
            showQuestion();
        }

        function showQuestion() {
            resetTimer();
            const currentQuestion = questions[currentQuestionIndex];
            document.getElementById('question').innerText = currentQuestion.question;

            const optionsContainer = document.getElementById('options');
            optionsContainer.innerHTML = '';
            currentQuestion.options.forEach((option, index) => {
                const button = document.createElement('button');
                button.innerText = option;
                button.addEventListener('click', () => selectOption(index));
                optionsContainer.appendChild(button);
            });
            document.getElementById('next-btn').style.display = 'none';
            startTimer();
        }

        function selectOption(index) {
            const currentQuestion = questions[currentQuestionIndex];
            if (index === currentQuestion.answer) {
                score++;
            }
            clearInterval(timer);
            if (currentQuestionIndex < questions.length - 1) {
                document.getElementById('next-btn').style.display = 'block';
            } else {
                showResult();
            }
        }

        function startTimer() {
            let timeLeft = timeLimit;
            document.getElementById('time-left').innerText
