# Calculator-
Performing arithmetic operations .
#code of html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Calculator</title>
    <link rel="stylesheet" href="style.css">
</head>
<body>
    <div class="calculator">
        <input type="text" id="display" disabled>
        <div class="keys">
            <button id="clear">C</button>
            <button id="backspace">&lt;</button>
            <button id="divide">/</button>
            <button id="seven">7</button>
            <button id="eight">8</button>
            <button id="nine">9</button>
            <button id="multiply">*</button>
            <button id="four">4</button>
            <button id="five">5</button>
            <button id="six">6</button>
            <button id="subtract">-</button>
            <button id="one">1</button>
            <button id="two">2</button>
            <button id="three">3</button>
            <button id="add">+</button>
            <button id="zero">0</button>
            <button id="decimal">.</button>
            <button id="equals">=</button>
        </div>
    </div>
    <script src="script.js"></script>
</body>
</html>

#code of css
.calculator {
    width: 250px;
    margin: 50px auto;
    padding: 20px;
    border: 1px solid #ccc;
    border-radius: 10px;
    box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
}

#display {
    width: 100%;
    height: 40px;
    font-size: 24px;
    text-align: right;
    padding: 10px;
    border: none;
    border-radius: 10px;
    background-color: #f0f0f0;
}

.keys {
    display: grid;
    grid-template-columns: repeat(4, 1fr);
    gap: 10px;
    margin-top: 20px;
}

button {
    height: 40px;
    font-size: 18px;
    border: none;
    border-radius: 10px;
    background-color: #f0f0f0;
    cursor: pointer;
}

button:hover {
    background-color: #ccc;
}

#code of js
let display = document.getElementById('display');
let currentNumber = '';
let previousNumber = '';
let operation = '';

document.querySelectorAll('button').forEach(button => {
    button.addEventListener('click', () => {
        let value = button.textContent;

        if (value === 'C') {
            currentNumber = '';
            previousNumber = '';
            operation = '';
            display.value = '';
        } else if (value === '&lt;') {
            currentNumber = currentNumber.slice(0, -1);
            display.value = currentNumber;
        } else if (['+', '-', '*', '/'].includes(value)) {
            previousNumber = currentNumber;
            currentNumber = '';
            operation = value;
        } else if (value === '=') {
            let result = eval(`${previousNumber} ${operation} ${currentNumber}`);
            display.value = result;
            currentNumber = result.toString();
            previousNumber = '';
            operation = '';
        } else {
            currentNumber += value;
            display.value = currentNumber;
        }
    });
});
