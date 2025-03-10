# Introduction to JavaScript

## Mini Projects

### 1. **Temperature Converter**

- **Objective**: Create a program that converts temperatures between Celsius and Fahrenheit.
- **Task**:
  - Use variables to store the temperature and the conversion formula.
  - Allow the user to input a temperature in Celsius or Fahrenheit and convert it to the other unit.

```javascript
function convertTemperature(temp, unit) {
  if (unit === "C") {
    return (temp * 9) / 5 + 32; // Convert Celsius to Fahrenheit
  } else if (unit === "F") {
    return ((temp - 32) * 5) / 9; // Convert Fahrenheit to Celsius
  } else {
    return "Invalid unit. Use 'C' for Celsius or 'F' for Fahrenheit.";
  }
}

const temperature = 30; // Example: Replace with any number
const unit = "C"; // Replace with "C" for Celsius or "F" for Fahrenheit
const result = convertTemperature(temperature, unit);
console.log(`Converted Temperature: ${result}`);
```

---

### 2. **Simple Calculator**

- **Objective**: Build a calculator program that performs basic arithmetic operations.
- **Task**:
  - Use variables to store two numbers and an operator (`+`, `-`, `*`, `/`).
  - Perform the operation based on the operator provided.

```javascript
function calculator(num1, num2, operator) {
  if (operator === "+") {
    return num1 + num2;
  } else if (operator === "-") {
    return num1 - num2;
  } else if (operator === "*") {
    return num1 * num2;
  } else if (operator === "/") {
    return num1 / num2;
  } else {
    return "Invalid operator. Use '+', '-', '*', or '/'.";
  }
}

const number1 = 10; // Replace with any number
const number2 = 5; // Replace with any number
const operation = "+"; // Replace with '+', '-', '*', or '/'
const result = calculator(number1, number2, operation);
console.log(`Result: ${result}`);
```

---

### 3. **Random Number Guessing Game**

- **Objective**: Create a simple game where the computer generates a random number, and the user has to guess it.
- **Task**:
  - Use variables to store the random number and the user's guess.
  - Provide feedback on whether the guess is too high, too low, or correct.

```javascript
function guessingGame() {
    const randomNumber = Math.floor(Math.random() * 100) + 1; // Random number between 1 and 100
    let guess;
    let attempts = 0;

    while (guess !== randomNumber) {
        guess = parseInt(prompt("Guess a number between 1 and 100:"));
        attempts++;

        if (guess > randomNumber) {
            console.log("Too high! Try again.");
        } else if (guess  balance) {
        console.log("Insufficient funds!");
    } else {
        balance -= amount;
        console.log(`You withdrew $${amount}. New balance: $${balance}`);
    }
}

function checkBalance() {
    console.log(`Your current balance is $${balance}`);
}

// Example usage:
deposit(500);       // Deposit $500
withdraw(300);      // Withdraw $300
checkBalance();     // Check current balance
```

---

### 2. **Rock-Paper-Scissors Game**

- **Objective**: Create a Rock-Paper-Scissors game where the user plays against the computer.
- **Task**:
  - Use variables to store choices for both the user and computer.
  - Determine the winner based on standard Rock-Paper-Scissors rules.

```javascript
function playRockPaperScissors(userChoice) {
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
    console.log("You win!");
  } else {
    console.log("You lose!");
  }
}

// Example usage:
playRockPaperScissors("rock"); // Replace with "rock", "paper", or "scissors"
```

---

### 3. **Shopping Cart System**

- **Objective**: Simulate a simple shopping cart system where users can add items, remove items, and view their cart.
- **Task**:
  - Use an array to store items in the cart.
  - Implement functions for adding items, removing items, and displaying all items in the cart.

```javascript
let shoppingCart = [];

function addItem(item) {
  shoppingCart.push(item);
  console.log(`${item} added to your cart.`);
}

function removeItem(item) {
  const index = shoppingCart.indexOf(item);

  if (index > -1) {
    shoppingCart.splice(index, 1);
    console.log(`${item} removed from your cart.`);
  } else {
    console.log(`${item} is not in your cart.`);
  }
}

function viewCart() {
  if (shoppingCart.length > 0) {
    console.log("Your shopping cart contains:");
    shoppingCart.forEach((item, index) => console.log(`${index + 1}. ${item}`));
  } else {
    console.log("Your shopping cart is empty.");
  }
}

// Example usage:
addItem("Apple");
addItem("Banana");
viewCart();
removeItem("Apple");
viewCart();
```

---

### 4. **Simple Budget Tracker**

- **Objective**: Build a program that tracks expenses and calculates remaining budget.
- **Task**:
  - Use variables to store total budget and expenses.
  - Add functionality to track expenses and calculate remaining budget.

```javascript
let totalBudget = 1000; // Starting budget
let expenses = [];

function addExpense(description, amount) {
  expenses.push({ description, amount });
  totalBudget -= amount;

  console.log(
    `Added expense: ${description} ($${amount}). Remaining budget: $${totalBudget}`
  );
}

function viewExpenses() {
  console.log("Your expenses:");

  expenses.forEach((expense, index) =>
    console.log(`${index + 1}. ${expense.description}: $${expense.amount}`)
  );
}

function checkRemainingBudget() {
  console.log(`Remaining budget: $${totalBudget}`);
}

// Example usage:
addExpense("Groceries", 200);
addExpense("Rent", 500);
viewExpenses();
checkRemainingBudget();
```
