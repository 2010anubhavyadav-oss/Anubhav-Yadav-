<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Simple GitHub Calculator</title>
    <link rel="stylesheet" href="style.css">
</head>
<body>
    <div class="calculator">
        <input type="text" id="display" readonly placeholder="0">
        <div class="buttons">
            <button class="btn operator" onclick="clearDisplay()">C</button>
            <button class="btn operator" onclick="deleteLast()">DEL</button>
            <button class="btn operator" onclick="appendValue('%')">%</button>
            <button class="btn operator" onclick="appendValue('/')">/</button>

            <button class="btn" onclick="appendValue('7')">7</button>
            <button class="btn" onclick="appendValue('8')">8</button>
            <button class="btn" onclick="appendValue('9')">9</button>
            <button class="btn operator" onclick="appendValue('*')">*</button>

            <button class="btn" onclick="appendValue('4')">4</button>
            <button class="btn" onclick="appendValue('5')">5</button>
            <button class="btn" onclick="appendValue('6')">6</button>
            <button class="btn operator" onclick="appendValue('-')">-</button>

            <button class="btn" onclick="appendValue('1')">1</button>
            <button class="btn" onclick="appendValue('2')">2</button>
            <button class="btn" onclick="appendValue('3')">3</button>
            <button class="btn operator" onclick="appendValue('+')">+</button>

            <button class="btn zero" onclick="appendValue('0')">0</button>
            <button class="btn" onclick="appendValue('.')">.</button>
            <button class="btn equal" onclick="calculateResult()">=</button>
        </div>
    </div>
    <script src="script.js"></script>
</body>
</html>
* {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
    font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
}

body {
    display: flex;
    justify-content: center;
    align-items: center;
    height: 100vh;
    background-color: #1e1e24;
}

.calculator {
    background-color: #000000;
    padding: 20px;
    border-radius: 20px;
    box-shadow: 0px 10px 30px rgba(0, 0, 0, 0.5);
    width: 340px;
}

#display {
    width: 100%;
    height: 70px;
    background-color: transparent;
    border: none;
    outline: none;
    color: #ffffff;
    font-size: 2.5rem;
    text-align: right;
    padding: 10px;
    margin-bottom: 20px;
}

.buttons {
    display: grid;
    grid-template-columns: repeat(4, 1fr);
    gap: 12px;
}

.btn {
    height: 65px;
    border-radius: 50%;
    border: none;
    outline: none;
    font-size: 1.5rem;
    font-weight: 600;
    background-color: #333333;
    color: #ffffff;
    cursor: pointer;
    transition: background-color 0.2s;
}

.btn:active {
    background-color: #555555;
}

.operator {
    background-color: #a5a5a5;
    color: #000000;
}

.operator:active {
    background-color: #d4d4d4;
}

.equal {
    background-color: #ff9f0a;
    color: #ffffff;
}

.equal:active {
    background-color: #fcc06d;
}

.zero {
    grid-column: span 2;
    border-radius: 30px;
    text-align: left;
    padding-left: 25px;
}
const display = document.getElementById('display');

function appendValue(value) {
    if (display.value === 'Error') {
        display.value = '';
    }
    display.value += value;
}

function clearDisplay() {
    display.value = '';
}

function deleteLast() {
    display.value = display.value.slice(0, -1);
}

function calculateResult() {
    try {
        // Evaluate mathematical expression safely
        if (display.value) {
            display.value = eval(display.value);
        }
    } catch (error) {
        display.value = 'Error';
    }
}
