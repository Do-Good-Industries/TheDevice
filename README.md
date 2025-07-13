<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <title>Safety Deposit Box</title>
  <style>
    body {
      margin: 0;
      padding: 0;
      background: url('https://i.imgur.com/9fplPzG.jpg') no-repeat center center fixed;
      background-size: cover;
      font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
    }

    .container {
      position: relative;
      width: 800px;
      height: 500px;
      margin: 100px auto;
      background: #333;
      border: 8px solid #777;
      border-radius: 10px;
      box-shadow: 0 0 30px rgba(0,0,0,0.7);
      overflow: hidden;
    }

    .keypad {
      position: absolute;
      top: 20px;
      right: 20px;
      background: #222;
      padding: 10px;
      border-radius: 8px;
      display: grid;
      grid-template-columns: repeat(3, 50px);
      grid-gap: 10px;
    }

    .keypad button {
      background: #444;
      border: none;
      colour: white;
      font-size: 20px;
      border-radius: 5px;
      cursor: pointer;
      transition: background 0.2s;
    }

    .keypad button:hover {
      background: #666;
    }

    .display {
      position: absolute;
      top: 20px;
      left: 20px;
      background: black;
      colour: #0f0;
      font-size: 24px;
      padding: 10px 20px;
      border-radius: 8px;
      letter-spacing: 8px;
    }

    .document {
      position: absolute;
      top: 100px;
      left: 100px;
      width: 600px;
      height: 300px;
      background: #fef9e7;
      border: 2px solid #ccc;
      border-radius: 10px;
      padding: 20px;
      font-family: 'Courier New', Courier, monospace;
      font-size: 18px;
      box-shadow: inset 0 0 20px rgba(0,0,0,0.3);
      display: none;
    }

    .document.visible {
      display: block;
    }
  </style>
</head>
<body>
  <div class="container">
    <div class="display" id="codeDisplay">____</div>

    <div class="keypad">
      <button onclick="pressKey('1')">1</button>
      <button onclick="pressKey('2')">2</button>
      <button onclick="pressKey('3')">3</button>
      <button onclick="pressKey('4')">4</button>
      <button onclick="pressKey('5')">5</button>
      <button onclick="pressKey('6')">6</button>
      <button onclick="pressKey('7')">7</button>
      <button onclick="pressKey('8')">8</button>
      <button onclick="pressKey('9')">9</button>
      <button onclick="clearCode()">C</button>
      <button onclick="pressKey('0')">0</button>
      <button onclick="submitCode()">⏎</button>
    </div>

    <div class="document" id="document">
      <h2>Classified Cipher Document</h2>
      <p>
        The treasure lies where numbers reverse,<br>
        A mirror of time, a twisted curse.<br>
        ROT13 hides what once was seen,<br>
        Decode to find what lies between.
      </p>
      <p><strong>Encrypted:</strong> Gur genvar vf va gur pnfgre.</p>
    </div>
  </div>

  <script>
    let enteredCode = "";

    function pressKey(num) {
      if (enteredCode.length < 4) {
        enteredCode += num;
        updateDisplay();
      }
    }

    function clearCode() {
      enteredCode = "";
      updateDisplay();
    }

    function updateDisplay() {
      const display = document.getElementById("codeDisplay");
      display.textContent = enteredCode.padEnd(4, '_');
    }

    function submitCode() {
      if (enteredCode === "1066") {
        document.getElementById("document").classList.add("visible");
        document.getElementById("codeDisplay").textContent = "✔️✔️✔️✔️";
      } else {
        document.getElementById("codeDisplay").textContent = "❌❌❌❌";
        setTimeout(() => {
          clearCode();
        }, 1000);
      }
    }
  </script>
</body>
</html>
