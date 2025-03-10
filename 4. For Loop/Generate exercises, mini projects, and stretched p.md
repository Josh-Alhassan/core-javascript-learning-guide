<img src="https://r2cdn.perplexity.ai/pplx-full-logo-primary-dark%402x.png" class="logo" width="120"/>

# 

---

# Generate exercises, mini projects, and stretched projects based on this topic.

The project/strectched projects should ONLY be based on JavaScript. No HTML or CSS

Here are some exercises, mini-projects, and stretched projects based on the topics of for loops, while loops, for-of loops, do-while loops, for-in loops, nested loops, and higher-order array methods. All projects will focus solely on JavaScript without any HTML or CSS.

## Exercises

### 1. Basic Loop Exercise

- **Objective**: Practice using a for loop to print numbers.
- **Task**: Write a for loop to print numbers from 1 to 10.

```javascript
for (let i = 1; i <= 10; i++) {
    console.log(i);
}
```


### 2. While Loop Exercise

- **Objective**: Understand while loops.
- **Task**: Use a while loop to print numbers from 1 to 5.

```javascript
let i = 1;
while (i <= 5) {
    console.log(i);
    i++;
}
```


### 3. For-Of Loop Exercise

- **Objective**: Practice iterating over an array using a for-of loop.
- **Task**: Create an array of fruits and print each fruit using a for-of loop.

```javascript
const fruits = ["apple", "banana", "cherry"];
for (const fruit of fruits) {
    console.log(fruit);
}
```


## Mini Projects

### 1. Multiplication Table Generator

- **Objective**: Create a program to generate a multiplication table.
- **Task**: Use nested loops to print a multiplication table for numbers 1 through 10.

```javascript
for (let i = 1; i <= 10; i++) {
    for (let j = 1; j <= 10; j++) {
        console.log(`${i} * ${j} = ${i * j}`);
    }
}
```


### 2. Array Sum Calculator

- **Objective**: Calculate the sum of all numbers in an array.
- **Task**: Use the `reduce()` method to sum all numbers in an array.

```javascript
const numbers = [1, 2, 3, 4, 5];
const sum = numbers.reduce((total, num) => total + num, 0);
console.log(`Sum: ${sum}`);
```


### 3. Object Property Printer

- **Objective**: Print all properties of an object.
- **Task**: Use a for-in loop to iterate over an object's properties and print them.

```javascript
const person = { name: "Alice", age: 30, occupation: "Developer" };
for (const key in person) {
    console.log(`${key}: ${person[key]}`);
}
```


## Stretched Projects

### 1. Matrix Operations

- **Objective**: Perform operations on a matrix using nested loops.
- **Task**: Create a function to add two matrices together.

```javascript
function addMatrices(matrix1, matrix2) {
    const result = [];
    for (let i = 0; i < matrix1.length; i++) {
        result[i] = [];
        for (let j = 0; j < matrix1[0].length; j++) {
            result[i][j] = matrix1[i][j] + matrix2[i][j];
        }
    }
    return result;
}

const matrix1 = [[1, 2], [3, 4]];
const matrix2 = [[5, 6], [7, 8]];
console.log(addMatrices(matrix1, matrix2)); // Output: [[6, 8], [10, 12]]
```


### 2. Student Grade Analyzer

- **Objective**: Analyze student grades using higher-order array methods.
- **Task**: Create an array of student objects with grades. Use `filter()` to find students with passing grades and `reduce()` to calculate the average grade.

```javascript
const students = [
    { name: "Alice", grade: 85 },
    { name: "Bob", grade: 70 },
    { name: "Charlie", grade: 90 }
];

const passingStudents = students.filter(student => student.grade >= 80);
console.log("Passing Students:");
passingStudents.forEach(student => console.log(student.name));

const averageGrade = students.reduce((total, student) => total + student.grade, 0) / students.length;
console.log(`Average Grade: ${averageGrade}`);
```


### 3. Sudoku Solver

- **Objective**: Create a basic Sudoku solver using nested loops.
- **Task**: Implement a function to check if a number can be placed in a Sudoku grid and use it to solve a simple Sudoku puzzle.

```javascript
function isValid(board, row, col, num) {
    // Check the row
    for (let i = 0; i < 9; i++) {
        if (board[row][i] === num) {
            return false;
        }
    }

    // Check the column
    for (let i = 0; i < 9; i++) {
        if (board[i][col] === num) {
            return false;
        }
    }

    // Check the box
    const startRow = row - row % 3;
    const startCol = col - col % 3;
    for (let i = 0; i < 3; i++) {
        for (let j = 0; j < 3; j++) {
            if (board[i + startRow][j + startCol] === num) {
                return false;
            }
        }
    }

    return true;
}

function solveSudoku(board) {
    for (let i = 0; i < 9; i++) {
        for (let j = 0; j < 9; j++) {
            if (board[i][j] === 0) {
                for (let num = 1; num <= 9; num++) {
                    if (isValid(board, i, j, num)) {
                        board[i][j] = num;
                        if (solveSudoku(board)) {
                            return true;
                        }
                        board[i][j] = 0;
                    }
                }
                return false;
            }
        }
    }
    return true;
}

const board = [
    [5, 3, 0, 0, 7, 0, 0, 0, 0],
    [6, 0, 0, 1, 9, 5, 0, 0, 0],
    [0, 9, 8, 0, 0, 0, 0, 6, 0],
    [8, 0, 0, 0, 6, 0, 0, 0, 3],
    [4, 0, 0, 8, 0, 3, 0, 0, 1],
    [7, 0, 0, 0, 2, 0, 0, 0, 6],
    [0, 6, 0, 0, 0, 0, 2, 8, 0],
    [0, 0, 0, 4, 1, 9, 0, 0, 5],
    [0, 0, 0, 0, 8, 0, 0, 7, 9]
];

if (solveSudoku(board)) {
    console.log(board);
} else {
    console.log("No solution exists");
}
```

---

## Conclusion

These exercises, mini-projects, and stretched projects will help you practice and reinforce your understanding of loops and higher-order array methods in JavaScript. As you work through these tasks, feel free to experiment with additional features or enhancements to deepen your understanding! Happy coding!

