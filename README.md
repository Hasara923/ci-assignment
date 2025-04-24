# Creating a Simple Continuous Integration (CI) Pipeline Using GitHub Actions

## Project Overview

This project demonstrates how to create a simple Continuous Integration (CI) pipeline using **GitHub Actions** with a basic **JavaScript** project. It includes a simple function to add two numbers and an automated test using **Jest**.

---

##  Technologies Used

- JavaScript (Node.js)
- Jest (Testing Framework)
- Git & GitHub
- GitHub Actions (CI)

---

## Function: sum(a, b)

A basic JavaScript function that returns the sum of two numbers.

```js
function sum(a, b) {
  return a + b;
}
module.exports = sum;
```

---

## Test with Jest

We use Jest to ensure the sum function works correctly.

**Test File: `sum.test.js`**
```js
const sum = require('./sum');

test('adds 1 + 2 to equal 3', () => {
  expect(sum(1, 2)).toBe(3);
});
```

To run the test locally:

```bash
npm install
npm test
```

---

##  GitHub Actions Workflow

A CI pipeline is set up using GitHub Actions to automatically run the test whenever new code is pushed to the repository.

**Workflow File: `.github/workflows/node.js.yml`**
```yaml
name: Node.js CI

on:
  push:
    branches: [main]

jobs:
  build:
    runs-on: ubuntu-latest

    steps:
      - uses: actions/checkout@v2
      - name: Use Node.js
        uses: actions/setup-node@v2
        with:
          node-version: '20'
      - run: npm install
      - run: npm test
```

---

## Simulating Failure and Recovery

To demonstrate CI effectiveness:
1. The `sum` function was modified to return `a - b` (intentional bug).
2. A commit was pushed, and GitHub Actions failed the test.
3. The bug was fixed by restoring the original function.
4. CI ran again and passed the test successfully.

---

## What I Learned

- How to configure a GitHub Actions CI workflow.
- How to write and run unit tests using Jest.
- How CI helps automate testing and ensures code reliability.

---

## Repository Link
https://github.com/Hasara923/ci-assignment.git  
