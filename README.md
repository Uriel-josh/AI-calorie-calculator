</head>
<body>
    <div class="calculator">
        <h1>AI Fitness Calculator</h1>
        <form id="calculatorForm">
            <label for="weight">Weight (kg):</label>
            <input type="number" id="weight" required>

            <label for="height">Height (cm):</label>
            <input type="number" id="height" required>

            <label for="age">Age:</label>
            <input type="number" id="age" required>

            <label for="gender">Gender:</label>
            <select id="gender" required>
                <option value="">Select</option>
                <option value="male">Male</option>
                <option value="female">Female</option>
            </select>

            <label for="activity">Activity Level:</label>
            <select id="activity" required>
                <option value="">Select</option>
                <option value="sedentary">Sedentary</option>
                <option value="light">Light Exercise</option>
                <option value="moderate">Moderate Exercise</option>
                <option value="active">Very Active</option>
            </select>

            <label for="goal">Goal:</label>
            <select id="goal" required>
                <option value="">Select</option>
                <option value="lose">Lose Weight</option>
                <option value="maintain">Maintain Weight</option>
                <option value="gain">Gain Weight</option>
            </select>

            <button type="submit">Calculate</button>
        </form>
        <div id="result"></div>
    </div>

    <script>
        document.getElementById('calculatorForm').addEventListener('submit', function(e) {
            e.preventDefault();
            
            const weight = parseFloat(document.getElementById('weight').value);
            const height = parseFloat
         

        
    
    

    
