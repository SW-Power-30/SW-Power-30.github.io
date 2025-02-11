
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
    <h1>Clue Solver</h1>
    <p id="Clue to Stop 1">Loading clue...</p>
    <input type="text" id="answer" placeholder="Enter your answer">
    <button onclick="checkAnswer()">Submit</button>
    <p id="feedback"></p>
    <button id="nextButton" onclick="nextClue()" style="display:none;">Next Clue</button>

    <script>
        const clues = [
            { question: "Where the earth’s bounty meets eager hands, near a place where animals once took their stands. On Sundays, the flavours are rich, the produce is prime—find this spot, and you’ll feast in no time!", answer: "keyboard", formal: "A Keyboard" },
            { question: "The more you take, the more you leave behind. What am I?", answer: "footsteps", formal: "Footsteps" },
            { question: "What has to be broken before you can use it?", answer: "egg", formal: "An Egg" }
        ];
        
        let currentClueIndex = 0;
        let attemptsLeft = 3;
        const clueElement = document.getElementById("clue");
        const feedbackElement = document.getElementById("feedback");
        const answerInput = document.getElementById("answer");
        const nextButton = document.getElementById("nextButton");

        function loadClue() {
            clueElement.textContent = clues[currentClueIndex].question;
            feedbackElement.textContent = "Attempts left: " + attemptsLeft;
            answerInput.value = "";
            nextButton.style.display = "none";
        }

        function checkAnswer() {
            const userAnswer = answerInput.value.trim().toLowerCase();
            if (userAnswer === clues[currentClueIndex].answer) {
                feedbackElement.textContent = "Correct! " + clues[currentClueIndex].formal;
                feedbackElement.style.color = "green";
                nextButton.style.display = "inline";
            } else {
                attemptsLeft--;
                if (attemptsLeft > 0) {
                    feedbackElement.textContent = "Try again! Attempts left: " + attemptsLeft;
                    feedbackElement.style.color = "red";
                } else {
                    feedbackElement.textContent = "No attempts left! The correct answer was: " + clues[currentClueIndex].formal;
                    feedbackElement.style.color = "red";
                    nextButton.style.display = "inline";
                }
            }
        }

        function nextClue() {
            if (currentClueIndex < clues.length - 1) {
                currentClueIndex++;
                attemptsLeft = 3;
                loadClue();
            } else {
                clueElement.textContent = "Congratulations! You've solved all the clues!";
                answerInput.style.display = "none";
                nextButton.style.display = "none";
            }
        }

        loadClue();
    </script>
</body>
</html>
