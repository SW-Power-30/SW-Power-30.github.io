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

    <script>
        const questions = [
            { question: "Where the earth’s bounty meets eager hands, near a place where animals once took their stands. On Sundays, the flavours are rich, the produce is prime—find this spot, and you’ll feast in no time?", answer: "farmer markets", image: "https://example.com/egg.jpg"  },
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

        function loadQuestion() {
            if (currentQuestionIndex < questions.length) {
                questionElement.textContent = questions[currentQuestionIndex].question;
                feedbackElement.textContent = `Attempts left: ${attemptsLeft}`;
                answerInput.value = "";
                answerInput.disabled = false;
                answerImage.style.display = "none"; // Hide previous image
            } else {
                questionElement.textContent = "🎉 Congratulations! You have solved all the clues and collected all the goodies, now enjoy the picnic!";
                answerInput.style.display = "none";
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
                setTimeout(() => {
                    currentQuestionIndex++;
                    attemptsLeft = 3; // Reset attempts for next question
                    loadQuestion();
                }, 10000); // Delay before next question
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
                    setTimeout(() => {
                        currentQuestionIndex++;
                        attemptsLeft = 3; // Reset attempts
                        loadQuestion();
                    }, 3000); // Delay before moving to next question
                }
            }
        }

        loadQuestion(); // Initialize first question
    </script>
</body>
</html>
