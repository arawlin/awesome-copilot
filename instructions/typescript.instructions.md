---
applyTo: '**/*.ts, **/*.tsx'
description: 'TypeScript coding conventions and best practices'
---

# TypeScript Coding Conventions

## General Instructions

- Write clear, concise, and maintainable code.
- Follow the principle of least surprise.
- Keep functions small and focused on a single responsibility.
- Use modern TypeScript features where appropriate.
- Ensure code is well-documented, especially public APIs.

## Code Style and Formatting

- Use a consistent code formatter like `Prettier` to maintain a uniform style.
- Follow the Airbnb JavaScript Style Guide where applicable.
- Use 2 spaces for indentation.
- Use single quotes for strings, unless template literals are needed.
- Add a semicolon at the end of every statement.

## Naming Conventions

- **Variables and Functions:** Use `camelCase`.
- **Classes, Interfaces, Enums, and Types:** Use `PascalCase`.
- **Constants:** Use `UPPER_SNAKE_CASE` for constants that are hard-coded and widely used.
- **Private Members:** Prefix private members with an underscore `_`.
- **Files:** Use `kebab-case` for file names (e.g., `user-profile.component.ts`).

## Type Safety and Best Practices

- **Strict Mode:** Enable `strict` mode in `tsconfig.json` for maximum type safety.
- **`any` type:** Avoid using `any`. Use `unknown` for values with an unknown type and perform type checking.
- **Type Inference:** Rely on TypeScript's type inference where possible, but be explicit with types for function signatures and complex data structures.
- **Interfaces vs. Types:** Prefer `interface` for defining the shape of objects and classes. Use `type` for unions, intersections, and more complex types.
- **Readonly:** Use the `readonly` modifier for properties that should not be changed after initialization.
- **Enums:** Use string enums for better readability and debugging.

```typescript
// Good: String enum
enum UserRole {
  Admin = 'ADMIN',
  User = 'USER',
}
```

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
  3. Type imports
- Use absolute paths for imports from other modules within the project.

## Testing

- Write unit tests for all business logic.
- Use a testing framework like `Jest` or `Mocha`.
- Use a mocking library like `jest.fn()` or `sinon` to mock dependencies.
- Write integration tests to test the interaction between different modules.
- Write end-to-end tests to test the application as a whole.

## Documentation

- Use JSDoc comments for all public functions, classes, and interfaces.
- Document the purpose of the code, its parameters, and its return value.
- Provide examples of how to use the code.

```typescript
/**
 * Represents a user in the system.
 */
export interface User {
  id: string;
  name: string;
  email: string;
}

/**
 * Fetches a user by their ID.
 * @param userId The ID of the user to fetch.
 * @returns A promise that resolves to the user object.
 */
async function getUserById(userId: string): Promise<User> {
  // ...
}
```
