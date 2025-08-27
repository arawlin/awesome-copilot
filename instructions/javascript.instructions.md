---
applyTo: '**/*.js, **/*.jsx'
description: 'JavaScript coding conventions and best practices'
---

# JavaScript Coding Conventions

## General Instructions

- Write clear, concise, and maintainable code.
- Follow the principle of least surprise.
- Keep functions small and focused on a single responsibility.
- Use modern JavaScript features (ES6+) where appropriate.
- Ensure code is well-documented, especially public APIs.

## Code Style and Formatting

- Use a consistent code formatter like `Prettier` to maintain a uniform style.
- Follow the Airbnb JavaScript Style Guide.
- Use 2 spaces for indentation.
- Use single quotes for strings, unless template literals are needed.
- Add a semicolon at the end of every statement.

## Naming Conventions

- **Variables and Functions:** Use `camelCase`.
- **Classes:** Use `PascalCase`.
- **Constants:** Use `UPPER_SNAKE_CASE` for constants that are hard-coded and widely used.
- **Private Members:** While JavaScript doesn't have true private members, a common convention is to prefix them with an underscore `_`.
- **Files:** Use `kebab-case` for file names (e.g., `user-profile.component.js`).

## Best Practices

- **`let` and `const`:** Prefer `const` over `let` to avoid accidental reassignment. Use `let` only for variables that need to be reassigned.
- **Arrow Functions:** Use arrow functions for anonymous functions and to maintain the `this` context.
- **Template Literals:** Use template literals for string concatenation.
- **Destructuring:** Use destructuring to extract values from objects and arrays.
- **Spread Operator:** Use the spread operator for copying arrays and objects and for function arguments.
- **Strict Mode:** Use `'use strict';` at the beginning of your files to catch common coding mistakes.

## Error Handling

- Use `try...catch` blocks for handling synchronous errors.
- Use `.catch()` with Promises or `try...catch` with `async/await` for asynchronous errors.
- Create custom error classes that extend `Error` for specific error scenarios.
- Avoid swallowing errors. Always log them or re-throw them.

## Asynchronous Programming

- Prefer `async/await` over Promises for better readability.
- Always handle promise rejections.
- Use `Promise.all` for running multiple promises in parallel.
- Use `Promise.race` when you need the result of the first promise that resolves or rejects.

## Modules and Imports

- Use ES modules (`import`/`export`) for all new code.
- Organize imports in the following order:
  1. Third-party libraries
  2. Internal modules
- Use absolute paths for imports from other modules within the project.

## Testing

- Write unit tests for all business logic.
- Use a testing framework like `Jest` or `Mocha`.
- Use a mocking library like `jest.fn()` or `sinon` to mock dependencies.
- Write integration tests to test the interaction between different modules.
- Write end-to-end tests to test the application as a whole.

## Documentation

- Use JSDoc comments for all public functions and classes.
- Document the purpose of the code, its parameters, and its return value.
- Provide examples of how to use the code.

```javascript
/**
 * Represents a user in the system.
 */
class User {
  /**
   * @param {string} id - The user's ID.
   * @param {string} name - The user's name.
   * @param {string} email - The user's email.
   */
  constructor(id, name, email) {
    this.id = id;
    this.name = name;
    this.email = email;
  }
}

/**
 * Fetches a user by their ID.
 * @param {string} userId - The ID of the user to fetch.
 * @returns {Promise<User>} A promise that resolves to the user object.
 */
async function getUserById(userId) {
  // ...
}
```
