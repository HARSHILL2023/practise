# JavaScript Execution & Async Programming – Summary

---

## How JavaScript Runs

### Execution Context

* An **execution context** is the environment where JavaScript code runs
* Two main environments:

  * **Browser** (DOM, Web APIs, events)
  * **Node.js** (File System, OS-level APIs)

> Chrome and Node.js both use the **V8 engine**, but their environments and available APIs differ.

---

## JavaScript Characteristics

* JavaScript is **single-threaded**
* Executes one task at a time
* Uses **non-blocking async mechanisms** to handle slow operations efficiently

---

## Thread, Scope & Stack

### Thread

* A **thread** is like a pipeline executing code
* More threads → more parallel work (multi-threaded languages)
* JS has **one main thread**, so poor async handling can slow apps

### Scope

* **Global Scope**
* **Local / Function Scope**
* **Block Scope** (`let`, `const`)

### Call Stack

* Tracks function execution order (LIFO)
* Handles:

  * Lexical scope
  * Closures
* Blocking code stacks up here

---

## Event Loop (Async Brain of JS)

* Moves async tasks back to the call stack when ready
* Not directly visible in browser dev tools

### Priority Rules

1. **Synchronous code** always runs first
2. **Microtask Queue**
3. **Macrotask Queue**

---

## Microtasks vs Macrotasks

### Microtasks (Higher Priority)

* `Promise.then / catch / finally`
* `async / await`
* Callbacks from promises

**Priority (same queue):**

```
Promises ≥ async/await ≥ callbacks
```

### Macrotasks (Lower Priority)

* `setTimeout`
* `setInterval`
* `setImmediate` (Node.js only)

---

## Timers Explained

### setTimeout

* Runs **once** after delay
* Lowest priority
* Browser & Node.js

### setInterval

* Runs **repeatedly** after delay
* Must use `clearInterval()` to avoid memory leaks

### setImmediate (Node.js only)

* Runs **after current execution**
* Higher priority than `setTimeout`

---

## Nodemon

* Development tool for Node.js
* Automatically restarts app on file changes
* Improves developer productivity
* Similar concept to CI/CD auto triggers

---

## Callbacks

### What is a Callback?

* A function passed as an argument
* Executed later

### Why Callbacks?

* Prevent blocking the single JS thread
* Handle async operations

### Callback Hell

* Deeply nested callbacks

#### Problems

* Poor readability
* Hard error handling
* Difficult maintenance

> Should be avoided ❌

---

## Promises (Solution to Callback Hell)

* Cleaner async handling
* Better error flow
* Can directly jump to `.catch()`

---

## Promise Utility Methods

### Promise.all()

* Resolves when **all succeed**
* Rejects if **any fails**
* Use when everything is mandatory

### Promise.allSettled()

* Waits for **all promises**
* Never rejects
* Returns status of each

**Use cases:**

* Reports
* Logs
* Partial UI rendering

### Promise.race()

* First settled promise wins (success or failure)

**Use cases:**

* Timeouts
* Fastest API
* Fallback strategies

### Promise.any()

* First **successful** promise wins
* Rejects only if all fail

**Use cases:**

* Backup APIs
* CDN fallback

### .finally()

* Always executes
* No result/error passed

**Use cases:**

* Hide loaders
* Stop spinners
* Cleanup logic

---

## Best Practices

* Use `Promise.all()` → when all results are required
* Use `Promise.allSettled()` → when partial success is okay
* Use `Promise.race()` → when speed matters
* Use `Promise.any()` → when reliability matters
* Prefer **async/await** for readable async code

---

📅 *Notes Compiled: 1st Jan 2026*
