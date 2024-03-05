# calculater-by-html-css-and-java-script
creating a calculater by using HTML,CSS and java script

<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Rarest Calculator</title>
  <style>
    body {
      font-family: 'Arial', sans-serif;
      display: flex;
      align-items: center;
      justify-content: center;
      height: 100vh;
      margin: 0;
      background-color: #f4f4f4;
      transition: background-color 0.3s;
    }

    #calculator {
      background-color: #fff;
      border-radius: 8px;
      box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
      overflow: hidden;
      width: 350px;
    }

    #display {
      width: 100%;
      padding: 15px;
      font-size: 24px;
      border: none;
      outline: none;
      background-color: #f4f4f4;
      color: #333;
    }

    #history {
      padding: 10px 15px;
      font-size: 14px;
      background-color: #fff;
      color: #777;
    }

    .button {
      width: 20%;
      padding: 15px;
      font-size: 18px;
      border: none;
      cursor: pointer;
      transition: background-color 0.3s;
    }

    .button:hover {
      background-color: #ddd;
    }

    .button.operator {
      background-color: #ff8c00;
      color: #fff;
    }

    .button.double {
      width: 40%;
    }

    .button.equal {
      background-color: #4caf50;
      color: #fff;
    }

    #settings {
      display: flex;
      justify-content: space-between;
      padding: 10px;
      background-color: #f4f4f4;
    }
  </style>
</head>
<body>

<div id="calculator">
  <input type="text" id="display" readonly>
  <div id="history"></div>
  <button class="button" onclick="clearDisplay()">C</button>
  <button class="button operator" onclick="appendToDisplay('/')">/</button>
  <button class="button operator" onclick="appendToDisplay('')"></button>
  <button class="button" onclick="appendToDisplay('7')">7</button>
  <button class="button" onclick="appendToDisplay('8')">8</button>
  <button class="button" onclick="appendToDisplay('9')">9</button>
  <button class="button operator" onclick="appendToDisplay('-')">-</button>
  <button class="button" onclick="appendToDisplay('4')">4</button>
  <button class="button" onclick="appendToDisplay('5')">5</button>
  <button class="button" onclick="appendToDisplay('6')">6</button>
  <button class="button operator" onclick="appendToDisplay('+')">+</button>
  <button class="button" onclick="appendToDisplay('1')">1</button>
  <button class="button" onclick="appendToDisplay('2')">2</button>
  <button class="button" onclick="appendToDisplay('3')">3</button>
  <button class="button double" onclick="appendToDisplay('0')">0</button>
  <button class="button" onclick="appendToDisplay('.')">.</button>
  <button class="button equal" onclick="calculate()">=</button>
  <button class="button double" onclick="toggleSettings()">⚙️</button>
</div>

<div id="settings" style="display: none;">
  <label for="precision">Precision:</label>
  <input type="number" id="precision" min="0" max="10" value="2">
  <label for="themeToggle">Dark Mode:</label>
  <input type="checkbox" id="themeToggle" onchange="toggleDarkMode()">
</div>

<script>
  function appendToDisplay(value) {
    document.getElementById('display').value += value;
  }

  function clearDisplay() {
    document.getElementById('display').value = '';
  }

  function calculate() {
    try {
      const precision = parseInt(document.getElementById('precision').value);
      const result = eval(document.getElementById('display').value).toFixed(precision);
      document.getElementById('history').innerHTML = document.getElementById('display').value + ' = ' + result;
      document.getElementById('display').value = result;
    } catch (error) {
      document.getElementById('display').value = 'Error';
    }
  }

  function toggleSettings() {
    const settings = document.getElementById('settings');
    settings.style.display = settings.style.display === 'none' ? 'flex' : 'none';
  }

  function toggleDarkMode() {
    const calculator = document.getElementById('calculator');
    const currentMode = calculator.style.backgroundColor;

    if (currentMode === 'rgb(255, 255, 255)') {
      calculator.style.backgroundColor = '#282c35';
      document.body.style.backgroundColor = '#1a1e23';
      document.body.style.color = '#fff';
    } else {
      calculator.style.backgroundColor = '#fff';
      document.body.style.backgroundColor = '#f4f4f4';
      document.body.style.color = '#333';
    }
  }
</script>

</body>
</html>
