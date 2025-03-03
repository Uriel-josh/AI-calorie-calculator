# AI-calorie-calculator
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Nigerian AI Fitness Calculator</title>
    <style>
        body {
            font-family: New Times Roman, sans-serif;
            background-color: #1a1a1a;
            color: #ffffff;
            display: flex;
            justify-content: center;
            align-items: center;
            min-height: 100vh;
            margin: 0;
            padding: 20px;
        }
        .calculator {
            background-color: #2c2c2c;
            border-radius: 10px;
            padding: 20px;
            box-shadow: 0 0 10px rgba(255, 255, 255, 0.1);
            width: 100%;
            max-width: 400px;
        }
        h1 {
            text-align: center;
            color: #4CAF50;
        }
        label {
            display: block;
            margin-top: 10px;
        }
        input, select {
            width: 100%;
            padding: 8px;
            margin-top: 5px;
            background-color: #3a3a3a;
            border: 1px solid #4a4a4a;
            color: #ffffff;
            border-radius: 4px;
        }
        button {
            width: 100%;
            padding: 10px;
            margin-top: 20px;
            background-color: #4CAF50;
            color: white;
            border: none;
            border-radius: 4px;
            cursor: pointer;
            font-size: 16px;
        }
        button:hover {
            background-color: #45a049;
        }
        #result {
            margin-top: 20px;
            text-align: left;
            font-size: 16px;
        }
    </style>
</head>
<body>
    <div class="calculator">
        <h1>Nigerian AI Fitness Calculator</h1>
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
            const height = parseFloatfrom flask import Flask, render_template, request, jsonify

app = Flask(_name_)

@app.route("/", methods=["GET"])
def index():
    return render_template("index.html")  # Render the HTML file

@app.route("/calculate", methods=["POST"])
def calculate():
    try:
        weight = float(request.form["weight"])
        height = float(request.form["height"])
        age = int(request.form["age"])
        gender = request.form["gender"]
        activity = request.form["activity"]
        goal = request.form["goal"]

        # Basic BMI calculation (you can expand this)
        height_meters = height / 100
        bmi = weight / (height_meters * height_meters)


        # Placeholder for more complex calculations (BMR, calorie needs, etc.)
        # You'll need to implement these based on standard formulas.
        bmr = calculate_bmr(weight, height, age, gender)
        calories = calculate_calories(bmr, activity, goal)


        result = {
            "bmi": round(bmi, 2),
            "bmr": round(bmr, 2),
            "calories": round(calories, 2)
        }
        return jsonify(result)

    except ValueError:
        return jsonify({"error": "Invalid input. Please enter numbers only."}), 400
    except Exception as e: # Catch any other error
      return jsonify({"error": str(e) }), 500

def calculate_bmr(weight, height, age, person_type):
    """Placeholder BMR calculation.  Replace with an appropriate formula."""

    if person_type == "male":
      bmr = 88.362 + (13.397 * weight) + (4.799 * height) - (5.677 * age)

    elif person_type == "female":
      bmr = 447.593 + (9.247 * weight) + (3.098 * height) - (4.330 * age)
    
    return bmr

def calculate_calories(bmr, activity, goal):
    """Placeholder calorie calculation. Replace with a proper formula."""

    activity_multipliers = {
        "sedentary": 1.2,
        "light": 1.375,
        "moderate": 1.55,
        "active": 1.725
    }

    goal_adjustments = {
      "lose": -500,
      "maintain": 0,
      "gain": 500
    }

    calories = bmr * activity_multipliers.get(activity, 1.2) # Default to sedentary if invalid activity level

    calories += goal_adjustments.get(goal,0) # Apply goal adjustment

    return calories

if _name_ == "_main_":
    app.run(debug=True)  # Set debug=False for production
