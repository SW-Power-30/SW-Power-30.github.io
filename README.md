
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
    <p id="clue">"Where the earth’s bounty meets eager hands, near a place where animals once took their stands. On Sundays, the flavours are rich, the produce is prime—find this spot, and you’ll feast in no time!" .</p>
    <input type="text" id="answer" placeholder="Enter your answer">
    <button onclick="checkAnswer()">Submit</button>
    <p id="feedback"></p>
    <button id="nextButton" onclick="nextClue()" style="display:none;">Next Clue</button>

   <!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Answer Checker</title>
</head>
<body>
    <h2>Clue to Stop 1:</h2>
    <p>"Where the earth’s bounty meets eager hands, near a place where animals once took their stands. On Sundays, the flavours are rich, the produce is prime—find this spot, and you’ll feast in no time!"</p>
    <input type="text" id="userAnswer" placeholder="Enter your answer">
    <button onclick="checkAnswer()">Submit</button>
    <p id="result"></p>

    <script>
        const correctAnswer = "Newcastle Farmer Markets"; // Predefined correct answer

        function checkAnswer() {
            const userInput = document.getElementById("userAnswer").value.trim().toLowerCase();
            const resultElement = document.getElementById("result");

            if (userInput === correctAnswer) {
                resultElement.textContent = "Correct! The answer is 'Newcastle Farmer Markets'. 🎉";
                resultElement.style.color = "green";
            } else {
                resultElement.textContent = "Incorrect! Try again. ❌";
                resultElement.style.color = "red";
            }
        }
    </script>
</body>
</html>

