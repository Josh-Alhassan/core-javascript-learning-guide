<img src="https://r2cdn.perplexity.ai/pplx-full-logo-primary-dark%402x.png" class="logo" width="120"/>

# 

---

# Generate exercises, mini projects, and stretched projects based on this topic.

The project/strectched projects should ONLY be based on JavaScript. No HTML or CSS

Here are some engaging exercises, mini-projects, and stretched projects based on the topics of arithmetic operations, comparison operations, functions, conditionals, and the Math object. All projects will focus solely on JavaScript without any HTML or CSS.

## Exercises

### 1. Basic Arithmetic Operations

- **Objective**: Practice using arithmetic operators.
- **Task**: Write a function that takes two numbers and an operator as arguments and returns the result of the operation.

```javascript
function calculate(num1, num2, operator) {
    switch (operator) {
        case '+':
            return num1 + num2;
        case '-':
            return num1 - num2;
        case '*':
            return num1 * num2;
        case '/':
            return num1 / num2;
        case '%':
            return num1 % num2;
        default:
            return "Invalid operator!";
    }
}

// Example usage:
console.log(calculate(10, 5, '+')); // Output: 15
```


### 2. Comparison Checker

- **Objective**: Understand comparison operations.
- **Task**: Create a function that takes two numbers and returns a string indicating whether the first number is greater than, less than, or equal to the second number.

```javascript
function compareNumbers(num1, num2) {
    if (num1 > num2) {
        return `${num1} is greater than ${num2}`;
    } else if (num1 < num2) {
        return `${num1} is less than ${num2}`;
    } else {
        return `${num1} is equal to ${num2}`;
    }
}

// Example usage:
console.log(compareNumbers(5, 10)); // Output: "5 is less than 10"
```


### 3. Factorial Function

- **Objective**: Practice using functions and conditionals.
- **Task**: Write a recursive function that calculates the factorial of a given number.

```javascript
function factorial(n) {
    if (n === 0 || n === 1) {
        return 1;
    }
    return n * factorial(n - 1);
}

// Example usage:
console.log(factorial(5)); // Output: 120
```


## Mini Projects

### 1. Simple Interest Calculator

- **Objective**: Create a program to calculate simple interest.
- **Task**: Write a function that takes principal amount, rate of interest, and time in years as parameters and returns the calculated simple interest.

```javascript
function calculateSimpleInterest(principal, rate, time) {
    return (principal * rate * time) / 100;
}

// Example usage:
const principal = 1000; // Principal amount
const rate = 5; // Rate of interest
const time = 3; // Time in years
const interest = calculateSimpleInterest(principal, rate, time);
console.log(`Simple Interest: $${interest}`); // Output: Simple Interest: $150
```


### 2. Number Guessing Game

- **Objective**: Build a simple number guessing game.
- **Task**: Create a function that generates a random number between 1 and 100. Allow the user to guess the number and provide feedback on whether their guess was too high, too low, or correct.

```javascript
function numberGuessingGame(userGuess) {
    const randomNumber = Math.floor(Math.random() * 100) + 1;

    if (userGuess === randomNumber) {
        return "Congratulations! You guessed it right!";
    } else if (userGuess > randomNumber) {
        return "Too high! Try again.";
    } else {
        return "Too low! Try again.";
    }
}

// Example usage:
console.log(numberGuessingGame(50)); // Output depends on random number generated
```


### 3. Temperature Converter

- **Objective**: Create a program to convert temperatures between Celsius and Fahrenheit.
- **Task**: Write functions to convert Celsius to Fahrenheit and vice versa.

```javascript
function celsiusToFahrenheit(celsius) {
    return (celsius * 9/5) + 32;
}

function fahrenheitToCelsius(fahrenheit) {
    return (fahrenheit - 32) * 5/9;
}

// Example usage:
console.log(celsiusToFahrenheit(25)); // Output: 77
console.log(fahrenheitToCelsius(77)); // Output: 25
```


## Stretched Projects

### 1. Shopping Cart Total Calculator

- **Objective**: Simulate a shopping cart system that calculates total cost with discounts.
- **Task**:
    - Create an array to hold item prices.
    - Write functions to add items to the cart, apply discounts, and calculate the total price.

```javascript
let cart = [];

function addItem(price) {
    cart.push(price);
}

function applyDiscount(discountPercentage) {
    const total = calculateTotal();
    const discountAmount = (total * discountPercentage) / 100;
    return total - discountAmount;
}

function calculateTotal() {
    return cart.reduce((accumulatedTotal, itemPrice) => accumulatedTotal + itemPrice, 0);
}

// Example usage:
addItem(20);
addItem(30);
addItem(50);
console.log(`Total before discount: $${calculateTotal()}`); // Output: Total before discount: $100
console.log(`Total after applying discount of 10%: $${applyDiscount(10)}`); // Output depends on discount applied
```


### 2. BMI Calculator

- **Objective**: Build a Body Mass Index (BMI) calculator.
- **Task**:
    - Write a function that takes weight (in kg) and height (in meters), calculates BMI, and returns a category based on BMI value.

```javascript
function calculateBMI(weight, height) {
    const bmi = weight / (height * height);
    
    if (bmi < 18.5) {
        return `Your BMI is ${bmi.toFixed(2)}. You are underweight.`;
    } else if (bmi < 24.9) {
        return `Your BMI is ${bmi.toFixed(2)}. You have a normal weight.`;
    } else if (bmi < 29.9) {
        return `Your BMI is ${bmi.toFixed(2)}. You are overweight.`;
    } else {
        return `Your BMI is ${bmi.toFixed(2)}. You are obese.`;
    }
}

// Example usage:
console.log(calculateBMI(70, 1.75)); // Output depends on weight and height provided
```


### 3. Rock-Paper-Scissors Game with Score Tracking

- **Objective**: Create an interactive Rock-Paper-Scissors game where users can play multiple rounds.
- **Task**:
    - Use functions to handle user input for choices.
    - Keep track of scores for both the user and computer over multiple rounds.

```javascript
let userScore = 0;
let computerScore = 0;

function playRound(userChoice) {
    const choices = ["rock", "paper", "scissors"];
    const computerChoice = choices[Math.floor(Math.random() * choices.length)];
    
    console.log(`You chose: ${userChoice}`);
    console.log(`Computer chose: ${computerChoice}`);

    if (userChoice === computerChoice) {
        console.log("It's a tie!");
    } else if (
        (userChoice === "rock" && computerChoice === "scissors") ||
        (userChoice === "paper" && computerChoice === "rock") ||
        (userChoice === "scissors" && computerChoice === "paper")
    ) {
        userScore++;
        console.log("You win this round!");
    } else {
        computerScore++;
        console.log("You lose this round!");
    }
    
    console.log(`Score - You: ${userScore}, Computer: ${computerScore}`);
}

// Example usage for multiple rounds:
// playRound("rock");
// playRound("paper");
// playRound("scissors");
```

---

## Conclusion

These exercises, mini-projects, and stretched projects provide ample opportunity for you to practice arithmetic operations, comparison operations, functions, conditionals, and using the Math object in JavaScript. As you work through these tasks, don't hesitate to experiment with additional features or enhancements to deepen your understanding! Happy coding!

