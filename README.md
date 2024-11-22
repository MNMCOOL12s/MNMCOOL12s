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
    </style>
</head>
<body>

    <h1>Welcome to the Quiz Game!</h1>
    <button id="start-btn">Start Game</button>

    <div id="quiz-container">
        <h2 id="question"></h2>
        <div id="options"></div>
        <button id="next-btn">Next Question</button>
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
            }
        ];

        let currentQuestionIndex = 0;
        let score = 0;

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
        }

        function selectOption(index) {
            const currentQuestion = questions[currentQuestionIndex];
            if (index === currentQuestion.answer) {
                score++;
            }
            if (currentQuestionIndex < questions.length - 1) {
                currentQuestionIndex++;
                showQuestion();
            } else {
                showResult();
            }
        }

        function showResult() {
            document.getElementById('quiz-container').style.display = 'none';
            document.getElementById('result').innerText = `Your score: ${score} out of ${questions.length}`;
            document.getElementById('result').style.display = 'block';
        }
    </script>

</body>
</html>
