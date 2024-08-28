<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Heart Rate Calculator</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            margin: 20px;
            padding: 10px;
        }
        .calculator {
            max-width: 400px;
            margin: 0 auto;
            padding: 20px;
            border: 1px solid #ddd;
            border-radius: 8px;
            box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
        }
        input, button {
            padding: 8px;
            width: calc(100% - 16px);
            margin: 8px 0;
            border: 1px solid #ccc;
            border-radius: 4px;
        }
        button {
            background-color: #4CAF50;
            color: white;
            cursor: pointer;
        }
        button:hover {
            background-color: #45a049;
        }
        .result {
            margin-top: 10px;
            font-weight: bold;
        }
    </style>
</head>
<body>

    <div class="calculator">
        <h2>Heart Rate Calculator</h2>
        <label for="age">Enter Your Age:</label>
        <input type="number" id="age" placeholder="Age" required>

        <label for="resting">Enter Your Resting Heart Rate:</label>
        <input type="number" id="resting" placeholder="Resting Heart Rate" required>

        <button onclick="calculateHeartRate()">Calculate</button>

        <div class="result" id="result"></div>
    </div>

    <script>
        function calculateHeartRate() {
            const age = document.getElementById('age').value;
            const resting = document.getElementById('resting').value;

            if (age && resting) {
                // Maximum Heart Rate Calculation
                const maxHeartRate = 220 - age;

                // Target Heart Rate Zones (Zone 2, typically 60-70% of max HR)
                const lowerEnd = Math.round((maxHeartRate - resting) * 0.6 + parseInt(resting));
                const upperEnd = Math.round((maxHeartRate - resting) * 0.7 + parseInt(resting));

                document.getElementById('result').innerHTML = `
                    Maximum Heart Rate: ${maxHeartRate} bpm<br>
                    Zone 2 Heart Rate: ${lowerEnd} - ${upperEnd} bpm
                `;
            } else {
                document.getElementById('result').innerHTML = "Please enter valid inputs.";
            }
        }
    </script>

</body>
</html>
