## Exercises and Their Solutions

### 1. Variable Declaration Exercise

- **Objective**: Practice declaring variables using `var`, `let`, and `const`.
- **Task**: Create a JavaScript file and declare three variables for your name, age, and favorite color using each of the three keywords. Log them to the console.

  ```javascript
  var name = "John";
  let age = 28;
  const favoriteColor = "blue";

  console.log(name, age, favoriteColor);
  ```

### 2. Data Type Identification

- **Objective**: Understand different data types in JavaScript.
- **Task**: Create a function that takes a variable as an argument and returns its data type using `typeof`. Test the function with different types of values (string, number, boolean, object).

  ```javascript
  function checkDataType(value) {
    return typeof value;
  }

  console.log(checkDataType("Hello")); // string
  console.log(checkDataType(42)); // number
  console.log(checkDataType(true)); // boolean
  console.log(checkDataType({})); // object
  ```

## Mini Projects

### 1. Personal Profile Card

- **Objective**: Create a simple profile card using JavaScript to display personal information.
- **Task**: Use HTML and CSS to create a basic layout. Use JavaScript to store your name, age, and hobbies in variables and dynamically display them on the webpage.

  ```html
  const name = "John Doe"; const age = 28; const hobbies = ["reading", "gaming",
  "coding"]; document.getElementById("name").textContent = name;
  document.getElementById("age").textContent = `Age: ${age}`;
  document.getElementById("hobbies").textContent = `Hobbies: ${hobbies.join(",
  ")}`;
  ```

### 2. Simple Quiz Application

- **Objective**: Build a basic quiz application that uses variables to store questions and answers.
- **Task**: Create an array of questions and answers. Use a loop to display each question and prompt the user for an answer. Keep track of the score based on correct answers.

```javascript
const questions = [
  { question: "What is the capital of France?", answer: "Paris" },
  { question: "What is 2 + 2?", answer: "4" },
  { question: "What is the color of the sky?", answer: "blue" },
];

let score = 0;

questions.forEach((q) => {
  const userAnswer = prompt(q.question);
  if (userAnswer.toLowerCase() === q.answer.toLowerCase()) {
    score++;
    alert("Correct!");
  } else {
    alert(`Wrong! The correct answer is ${q.answer}.`);
  }
});

alert(`Your score is ${score} out of ${questions.length}.`);
```

## Stretched Projects

### 1. To-Do List Application

- **Objective**: Create a functional to-do list application using JavaScript.
- **Task**:
  - Use HTML/CSS for layout and styling.
  - Allow users to add tasks, mark them as completed, and remove them.
  - Store tasks in an array and update the displayed list dynamically using JavaScript.

```html
Add Task const tasks = []; document.getElementById("addTaskButton").onclick =
function() { const taskInput = document.getElementById("taskInput"); const
taskText = taskInput.value; if (taskText) { tasks.push(taskText);
taskInput.value = ""; // Clear input field renderTasks(); } }; function
renderTasks() { const taskList = document.getElementById("taskList");
taskList.innerHTML = ""; // Clear existing tasks tasks.forEach((task, index) =>
{ const li = document.createElement("li"); li.textContent = task; li.onclick =
function() { tasks.splice(index, 1); // Remove task on click renderTasks(); };
taskList.appendChild(li); }); }
```

### 2. Weather App (Using API)

- **Objective**: Build a weather application that fetches data from a weather API.
- **Task**:
  - Use HTML/CSS for layout.
  - Use JavaScript to fetch weather data based on user input (city name).
  - Display temperature, weather conditions, etc., dynamically on the webpage.

```html
Get Weather document.getElementById("getWeatherButton").onclick = async
function() { const cityName = document.getElementById("cityInput").value; const
apiKey = 'YOUR_API_KEY'; // Replace with your API key const response = await
fetch(`https://api.openweathermap.org/data/2.5/weather?q=${cityName}&appid=${apiKey}&units=metric`);
if (response.ok) { const data = await response.json();
document.getElementById("weatherResult").innerHTML = `Temperature in
${data.name}: ${data.main.temp}°CWeather: ${data.weather[0].description}`; }
else { alert('City not found!'); } };
```
