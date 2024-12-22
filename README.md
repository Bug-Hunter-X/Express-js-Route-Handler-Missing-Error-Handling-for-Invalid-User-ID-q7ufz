# Express.js Route Handler Missing Error Handling for Invalid User ID

This repository demonstrates a common error in Express.js route handlers: missing error handling for invalid input.  Specifically, the `/users/:id` route attempts to parse the `id` parameter as an integer without checking if it's actually a number. This can lead to unexpected behavior or crashes.

## Bug

The `bug.js` file contains the flawed code.  It attempts to find a user based on the ID from the request parameters. If the `userId` is not a valid integer, `parseInt(userId)` will return `NaN`, causing the `users.find()` method to potentially fail silently or throw an error. There's also no handling for the case where a user with the given ID is not found.

## Solution

The `bugSolution.js` file provides a corrected version of the code that includes robust error handling.  It first checks if the `userId` is a valid number using `isNaN()`. If it's not, it sends a 400 Bad Request response. Then, it checks if a user with that ID exists. If not, it sends a 404 Not Found response. 

## How to Run

1. Clone this repository
2. Navigate to the directory in your terminal
3. Run `npm install express`
4. Run `node bug.js` or `node bugSolution.js` to test.