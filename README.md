# file-C-Users-SAMSUNG-Documents-index.html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>SmartStudy AI</title>

  <!-- Google Fonts -->
  <link href="https://fonts.googleapis.com/css2?family=Roboto:wght@300;400;500;700&display=swap" rel="stylesheet">

  <!-- Material Icons -->
  <link href="https://fonts.googleapis.com/icon?family=Material+Icons" rel="stylesheet">

  <style>
    body {
      font-family: "Roboto", sans-serif;
      background: #f1f3f4;
      margin: 0;
      padding: 0;
    }

    header {
      background: #1a73e8;
      color: white;
      padding: 20px;
      font-size: 26px;
      font-weight: 500;
      display: flex;
      align-items: center;
      justify-content: center;
      gap: 10px;
      box-shadow: 0 2px 6px rgba(0,0,0,0.1);
    }

    .container {
      max-width: 800px;
      margin: 40px auto;
      background: white;
      padding: 25px;
      border-radius: 12px;
      box-shadow: 0px 4px 12px rgba(0,0,0,0.1);
      animation: fadeIn 1s ease-in-out;
    }

    h2 {
      color: #202124;
      font-weight: 500;
      margin-bottom: 20px;
    }

    label {
      font-size: 15px;
      font-weight: 500;
      color: #5f6368;
    }

    textarea, input, select {
      width: 100%;
      padding: 12px;
      margin-top: 6px;
      margin-bottom: 20px;
      border: 1px solid #dadce0;
      border-radius: 8px;
      font-size: 16px;
      outline-color: #1a73e8;
      background: #fcfcfc;
    }

    button {
      width: 100%;
      padding: 14px;
      background: #1a73e8;
      color: white;
      border: none;
      border-radius: 8px;
      font-size: 17px;
      font-weight: 500;
      cursor: pointer;
      transition: 0.3s;
    }

    button:hover {
      background: #0c5ed9;
    }

    .output-box {
      margin-top: 30px;
      padding: 20px;
      border-left: 4px solid #1a73e8;
      background: #e8f0fe;
      border-radius: 8px;
      white-space: pre-line;
      font-size: 17px;
    }

    @keyframes fadeIn {
      from { opacity: 0; transform: translateY(15px); }
      to { opacity: 1; transform: translateY(0); }
    }

    /* Mobile Responsive */
    @media (max-width: 600px) {
      header {
        font-size: 22px;
      }

      .container {
        margin: 20px;
        padding: 18px;
      }

      h2 {
        font-size: 22px;
      }
    }
  </style>
</head>

<body>

<header>
  <span class="material-icons">auto_stories</span>
  SmartStudy AI
</header>

<div class="container">
  <h2>Create Your Personalized Study Plan</h2>

  <label for="subjects">Enter Your Subjects:</label>
  <textarea id="subjects" placeholder="Example: Math, Physics, English"></textarea>

  <label for="hours">Hours Available Per Day:</label>
  <input type="number" id="hours" placeholder="Example: 4">

  <label for="difficulty">Study Difficulty Level:</label>
  <select id="difficulty">
    <option value="easy">Easy</option>
    <option value="medium">Medium</option>
    <option value="hard">Hard</option>
  </select>

  <button onclick="generatePlan()">Generate Study Plan</button>

  <div class="output-box" id="output">Your plan will appear here...</div>
</div>

<script>
function generatePlan() {
  const subjects = document.getElementById("subjects").value.split(",").map(s => s.trim());
  const hours = parseInt(document.getElementById("hours").value);
  const difficulty = document.getElementById("difficulty").value;

  if (subjects.length === 0 || !hours) {
    document.getElementById("output").innerText = "⚠️ Please enter all fields.";
    return;
  }

  let multiplier = difficulty === "easy" ? 0.8 : difficulty === "medium" ? 1 : 1.25;
  let timePerSubject = (hours / subjects.length) * multiplier;

  let plan = "📘 Your Personalized Study Plan:\n\n";
  subjects.forEach(sub => {
    plan += `• ${sub}: ${timePerSubject.toFixed(1)} hours/day\n`;
  });

  document.getElementById("output").innerText = plan;
}
</script>

</body>
</html>
