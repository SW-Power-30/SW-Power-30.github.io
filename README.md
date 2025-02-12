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
    <h2>Solve the clue to find the next stop</h2>
    <p id="question">Loading...</p>
    <input type="text" id="answer" placeholder="Enter your answer">
    <button onclick="checkAnswer()">Submit</button>
    <p id="feedback"></p>

    <script>
        const questions = [
            { question: "Where the earth’s bounty meets eager hands, near a place where animals once took their stands. On Sundays, the flavours are rich, the produce is prime—find this spot, and you’ll feast in no time?", answer: "farmer markets" },
            { question: "Near towering trees where wildlife roams, A hidden gem feels just like home. With a European touch and a scent so sweet,Find this spot for the perfect treat!", answer: "euro patisserie" },
            { question: "Nestled where the grapevines grow, A cottage waits with a golden glow. In Lovedale’s heart, both quaint and great, Find the wines—don’t be late!", answer: "emmas cottage" }
            { question: "Near bubbles that sparkle, yet not in a glass, A sweet little haven, too tempting to pass. Find this stop near famous white wine.", answer: "hunter valley chocolate company" }
            { question: "Where flavors are bold and aromas are grand, You'll find creamy delights in a well-known land. On a road that's 'not fixed' yet leads the right way", answer: "smelly cheese shop" }
            { question: "Not far from shops and cellar doors, A place for play and open floors. Pack your basket, take a seat, if you can find your spot?", answer: "hunter valley gardens" }
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
                questionElement.textContent = "🎉 Congratulations! You have solved all the clues and collected all the goodies, now enjoy the picnic!";
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
