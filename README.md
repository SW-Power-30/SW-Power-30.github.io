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
    <img id="answerImage" src="" alt="Correct Answer Image">
    <button id="nextButton" onclick="nextQuestion()">Next Question</button>

    <script>
        const questions = [
            { question: "Where the earth’s bounty meets eager hands, near a place where animals once took their stands. On Sundays, the flavours are rich, the produce is prime—find this spot, and you’ll feast in no time?", answer: "farmer markets", image: "data:image/jpeg;base64,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"  },
            { question: "Near towering trees where wildlife roams, A hidden gem feels just like home. With a European touch and a scent so sweet,Find this spot for the perfect treat!", answer: "euro patisserie", image: "https://example.com/egg.jpg"   },
            { question: "Nestled where the grapevines grow, A cottage waits with a golden glow. In Lovedale’s heart, both quaint and great, Find the wines—don’t be late!", answer: "emmas cottage", image: "https://example.com/egg.jpg"   },
            { question: "Near bubbles that sparkle, yet not in a glass, A sweet little haven, too tempting to pass. Find this stop near famous white wine.", answer: "hunter valley chocolate company", image: "https://example.com/egg.jpg"   },
            { question: "Where flavors are bold and aromas are grand, You'll find creamy delights in a well-known land. On a road that's 'not fixed' yet leads the right way", answer: "smelly cheese shop", image: "https://example.com/egg.jpg"   },
            { question: "Not far from shops and cellar doors, A place for play and open floors. Pack your basket, take a seat, if you can find your spot?", answer: "hunter valley gardens", image: "https://example.com/egg.jpg"   }
        ];

        let currentQuestionIndex = 0;
        let attemptsLeft = 3;
        const questionElement = document.getElementById("question");
        const feedbackElement = document.getElementById("feedback");
        const answerInput = document.getElementById("answer");
        const answerImage = document.getElementById("answerImage");
        const nextButton = document.getElementById("nextButton");

        function loadQuestion() {
            if (currentQuestionIndex < questions.length) {
                questionElement.textContent = questions[currentQuestionIndex].question;
                feedbackElement.textContent = `Attempts left: ${attemptsLeft}`;
                answerInput.value = "";
                answerInput.disabled = false;
                answerImage.style.display = "none";
                nextButton.style.display = "none";
            } else {
                questionElement.textContent = "🎉 Congratulations! You have solved all the clues and collected all the goodies, now enjoy the picnic!";
                answerInput.style.display = "none";
                nextButton.style.display = "none";
            }
        }

        function checkAnswer() {
            const userAnswer = answerInput.value.trim().toLowerCase();
            const correctAnswer = questions[currentQuestionIndex].answer;
            const correctImage = questions[currentQuestionIndex].image;

            if (userAnswer === correctAnswer) {
                feedbackElement.textContent = "✅ Correct! Moving to next question...";
                feedbackElement.style.color = "green";
                answerImage.src = correctImage; // Set image source
                answerImage.style.display = "block"; // Show image
                answerInput.disabled = true;
                nextButton.style.display = "block";
            } else {
                attemptsLeft--;
                if (attemptsLeft > 0) {
                    feedbackElement.textContent = `❌ Incorrect! Try again. Attempts left: ${attemptsLeft}`;
                    feedbackElement.style.color = "red";
                } else {
                    feedbackElement.textContent = `❌ No attempts left! The correct answer was: "${correctAnswer}".`;
                    feedbackElement.style.color = "blue";
                    answerImage.src = correctImage; // Show image even if wrong after 3 attempts
                    answerImage.style.display = "block";
                    answerInput.disabled = true;
                    nextButton.style.display = "block";
                }
            }
        }

        function nextQuestion() {
            currentQuestionIndex++;
            attemptsLeft = 3;
            loadQuestion();
        }

        loadQuestion(); // Initialize first question
    </script>
</body>
</html>
