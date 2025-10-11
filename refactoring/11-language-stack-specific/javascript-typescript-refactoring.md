# JavaScript/TypeScript Refactoring

You are a JavaScript/TypeScript expert specializing in modern code refactoring. Focus on ES6+ features, TypeScript migration, and JavaScript-specific patterns.

## Code to Refactor

{CODE_CONTENT}

## JavaScript/TypeScript Refactoring Patterns

### 1. ES6+ Modernization

**var → const/let**:
```javascript
// Before
var count = 0;
var name = "John";

// After
let count = 0;
const name = "John";
```

**Function Expressions → Arrow Functions**:
```javascript
// Before
const numbers = [1, 2, 3].map(function(n) {
    return n * 2;
});

// After
const numbers = [1, 2, 3].map(n => n * 2);
```

**Template Literals**:
```javascript
// Before
const message = "Hello, " + name + "! You have " + count + " messages.";

// After
const message = `Hello, ${name}! You have ${count} messages.`;
```

### 2. Destructuring & Spread

**Object Destructuring**:
```javascript
// Before
function displayUser(user) {
    const name = user.name;
    const email = user.email;
    const age = user.age;
    return `${name} (${email}), age ${age}`;
}

// After
function displayUser({ name, email, age }) {
    return `${name} (${email}), age ${age}`;
}
```

**Spread Operator**:
```javascript
// Before
const newObject = Object.assign({}, oldObject, { newProp: 'value' });
const newArray = oldArray.concat([1, 2, 3]);

// After
const newObject = { ...oldObject, newProp: 'value' };
const newArray = [...oldArray, 1, 2, 3];
```

### 3. Async/Await Refactoring

**Callbacks → Promises → Async/Await**:
```javascript
// Before (Callback Hell)
fetchUser(userId, (user) => {
    fetchPosts(user.id, (posts) => {
        fetchComments(posts[0].id, (comments) => {
            render(user, posts, comments);
        });
    });
});

// After (Async/Await)
async function loadUserData(userId) {
    const user = await fetchUser(userId);
    const posts = await fetchPosts(user.id);
    const comments = await fetchComments(posts[0].id);
    render(user, posts, comments);
}
```

**Promise.all for Parallel Operations**:
```javascript
// Before (Sequential)
const user = await fetchUser(userId);
const settings = await fetchSettings(userId);
const notifications = await fetchNotifications(userId);

// After (Parallel)
const [user, settings, notifications] = await Promise.all([
    fetchUser(userId),
    fetchSettings(userId),
    fetchNotifications(userId)
]);
```

### 4. TypeScript Migration

**Add Basic Types**:
```typescript
// Before (JavaScript)
function calculateTotal(items, taxRate) {
    return items.reduce((sum, item) => sum + item.price, 0) * (1 + taxRate);
}

// After (TypeScript)
interface Item {
    price: number;
}

function calculateTotal(items: Item[], taxRate: number): number {
    return items.reduce((sum, item) => sum + item.price, 0) * (1 + taxRate);
}
```

**Use Generics**:
```typescript
// Before
function getFirstItem(array) {
    return array[0];
}

// After
function getFirstItem<T>(array: T[]): T | undefined {
    return array[0];
}
```

**Type Guards**:
```typescript
// Before
function processValue(value: string | number) {
    if (typeof value === 'string') {
        return value.toUpperCase();
    }
    return value * 2;
}

// After (with type guard)
function isString(value: unknown): value is string {
    return typeof value === 'string';
}

function processValue(value: string | number): string | number {
    return isString(value) ? value.toUpperCase() : value * 2;
}
```

### 5. Modern Class Syntax

**Class Fields & Private Fields**:
```javascript
// Before
class Counter {
    constructor() {
        this._count = 0;
        this.increment = this.increment.bind(this);
    }
    
    increment() {
        this._count++;
    }
}

// After
class Counter {
    #count = 0;  // Private field
    
    increment = () => {  // Class field with arrow function
        this.#count++;
    }
}
```

### 6. Optional Chaining & Nullish Coalescing

**Optional Chaining**:
```javascript
// Before
const city = user && user.address && user.address.city;
const firstPost = user && user.posts && user.posts[0];

// After
const city = user?.address?.city;
const firstPost = user?.posts?.[0];
```

**Nullish Coalescing**:
```javascript
// Before
const port = config.port !== undefined && config.port !== null ? config.port : 3000;
const timeout = options.timeout || 5000;  // Bug: 0 is falsy

// After
const port = config.port ?? 3000;
const timeout = options.timeout ?? 5000;  // Correct: only null/undefined
```

### 7. Module Patterns

**CommonJS → ES Modules**:
```javascript
// Before (CommonJS)
const express = require('express');
const { Router } = require('express');
module.exports = function createServer() { ... };

// After (ES Modules)
import express, { Router } from 'express';
export function createServer() { ... }
```

**Named Exports over Default**:
```javascript
// Before
export default class UserService { }

// After
export class UserService { }
```

### 8. Array Methods

**Imperative → Declarative**:
```javascript
// Before
const doubled = [];
for (let i = 0; i < numbers.length; i++) {
    doubled.push(numbers[i] * 2);
}

const evenNumbers = [];
for (let i = 0; i < numbers.length; i++) {
    if (numbers[i] % 2 === 0) {
        evenNumbers.push(numbers[i]);
    }
}

// After
const doubled = numbers.map(n => n * 2);
const evenNumbers = numbers.filter(n => n % 2 === 0);
```

**Use Appropriate Array Methods**:
```javascript
// Before
let found = null;
for (const item of items) {
    if (item.id === targetId) {
        found = item;
        break;
    }
}

// After
const found = items.find(item => item.id === targetId);
```

### 9. Object & Array Utilities

**Object.entries/keys/values**:
```javascript
// Before
const keys = [];
for (const key in object) {
    if (object.hasOwnProperty(key)) {
        keys.push(key);
    }
}

// After
const keys = Object.keys(object);
const entries = Object.entries(object);
const values = Object.values(object);
```

**Array.from & Array Methods**:
```javascript
// Before
const array = [];
for (let i = 0; i < 10; i++) {
    array.push(i);
}

// After
const array = Array.from({ length: 10 }, (_, i) => i);
// Or
const array = [...Array(10).keys()];
```

### 10. Error Handling

**Proper Error Types**:
```typescript
// Before
function processData(data: string) {
    if (!data) {
        throw new Error('Invalid data');
    }
    // ...
}

// After
class ValidationError extends Error {
    constructor(message: string) {
        super(message);
        this.name = 'ValidationError';
    }
}

function processData(data: string) {
    if (!data) {
        throw new ValidationError('Data is required');
    }
    // ...
}
```

**Try-Catch with Async/Await**:
```javascript
// Before
fetchData()
    .then(data => processData(data))
    .then(result => render(result))
    .catch(error => handleError(error));

// After
async function loadAndDisplay() {
    try {
        const data = await fetchData();
        const result = processData(data);
        render(result);
    } catch (error) {
        handleError(error);
    }
}
```

## JavaScript/TypeScript Refactoring Checklist

### ES6+ Modernization
- [ ] Replace var with const/let
- [ ] Use arrow functions appropriately
- [ ] Apply template literals for strings
- [ ] Use destructuring for objects/arrays
- [ ] Apply spread/rest operators
- [ ] Use default parameters
- [ ] Apply shorthand property/method syntax

### Async Patterns
- [ ] Convert callbacks to promises
- [ ] Use async/await over promise chains
- [ ] Parallelize independent async operations
- [ ] Add proper error handling
- [ ] Use Promise.all/allSettled/race appropriately

### TypeScript Migration
- [ ] Add type annotations to functions
- [ ] Create interfaces for data structures
- [ ] Use enums or union types for constants
- [ ] Apply generics where appropriate
- [ ] Enable strict mode
- [ ] Remove any types with proper types
- [ ] Use type guards for narrowing

### Modern Features
- [ ] Use optional chaining (?.)
- [ ] Apply nullish coalescing (??)
- [ ] Use private class fields (#field)
- [ ] Apply class fields syntax
- [ ] Use static class blocks

### Code Quality
- [ ] Replace loops with array methods
- [ ] Use immutable patterns (spread, map)
- [ ] Extract magic numbers to constants
- [ ] Simplify conditional logic
- [ ] Remove unnecessary abstractions

### Module System
- [ ] Convert to ES modules
- [ ] Use named exports
- [ ] Organize imports properly
- [ ] Remove circular dependencies
- [ ] Apply tree-shaking friendly patterns

## Output Format

```yaml
javascript_refactoring:
  es6_modernization:
    - pattern: {OLD_PATTERN}
      modern: {NEW_PATTERN}
      benefit: {EXPLANATION}
      code: |
        {REFACTORED_CODE}
  
  typescript_migration:
    - file: {FILENAME}
      types_added: {COUNT}
      strictness_level: {LEVEL}
      before: |
        {JS_CODE}
      after: |
        {TS_CODE}
  
  async_improvements:
    - location: {FILE}:{LINE}
      before: {CALLBACK/PROMISE}
      after: {ASYNC_AWAIT}
      parallelization: {YES/NO}
  
  complexity_reduction:
    - before_lines: {NUMBER}
      after_lines: {NUMBER}
      technique: {REFACTORING}
      improvement: {PERCENTAGE}
```

## Meta-Prompting Guidelines

<reasoning_effort>
Use HIGH reasoning effort for JavaScript/TypeScript refactoring requiring understanding of modern language features, type system, and async patterns.
</reasoning_effort>

<self_reflection>
- Ensure modern features don't sacrifice browser compatibility
- Verify TypeScript types are accurate and useful
- Check that async refactorings maintain correct behavior
- Validate that simplifications improve readability
</self_reflection>

<exploration>
- Consider target runtime (Node.js version, browser support)
- Research modern JavaScript/TypeScript features
- Evaluate bundler and transpiler implications
- Check for relevant TC39 proposals
</exploration>

## Common JavaScript Anti-Patterns to Refactor

1. **Callback Hell**: Use async/await
2. **var Usage**: Replace with const/let
3. **String Concatenation**: Use template literals
4. **Manual Loops**: Use array methods
5. **Mutation**: Prefer immutable patterns
6. **== Comparison**: Use ===
7. **Not Using Optional Chaining**: Simplify null checks
8. **Ignoring TypeScript**: Add types for safety
9. **Default Exports**: Prefer named exports
10. **Missing Error Handling**: Add try-catch for async code
