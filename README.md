<!DOCTYPE html>

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
    <title>Question with Attempts</title>
    <style>
        body { font-family: Arial, sans-serif; text-align: center; margin: 50px; }
        #feedback { font-weight: bold; margin-top: 10px; }
    </style>
</head>
<body>
    <h2>Answer the Question</h2>
    <p id="question">What has to be broken before you can use it?</p>
    <input type="text" id="answer" placeholder="Enter your answer">
    <button onclick="checkAnswer()">Submit</button>
    <p id="feedback"></p>

    <script>
        const correctAnswer = "egg"; // Define the correct answer
        let attemptsLeft = 3; // Maximum attempts

        function checkAnswer() {
            const userAnswer = document.getElementById("answer").value.trim().toLowerCase();
            const feedbackElement = document.getElementById("feedback");

            if (userAnswer === correctAnswer) {
                feedbackElement.textContent = "Correct! The answer is 'Egg'. 🎉";
                feedbackElement.style.color = "green";
            } else {
                attemptsLeft--;
                if (attemptsLeft > 0) {
                    feedbackElement.textContent = `Incorrect! Try again. Attempts left: ${attemptsLeft}`;
                    feedbackElement.style.color = "red";
                } else {
                    feedbackElement.textContent = `No attempts left! The correct answer was: '${correctAnswer}'.`;
                    feedbackElement.style.color = "blue";
                    document.getElementById("answer").disabled = true; // Disable input after attempts are used
                }
            }
        }
    </script>
</body>
</html>
