# Callback Functions in JavaScript

## What is a callback function?

A **callback function** is a function that is passed as an argument to another function and is intended to be called or executed later, often after the completion of an asynchronous operation or in response to an event. Callback functions are a fundamental concept in JavaScript, particularly in the context of asynchronous programming.

### Key Points:

1. **Passing as an Argument:**
   - Functions in JavaScript are first-class citizens, allowing them to be treated as values.
   - Callback functions can be passed as arguments to other functions.

2. **Execution at a Later Time:**
   - Callback functions are executed later, after a certain task or operation is complete.

3. **Asynchronous Operations:**
   - Callbacks are commonly used in asynchronous operations, such as reading files, making network requests, or handling events.

4. **Handling Results:**
   - Callbacks are often used to handle the results of asynchronous operations, ensuring that the code inside the callback runs when the operation is finished.

### Example:

```javascript
// Function that takes a callback as an argument
function performOperationAsync(callback) {
  // Simulate an asynchronous operation
  setTimeout(function () {
    // After the operation is complete, call the callback function
    callback("Operation completed");
  }, 1000); // Simulating a 1-second delay
}

// Callback function
function handleResult(result) {
  console.log(result);
}

// Using the performOperationAsync function with a callback
performOperationAsync(handleResult);
