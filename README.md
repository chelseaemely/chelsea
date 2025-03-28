<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Simple Calculator</title>
    <style>
        @import url('https://fonts.googleapis.com/css2?family=Playfair+Display:wght@400;700&family=Poppins:wght@300;500&display=swap');

        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: 'Poppins', sans-serif;
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: center;
            height: 100vh;
            background: linear-gradient(to right, #f9f3f0, #ebe1dc);
            color: #5a4d4d;
        }

        .nav {
            position: absolute;
            top: 20px;
            right: 20px;
        }

        .nav button {
            background: #6b5b5b;
            color: white;
            border: none;
            padding: 10px 15px;
            border-radius: 8px;
            cursor: pointer;
            font-size: 1em;
        }

        .container {
            background: rgba(255, 255, 255, 0.7);
            padding: 30px;
            border-radius: 12px;
            backdrop-filter: blur(10px);
            box-shadow: 0 4px 12px rgba(90, 77, 77, 0.1);
            text-align: center;
            width: 350px;
        }

        h1 {
            font-size: 1.8em;
            font-weight: 700;
            font-family: 'Playfair Display', serif;
            color: #6b5b5b;
            margin-bottom: 10px;
        }

        .calculator {
            display: grid;
            grid-template-columns: repeat(4, 1fr);
            gap: 10px;
            margin-top: 20px;
        }

        input {
            grid-column: span 4;
            padding: 15px;
            font-size: 1.5em;
            text-align: right;
            border: 2px solid #b89b9b;
            border-radius: 8px;
            background: rgba(255, 255, 255, 0.5);
            outline: none;
        }

        button {
            background: linear-gradient(135deg, #c5a6a6, #b38989);
            color: #ffffff;
            border: none;
            padding: 15px;
            font-size: 1.2em;
            border-radius: 10px;
            cursor: pointer;
            transition: 0.3s ease-in-out;
            font-weight: 500;
        }

        button:hover {
            transform: translateY(-2px);
            box-shadow: 0 5px 12px rgba(130, 112, 112, 0.6);
        }

        .equal {
            grid-column: span 2;
            background: #6b5b5b;
        }

        .modal {
            display: none;
            position: fixed;
            top: 50%;
            left: 50%;
            transform: translate(-50%, -50%);
            background: white;
            padding: 20px;
            border-radius: 10px;
            box-shadow: 0 5px 15px rgba(0, 0, 0, 0.3);
            text-align: center;
            z-index: 1000;
        }

        .overlay {
            display: none;
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: rgba(0, 0, 0, 0.5);
            z-index: 999;
        }
    </style>
</head>
<body>
    <div class="nav">
        <button onclick="openAbout()">About</button>
    </div>
    
    <div class="container">
        <h1>Simple Calculator</h1>
        <div class="calculator">
            <input type="text" id="display" disabled>
            <button onclick="clearDisplay()">C</button>
            <button onclick="appendValue('/')">/</button>
            <button onclick="appendValue('*')">*</button>
            <button onclick="appendValue('-')">-</button>
            <button onclick="appendValue('7')">7</button>
            <button onclick="appendValue('8')">8</button>
            <button onclick="appendValue('9')">9</button>
            <button onclick="appendValue('+')">+</button>
            <button onclick="appendValue('4')">4</button>
            <button onclick="appendValue('5')">5</button>
            <button onclick="appendValue('6')">6</button>
            <button class="equal" onclick="calculateResult()">=</button>
            <button onclick="appendValue('1')">1</button>
            <button onclick="appendValue('2')">2</button>
            <button onclick="appendValue('3')">3</button>
            <button onclick="appendValue('0')">0</button>
            <button onclick="appendValue('.')">.</button>
        </div>
    </div>

    <div class="overlay" id="overlay" onclick="closeAbout()"></div>
    <div class="modal" id="aboutModal">
        <h2>About</h2>
        <p>Chelsea Emely Mawikere</p>
        <p>NIM: 231011060002</p>
        <button onclick="closeAbout()">Close</button>
    </div>

    <script>
        function appendValue(value) {
            document.getElementById('display').value += value;
        }

        function clearDisplay() {
            document.getElementById('display').value = '';
        }

        function calculateResult() {
            try {
                document.getElementById('display').value = eval(document.getElementById('display').value);
            } catch (error) {
                document.getElementById('display').value = 'Error';
            }
        }

        function openAbout() {
            document.getElementById('aboutModal').style.display = 'block';
            document.getElementById('overlay').style.display = 'block';
        }

        function closeAbout() {
            document.getElementById('aboutModal').style.display = 'none';
            document.getElementById('overlay').style.display = 'none';
        }
    </script>
</body>
</html>
