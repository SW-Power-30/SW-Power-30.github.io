<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Clue Solver</title>
    <style>
        body { font-family: Arial, sans-serif; text-align: center; margin: 50px; }
        #feedback { font-weight: bold; margin-top: 10px; }
    </style>
</head>
<body>
    <h1>Mystery Picnic</h1>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Question with Attempts</title>
    <style>
        body { font-family: Arial, sans-serif; text-align: center; margin: 50px; }
        #feedback { font-weight: bold; margin-top: 10px; }
    </style>

<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Multi-Step Questions</title>
    <style>
        body { font-family: Arial, sans-serif; text-align: center; margin: 50px; }
        #feedback { font-weight: bold; margin-top: 10px; }
    </style>
</head>
<body>
    <h2>Answer the Question</h2>
    <p id="question">Loading...</p>
    <input type="text" id="answer" placeholder="Enter your answer">
    <button onclick="checkAnswer()">Submit</button>
    <p id="feedback"></p>

    <script>
        const questions = [
            { question: "What has to be broken before you can use it?", answer: "egg" },
            { question: "The more you take, the more you leave behind. What am I?", answer: "footsteps" },
            { question: "I have keys but open no locks. What am I?", answer: "keyboard" }
        ];

        let currentQuestionIndex = 0;
        let attemptsLeft = 3;
        const questionElement = document.getElementById("question");
        const feedbackElement = document.getElementById("feedback");
        const answerInput = document.getElementById("answer");

        function loadQuestion() {
            if (currentQuestionIndex < questions.length) {
                questionElement.textContent = questions[currentQuestionIndex].question;
                feedbackElement.textContent = `Attempts left: ${attemptsLeft}`;
                answerInput.value = "";
                answerInput.disabled = false;
            } else {
                questionElement.textContent = "🎉 Congratulations! You answered all questions!";
                answerInput.style.display = "none";
            }
        }

        function checkAnswer() {
            const userAnswer = answerInput.value.trim().toLowerCase();
            const correctAnswer = questions[currentQuestionIndex].answer;

            if (userAnswer === correctAnswer) {
                feedbackElement.textContent = "✅ Correct! Moving to next question...";
                feedbackElement.style.color = "green";
                setTimeout(() => {
                    currentQuestionIndex++;
                    attemptsLeft = 3; // Reset attempts for next question
                    loadQuestion();
                }, 1000); // Delay before next question
            } else {
                attemptsLeft--;
                if (attemptsLeft > 0) {
                    feedbackElement.textContent = `❌ Incorrect! Try again. Attempts left: ${attemptsLeft}`;
                    feedbackElement.style.color = "red";
                } else {
                    feedbackElement.textContent = `❌ No attempts left! The correct answer was: "${correctAnswer}".`;
                    feedbackElement.style.color = "blue";
                    setTimeout(() => {
                        currentQuestionIndex++;
                        attemptsLeft = 3; // Reset attempts
                        loadQuestion();
                    }, 2000); // Delay before moving to next question
                }
            }
        }

        loadQuestion(); // Initialize first question
    </script>
</body>
</html>
