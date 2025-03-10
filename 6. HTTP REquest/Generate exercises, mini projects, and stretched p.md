<img src="https://r2cdn.perplexity.ai/pplx-full-logo-primary-dark%402x.png" class="logo" width="120"/>

# 

---

# Generate exercises, mini projects, and stretched projects based on this topic.

The project/strectched projects should ONLY be based on JavaScript. No HTML or CSS

Here are exercises, mini-projects, and stretched projects focused on **asynchronous JavaScript, XHRs, Promises, Fetch API, simulated version control, and modular JavaScript** – all using pure JavaScript (no HTML/CSS).

---

## **Exercises**

**1. Basic Promise Exercise**

```javascript
// Create a promise that resolves after 2 seconds with "Success!"
function createDelay() {
  return new Promise((resolve) => {
    setTimeout(() => resolve("Success!"), 2000);
  });
}

// Call the function and log the result
createDelay().then(console.log); // Output after 2s: "Success!"
```

**2. Fetch API Practice**

```javascript
// Fetch data from JSONPlaceholder (a fake API)
async function fetchTodo() {
  try {
    const response = await fetch('https://jsonplaceholder.typicode.com/todos/1');
    const data = await response.json();
    console.log(data);
  } catch (error) {
    console.log("Error:", error);
  }
}

fetchTodo(); // Output: { userId: 1, id: 1, title: "...", completed: false }
```

**3. Simulated Git Commits**

```javascript
// Simulate Git version control with a JavaScript class
class VersionControl {
  constructor() {
    this.commits = [];
    this.currentCommit = null;
  }

  commit(message) {
    const commit = { id: Date.now(), message };
    this.commits.push(commit);
    this.currentCommit = commit;
    return commit;
  }
}

// Usage
const repo = new VersionControl();
repo.commit("Initial commit");
console.log(repo.commits); // Output: [{ id: ..., message: "Initial commit" }]
```

---

## **Mini Projects**

### **1. XHR-to-Promise Converter**

Convert legacy XHR code to a Promise-based function.

```javascript
function fetchWithXHR(url) {
  return new Promise((resolve, reject) => {
    const xhr = new XMLHttpRequest();
    xhr.open('GET', url);
    xhr.onload = () => resolve(xhr.responseText);
    xhr.onerror = () => reject("Request failed");
    xhr.send();
  });
}

// Usage
fetchWithXHR('https://jsonplaceholder.typicode.com/posts/1')
  .then(console.log) // Output: JSON data for post 1
  .catch(console.error);
```


### **2. Retry Mechanism for Failed Requests**

```javascript
async function fetchWithRetry(url, retries = 3) {
  for (let i = 0; i < retries; i++) {
    try {
      const response = await fetch(url);
      return await response.json();
    } catch (error) {
      if (i === retries - 1) throw error;
      console.log(`Retrying... (${i + 1}/${retries})`);
    }
  }
}

// Usage (simulate a failing URL)
fetchWithRetry('https://fake-api.example.com/data').catch(() => 
  console.log("All retries failed")
);
```


### **3. Modular Task Manager**

```javascript
// taskManager.js (module)
export const tasks = [];

export function addTask(task) {
  tasks.push(task);
}

export function listTasks() {
  return tasks;
}

// app.js (main file)
import { addTask, listTasks } from './taskManager.js';

addTask("Learn Promises");
addTask("Practice Fetch API");
console.log(listTasks()); // Output: ["Learn Promises", "Practice Fetch API"]
```

---

## **Stretched Projects**

### **1. Async Workflow Orchestrator**

Build a pipeline that runs async tasks in sequence and handles errors.

```javascript
async function runPipeline(tasks) {
  const results = [];
  for (const task of tasks) {
    try {
      const result = await task();
      results.push(result);
    } catch (error) {
      console.log(`Pipeline failed at step ${tasks.indexOf(task) + 1}:`, error);
      break;
    }
  }
  return results;
}

// Example tasks
const tasks = [
  () => fetch('https://jsonplaceholder.typicode.com/posts/1').then(res => res.json()),
  () => Promise.reject("Simulated error"),
  () => fetch('https://jsonplaceholder.typicode.com/posts/2').then(res => res.json())
];

runPipeline(tasks).then(console.log); // Output: [post1, Pipeline failed...]
```


### **2. Version Control Simulator with Branches**

```javascript
class AdvancedVersionControl {
  constructor() {
    this.commits = [];
    this.branches = { main: [] };
    this.currentBranch = 'main';
  }

  commit(message) {
    const commit = { id: Date.now(), message, branch: this.currentBranch };
    this.commits.push(commit);
    this.branches[this.currentBranch].push(commit);
    return commit;
  }

  createBranch(name) {
    this.branches[name] = [...this.branches[this.currentBranch]];
  }

  checkout(branch) {
    this.currentBranch = branch;
  }
}

// Usage
const repo = new AdvancedVersionControl();
repo.commit("First commit");
repo.createBranch("dev");
repo.checkout("dev");
repo.commit("Add feature");
console.log(repo.branches);
```


### **3. API Client with Caching**

```javascript
const apiCache = new Map();

async function fetchWithCache(url) {
  if (apiCache.has(url)) {
    console.log("Using cached data");
    return apiCache.get(url);
  }

  const response = await fetch(url);
  const data = await response.json();
  apiCache.set(url, data);
  return data;
}

// Usage
fetchWithCache('https://jsonplaceholder.typicode.com/posts/1')
  .then(() => fetchWithCache('https://jsonplaceholder.typicode.com/posts/1')); // Uses cache
```

---

## **How to Use These**

1. Run code in a Node.js environment or browser console.
2. For modular projects, use ES6 modules with `import/export`.
3. Replace API URLs with real endpoints for testing.

These exercises will help you master async workflows, modular code, and even simulate version control concepts in pure JavaScript! 🚀

