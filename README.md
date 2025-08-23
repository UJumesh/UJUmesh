<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Skills & Learning Section</title>
  <script src="https://cdn.jsdelivr.net/npm/chart.js"></script>
  <style>
    body {
      font-family: Arial, sans-serif;
      text-align: center;
      background: #f4f4f4;
      margin: 0;
      padding: 0;
    }

    h2 {
      margin: 20px 0;
      font-size: 28px;
      color: #333;
    }

    .skills-container {
      display: flex;
      flex-wrap: wrap;
      justify-content: center;
      gap: 30px;
      margin: 30px auto;
      max-width: 900px;
    }

    .skill {
      width: 180px;
      text-align: center;
    }

    .skill canvas {
      width: 150px !important;
      height: 150px !important;
    }

    .skill-label {
      margin-top: 10px;
      font-size: 20px;
      font-weight: bold;
      color: #222;
    }

    .learning-section {
      margin: 50px auto;
      max-width: 600px;
      background: #fff;
      padding: 25px;
      border-radius: 12px;
      box-shadow: 0 4px 12px rgba(0,0,0,0.1);
    }

    .learning-section h2 {
      font-size: 26px;
      margin-bottom: 20px;
      color: #444;
    }

    .learning-section canvas {
      width: 100% !important;
      height: 400px !important;
    }
  </style>
</head>
<body>
  <h2>My Skills</h2>

  <!-- Skills Circles -->
  <div class="skills-container">
    <div class="skill">
      <canvas id="skill-html"></canvas>
      <div class="skill-label">HTML</div>
    </div>
    <div class="skill">
      <canvas id="skill-css"></canvas>
      <div class="skill-label">CSS</div>
    </div>
    <div class="skill">
      <canvas id="skill-js"></canvas>
      <div class="skill-label">JavaScript</div>
    </div>
    <div class="skill">
      <canvas id="skill-react"></canvas>
      <div class="skill-label">React</div>
    </div>
  </div>

  <!-- Learning Section -->
  <div class="learning-section">
    <h2>📚 Learning Progress</h2>
    <canvas id="learningChart"></canvas>
  </div>

  <script>
    // Skills Progress Circles
    function createCircleChart(canvasId, value, color) {
      new Chart(document.getElementById(canvasId), {
        type: 'doughnut',
        data: {
          datasets: [{
            data: [value, 100 - value],
            backgroundColor: [color, "#eee"],
            borderWidth: 0
          }]
        },
        options: {
          responsive: true,
          cutout: "75%",
          plugins: {
            legend: { display: false },
            tooltip: { enabled: false },
            title: {
              display: true,
              text: value + "%",
              position: "center",
              color: "#333",
              font: {
                size: 22,
                weight: "bold"
              }
            }
          }
        }
      });
    }

    // Create skills circles
    createCircleChart("skill-html", 90, "#E34F26");   // HTML
    createCircleChart("skill-css", 85, "#2965F1");    // CSS
    createCircleChart("skill-js", 75, "#F7DF1E");     // JavaScript
    createCircleChart("skill-react", 65, "#61DBFB");  // React

    // Learning Section Chart (Bar chart)
    const ctx = document.getElementById("learningChart").getContext("2d");
    new Chart(ctx, {
      type: "bar",
      data: {
        labels: ["HTML", "CSS", "JavaScript", "React"],
        datasets: [{
          label: "Learning Progress (%)",
          data: [90, 85, 75, 65],
          backgroundColor: ["#E34F26", "#2965F1", "#F7DF1E", "#61DBFB"]
        }]
      },
      options: {
        responsive: true,
        plugins: {
          legend: { display: false }
        },
        scales: {
          y: { beginAtZero: true, max: 100 }
        }
      }
    });
  </script>
</body>
</html>
