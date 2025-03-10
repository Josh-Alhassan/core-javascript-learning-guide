# ES6, DOM, DOM Manipulation, Web Storage, the Window Object, and Execution Context

## Exercises

### 1. ES6 Arrow Functions and Template Literals

- **Objective**: Practice using ES6 features: arrow functions and template literals.
- **Task**: Create a function that takes a name and age as parameters and returns a greeting string using template literals and an arrow function.

```javascript
const createGreeting = (name, age) =>
  `Hello, my name is ${name} and I am ${age} years old.`;

console.log(createGreeting("Alice", 30)); // Output: Hello, my name is Alice and I am 30 years old.
```

### 2. ES6 `let` and `const`

- **Objective**: Understand the difference between `let` and `const`.
- **Task**: Demonstrate the scope and mutability of `let` and `const` variables.

```javascript
let x = 10;
const y = 20;

if (true) {
  let x = 30; // Different scope
  const y = 40; // Different scope
  console.log("Inside block:", x, y); // Output: Inside block: 30 40
}

console.log("Outside block:", x, y); // Output: Outside block: 10 20

x = 50; // Valid reassignment
// y = 60; // Invalid reassignment, will cause an error (uncomment to see)

console.log("After reassignment:", x, y); // Output: After reassignment: 50 20
```

### 3. DOM Simulation - Element Creation

- **Objective**: Simulate DOM element creation using JavaScript objects.
- **Task**: Create a JavaScript object that simulates a DOM element with properties like `id`, `className`, and `textContent`.

```javascript
function createSimulatedElement(tagName, attributes) {
  const element = {
    tagName: tagName,
    attributes: attributes || {},
    textContent: "",
    children: [],
    setAttribute: function (attr, value) {
      this.attributes[attr] = value;
    },
    getAttribute: function (attr) {
      return this.attributes[attr];
    },
    appendChild: function (child) {
      this.children.push(child);
    },
    toString: function () {
      let attrs = Object.entries(this.attributes)
        .map(([key, value]) => `${key}="${value}"`)
        .join(" ");
      let content =
        this.textContent || this.children.map((c) => c.toString()).join("");
      return `<${this.tagName} ${attrs}>${content}</${this.tagName}>`;
    },
  };
  return element;
}

const simulatedDiv = createSimulatedElement("div", {
  id: "myDiv",
  class: "container",
});
simulatedDiv.textContent = "Hello, simulated DOM!";

console.log(simulatedDiv.toString());
// Output: <div id="myDiv" class="container">Hello, simulated DOM!</div>
```

## Mini Projects

### 1. Web Storage Simulator

- **Objective**: Simulate web storage functionality using JavaScript objects.
- **Task**: Create functions to simulate `localStorage.setItem()`, `localStorage.getItem()`, and `localStorage.removeItem()`.

```javascript
const simulatedLocalStorage = {
  data: {},
  setItem: function (key, value) {
    this.data[key] = value.toString();
  },
  getItem: function (key) {
    return this.data[key] || null;
  },
  removeItem: function (key) {
    delete this.data[key];
  },
  clear: function () {
    this.data = {};
  },
};

// Usage
simulatedLocalStorage.setItem("name", "Alice");
console.log(simulatedLocalStorage.getItem("name")); // Output: Alice
simulatedLocalStorage.removeItem("name");
console.log(simulatedLocalStorage.getItem("name")); // Output: null
```

### 2. Window Object Simulator

- **Objective**: Simulate parts of the window object using JavaScript.
- **Task**: Create a simulated `window` object with functions for `alert()`, `prompt()`, and `confirm()`.

```javascript
const simulatedWindow = {
  alert: function (message) {
    console.log("Alert:", message);
  },
  prompt: function (message, defaultValue) {
    console.log("Prompt:", message, "(default:", defaultValue, ")");
    return null; // Simulate no user input
  },
  confirm: function (message) {
    console.log("Confirm:", message);
    return false; // Simulate user clicking "Cancel"
  },
};

// Usage
simulatedWindow.alert("Hello!");
simulatedWindow.prompt("Enter your name:", "Guest");
simulatedWindow.confirm("Are you sure?");
```

### 3. Execution Context Demonstration

- **Objective**: Illustrate how execution context affects variable scope.
- **Task**: Create nested functions to demonstrate variable scope in JavaScript.

```javascript
function outerFunction() {
  let outerVar = "Outer";

  function innerFunction() {
    let innerVar = "Inner";
    console.log(outerVar, innerVar); // Accessing outer scope variable
  }

  innerFunction();
  // console.log(innerVar); // This would cause an error because innerVar is not accessible here
}

outerFunction(); // Output: Outer Inner
```

## Stretched Projects

### 1. Advanced DOM Manipulation Simulator

- **Objective**: Create a more advanced DOM simulation with parent-child relationships and element manipulation.
- **Task**: Implement functions to create, append, and remove simulated DOM elements, and simulate selecting elements by ID and class name.

```javascript
function createSimulatedElement(tagName, attributes) {
  const element = {
    tagName: tagName,
    attributes: attributes || {},
    textContent: "",
    children: [],
    setAttribute: function (attr, value) {
      this.attributes[attr] = value;
    },
    getAttribute: function (attr) {
      return this.attributes[attr];
    },
    appendChild: function (child) {
      this.children.push(child);
      child.parentNode = this; // Simulate parent-child relationship
    },
    removeChild: function (child) {
      const index = this.children.indexOf(child);
      if (index > -1) {
        this.children.splice(index, 1);
        child.parentNode = null; // Remove parent-child relationship
      }
    },
    querySelector: function (selector) {
      // Simple selector simulation (e.g., "#id", ".className")
      if (selector.startsWith("#")) {
        const id = selector.slice(1);
        if (this.attributes.id === id) return this;
      } else if (selector.startsWith(".")) {
        const className = selector.slice(1);
        if (this.attributes.class === className) return this;
      }
      // Basic search within children
      for (const child of this.children) {
        const found = child.querySelector(selector);
        if (found) return found;
      }
      return null;
    },
    toString: function () {
      let attrs = Object.entries(this.attributes)
        .map(([key, value]) => `${key}="${value}"`)
        .join(" ");
      let content =
        this.textContent || this.children.map((c) => c.toString()).join("");
      return `<${this.tagName} ${attrs}>${content}</${this.tagName}>`;
    },
  };
  return element;
}

// Usage
const simulatedDiv = createSimulatedElement("div", { id: "root" });
const simulatedParagraph = createSimulatedElement("p", { class: "message" });
simulatedParagraph.textContent = "Hello, simulated DOM!";
simulatedDiv.appendChild(simulatedParagraph);

console.log(simulatedDiv.querySelector(".message").textContent);
console.log(simulatedDiv.toString());
```

### 2. Advanced Web Storage Simulator with Expiration

- **Objective**: Extend the web storage simulator with expiration times for stored data.
- **Task**: Implement a simulated `localStorage` that allows setting expiration times for stored items, after which they are automatically removed.

```javascript
const simulatedLocalStorageWithExpiration = {
  data: {},
  setItem: function (key, value, expiration) {
    const now = new Date();
    const expiry = now.getTime() + expiration * 1000; // expiration in seconds
    this.data[key] = {
      value: value.toString(),
      expiry: expiry,
    };
  },
  getItem: function (key) {
    const item = this.data[key];
    if (!item) return null;

    const now = new Date();
    if (now.getTime() > item.expiry) {
      this.removeItem(key);
      return null;
    }
    return item.value;
  },
  removeItem: function (key) {
    delete this.data[key];
  },
  clear: function () {
    this.data = {};
  },
};

// Usage
simulatedLocalStorageWithExpiration.setItem("name", "Alice", 10); // Expires in 10 seconds
console.log(simulatedLocalStorageWithExpiration.getItem("name")); // Output: Alice

setTimeout(() => {
  console.log(simulatedLocalStorageWithExpiration.getItem("name")); // Output: null
}, 11000); // After 11 seconds, the item should be expired
```

### 3. Nested Scope and Closure Demonstration

- **Objective**: Create a complex scenario to demonstrate nested scopes and closures.
- **Task**: Implement multiple nested functions with closures to access and modify variables in different scopes.

```javascript
function outerFunction() {
  let outerVar = "Outer";

  function middleFunction() {
    let middleVar = "Middle";

    function innerFunction() {
      let innerVar = "Inner";
      console.log(outerVar, middleVar, innerVar); // Accessing variables from outer scopes
      outerVar = "Outer Modified"; // Modifying outer scope variable
    }

    innerFunction();
    console.log(outerVar, middleVar); // Check if outerVar was modified
  }

  middleFunction();
  console.log(outerVar); // Check if outerVar was modified
}

outerFunction();
```

These exercises, mini-projects, and stretched projects provide a comprehensive way to practice and reinforce your understanding of ES6, DOM (simulated), DOM manipulation (simulated), Web Storage, the Window Object (simulated), and Execution Context in JavaScript without relying on HTML or CSS. As you work through these tasks, feel free to experiment with additional features or enhancements to deepen your understanding! Happy coding!
