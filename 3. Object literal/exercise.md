# Object literals, Methods, Arrays, Working with Strings, Working with Numbers, and Function Parameters

## Exercises

### 1. Object Literal Practice

- **Objective**: Create an object literal representing a person.
- **Task**: Include properties for name, age, and occupation. Add a method to greet the person.

```javascript
const person = {
  name: "John",
  age: 30,
  occupation: "Developer",
  greet: function () {
    console.log(
      `Hello, my name is ${this.name} and I am a ${this.occupation}.`
    );
  },
};

person.greet();
```

### 2. Array Operations

- **Objective**: Practice array operations.
- **Task**: Create an array of numbers, add a new number to the end, remove the first number, and calculate the sum of all numbers.

```javascript
let numbers = [1, 2, 3];

numbers.push(4); // Add 4 to the end
numbers.shift(); // Remove the first number

let sum = numbers.reduce((total, num) => total + num, 0);
console.log(sum); // Output: 9
```

### 3. String Manipulation

- **Objective**: Understand string manipulation methods.
- **Task**: Create a string and convert it to uppercase, lowercase, and extract a substring.

```javascript
let text = "Hello, World!";
console.log(text.toUpperCase()); // Output: HELLO, WORLD!
console.log(text.toLowerCase()); // Output: hello, world!
console.log(text.substring(7)); // Output: World!
```

## Mini Projects

### 1. Simple Bank Account System

- **Objective**: Create a basic bank account system using object literals.
- **Task**: Implement methods to deposit, withdraw, and check the balance.

```javascript
const account = {
  balance: 1000,
  deposit: function (amount) {
    this.balance += amount;
    console.log(`Deposited $${amount}. New balance: $${this.balance}`);
  },
  withdraw: function (amount) {
    if (amount > this.balance) {
      console.log("Insufficient funds!");
    } else {
      this.balance -= amount;
      console.log(`Withdrew $${amount}. New balance: $${this.balance}`);
    }
  },
  checkBalance: function () {
    console.log(`Your current balance is $${this.balance}`);
  },
};

account.deposit(500);
account.withdraw(200);
account.checkBalance();
```

### 2. To-Do List App

- **Objective**: Build a simple to-do list app using arrays.
- **Task**: Implement functions to add tasks, remove tasks, and display all tasks.

```javascript
let tasks = [];

function addTask(task) {
  tasks.push(task);
  console.log(`Task added: ${task}`);
}

function removeTask(task) {
  const index = tasks.indexOf(task);
  if (index > -1) {
    tasks.splice(index, 1);
    console.log(`Task removed: ${task}`);
  } else {
    console.log(`Task not found: ${task}`);
  }
}

function displayTasks() {
  console.log("Your tasks:");
  tasks.forEach((task) => console.log(task));
}

addTask("Buy groceries");
addTask("Do laundry");
displayTasks();
removeTask("Buy groceries");
displayTasks();
```

### 3. Word Frequency Counter

- **Objective**: Create a program to count the frequency of each word in a given string.
- **Task**: Use string manipulation and object literals to store word frequencies.

```javascript
function countWordFrequencies(text) {
  const words = text.toLowerCase().split(" ");
  const frequency = {};

  words.forEach((word) => {
    if (word in frequency) {
      frequency[word]++;
    } else {
      frequency[word] = 1;
    }
  });

  return frequency;
}

const text = "Hello world hello again";
console.log(countWordFrequencies(text));
```

## Stretched Projects

### 1. Library Management System

- **Objective**: Develop a library management system using object literals and arrays.
- **Task**: Implement methods to add books, remove books, and display all books.

```javascript
let library = {
  books: [],
  addBook: function (title, author) {
    this.books.push({ title, author });
    console.log(`Book added: ${title} by ${author}`);
  },
  removeBook: function (title) {
    const bookIndex = this.books.findIndex((book) => book.title === title);
    if (bookIndex > -1) {
      this.books.splice(bookIndex, 1);
      console.log(`Book removed: ${title}`);
    } else {
      console.log(`Book not found: ${title}`);
    }
  },
  displayBooks: function () {
    console.log("Library Books:");
    this.books.forEach((book) =>
      console.log(`${book.title} by ${book.author}`)
    );
  },
};

library.addBook("1984", "George Orwell");
library.addBook("To Kill a Mockingbird", "Harper Lee");
library.displayBooks();
library.removeBook("1984");
library.displayBooks();
```

### 2. Student Grade Tracker

- **Objective**: Build a student grade tracker using arrays and object literals.
- **Task**: Implement functions to add grades, calculate averages, and display student information.

```javascript
let students = [];

function addStudent(name) {
  students.push({ name, grades: [] });
}

function addGrade(name, grade) {
  const studentIndex = students.findIndex((student) => student.name === name);
  if (studentIndex > -1) {
    students[studentIndex].grades.push(grade);
    console.log(`Grade added for ${name}: ${grade}`);
  } else {
    console.log(`Student not found: ${name}`);
  }
}

function calculateAverage(name) {
  const studentIndex = students.findIndex((student) => student.name === name);
  if (studentIndex > -1) {
    const sum = students[studentIndex].grades.reduce(
      (total, grade) => total + grade,
      0
    );
    const average = sum / students[studentIndex].grades.length;
    console.log(`Average grade for ${name}: ${average}`);
  } else {
    console.log(`Student not found: ${name}`);
  }
}

addStudent("Alice");
addGrade("Alice", 90);
addGrade("Alice", 85);
calculateAverage("Alice");
```

### 3. Weather Forecast System

- **Objective**: Create a simple weather forecast system using object literals and arrays.
- **Task**: Implement methods to add forecasts, remove forecasts, and display all forecasts.

```javascript
let forecasts = {
  data: [],
  addForecast: function (date, temperature) {
    this.data.push({ date, temperature });
    console.log(`Forecast added for ${date}: ${temperature}°C`);
  },
  removeForecast: function (date) {
    const forecastIndex = this.data.findIndex(
      (forecast) => forecast.date === date
    );
    if (forecastIndex > -1) {
      this.data.splice(forecastIndex, 1);
      console.log(`Forecast removed for ${date}`);
    } else {
      console.log(`Forecast not found for ${date}`);
    }
  },
  displayForecasts: function () {
    console.log("Weather Forecasts:");
    this.data.forEach((forecast) =>
      console.log(`${forecast.date}: ${forecast.temperature}°C`)
    );
  },
};

forecasts.addForecast("Monday", 22);
forecasts.addForecast("Tuesday", 25);
forecasts.displayForecasts();
forecasts.removeForecast("Monday");
forecasts.displayForecasts();
```
