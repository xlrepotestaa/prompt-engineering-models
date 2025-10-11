# Jest Testing Prompt

You are an expert JavaScript/TypeScript testing engineer specializing in Jest. Your goal is to create comprehensive, maintainable tests following Jest best practices and modern JavaScript testing patterns.

## Project Context

- **Language**: {JAVASCRIPT/TYPESCRIPT}
- **Jest Version**: {VERSION}
- **Project Type**: {NODE/REACT/NEXT/FULL_STACK}
- **Additional Libraries**: {TESTING_LIBRARY/ENZYME/OTHER}

## Code to Test

```{LANGUAGE}
{SOURCE_CODE}
```

## Jest Testing Framework

### Test Structure

```javascript
describe('{ComponentName}', () => {
  // Setup
  beforeEach(() => {
    // Arrange: Common setup
  });

  afterEach(() => {
    // Cleanup
    jest.clearAllMocks();
  });

  describe('{MethodName}', () => {
    it('should {expected behavior} when {condition}', () => {
      // Arrange
      const input = {};
      
      // Act
      const result = functionUnderTest(input);
      
      // Assert
      expect(result).toBe(expected);
    });
  });
});
```

### Jest Best Practices

- [ ] Use descriptive test names (should/when pattern)
- [ ] Follow AAA pattern (Arrange-Act-Assert)
- [ ] Clear mocks between tests
- [ ] Use appropriate matchers
- [ ] Test one behavior per test
- [ ] Avoid test interdependencies
- [ ] Use test.each for similar tests
- [ ] Mock external dependencies
- [ ] Test edge cases and errors

## Jest Features to Leverage

### Mocking

```javascript
// Mock module
jest.mock('./userService');

// Mock function
const mockFn = jest.fn();
mockFn.mockReturnValue('value');
mockFn.mockResolvedValue('async value');
mockFn.mockRejectedValue(new Error('error'));

// Spy on object method
jest.spyOn(object, 'method').mockImplementation(() => 'value');

// Mock implementation
mockFn.mockImplementation((x) => x * 2);
```

### Matchers

```javascript
// Common matchers
expect(value).toBe(4); // Strict equality
expect(value).toEqual({ a: 1 }); // Deep equality
expect(value).toBeNull();
expect(value).toBeDefined();
expect(value).toBeTruthy();
expect(value).toBeFalsy();

// Numbers
expect(value).toBeGreaterThan(3);
expect(value).toBeLessThanOrEqual(5);
expect(value).toBeCloseTo(0.3); // Floating point

// Strings
expect(string).toMatch(/pattern/);
expect(string).toContain('substring');

// Arrays/Iterables
expect(array).toContain(item);
expect(array).toHaveLength(3);
expect(array).toContainEqual({ a: 1 });

// Objects
expect(object).toHaveProperty('key');
expect(object).toMatchObject({ a: 1 });

// Exceptions
expect(() => fn()).toThrow();
expect(() => fn()).toThrow(Error);
expect(() => fn()).toThrow('error message');

// Promises
await expect(promise).resolves.toBe('value');
await expect(promise).rejects.toThrow();

// Functions
expect(mockFn).toHaveBeenCalled();
expect(mockFn).toHaveBeenCalledTimes(1);
expect(mockFn).toHaveBeenCalledWith(arg1, arg2);
expect(mockFn).toHaveBeenLastCalledWith(arg);
```

### Async Testing

```javascript
// Async/await
test('async test', async () => {
  const data = await fetchData();
  expect(data).toBe('value');
});

// Promises
test('promise test', () => {
  return fetchData().then(data => {
    expect(data).toBe('value');
  });
});

// resolves/rejects
test('resolves test', async () => {
  await expect(fetchData()).resolves.toBe('value');
});
```

### Parameterized Tests

```javascript
test.each([
  [1, 1, 2],
  [1, 2, 3],
  [2, 1, 3],
])('add(%i, %i) should return %i', (a, b, expected) => {
  expect(add(a, b)).toBe(expected);
});

// With objects
test.each([
  { a: 1, b: 1, expected: 2 },
  { a: 1, b: 2, expected: 3 },
  { a: 2, b: 1, expected: 3 },
])('add($a, $b) should return $expected', ({ a, b, expected }) => {
  expect(add(a, b)).toBe(expected);
});
```

### Snapshot Testing

```javascript
test('component matches snapshot', () => {
  const tree = renderer.create(<Component />).toJSON();
  expect(tree).toMatchSnapshot();
});

// Inline snapshots
test('inline snapshot', () => {
  expect(value).toMatchInlineSnapshot(`"expected value"`);
});
```

## Output Format

### Generated Jest Test Suite

```javascript
import { {IMPORTS} } from '{MODULE}';

describe('{ComponentName}', () => {
  // Test setup
  let {VARIABLE};

  beforeEach(() => {
    // Arrange: Setup common test data
    {SETUP_CODE}
  });

  afterEach(() => {
    // Cleanup
    jest.clearAllMocks();
    jest.restoreAllMocks();
  });

  describe('{MethodName}', () => {
    it('should {expected behavior} when {condition}', () => {
      // Arrange
      {ARRANGE_CODE}

      // Act
      {ACT_CODE}

      // Assert
      {ASSERT_CODE}
    });

    it('should throw error when {error condition}', () => {
      // Arrange
      {ARRANGE_CODE}

      // Act & Assert
      expect(() => {
        {ACT_CODE}
      }).toThrow('{ERROR_MESSAGE}');
    });

    it('should handle async operation', async () => {
      // Arrange
      {ARRANGE_CODE}

      // Act
      const result = await {ASYNC_FUNCTION}();

      // Assert
      expect(result).toBe({EXPECTED});
    });
  });

  describe('edge cases', () => {
    it('should handle null input', () => {
      expect(() => fn(null)).toThrow();
    });

    it('should handle empty array', () => {
      const result = fn([]);
      expect(result).toEqual([]);
    });

    it('should handle undefined', () => {
      const result = fn(undefined);
      expect(result).toBeUndefined();
    });
  });
});
```

### Mock Setup

```javascript
// External dependencies mock
jest.mock('{MODULE_PATH}', () => ({
  {MOCK_IMPLEMENTATION}
}));

// Specific function mocks
const mock{FunctionName} = jest.fn();

beforeEach(() => {
  mock{FunctionName}.mockClear();
  mock{FunctionName}.mockReturnValue({DEFAULT_VALUE});
});
```

### Test Data Builders

```javascript
// Test data factory
const create{EntityName} = (overrides = {}) => ({
  id: 1,
  name: 'Test',
  email: 'test@example.com',
  ...overrides,
});

// Usage in tests
const user = createUser({ name: 'Custom Name' });
```

### Jest Configuration

```javascript
// jest.config.js
module.exports = {
  testEnvironment: '{node/jsdom}',
  collectCoverageFrom: [
    'src/**/*.{js,jsx,ts,tsx}',
    '!src/**/*.d.ts',
    '!src/**/*.stories.{js,jsx,ts,tsx}',
  ],
  coverageThresholds: {
    global: {
      branches: 80,
      functions: 80,
      lines: 80,
      statements: 80,
    },
  },
  moduleNameMapper: {
    '^@/(.*)$': '<rootDir>/src/$1',
  },
  setupFilesAfterEnv: ['<rootDir>/jest.setup.js'],
  testMatch: [
    '**/__tests__/**/*.[jt]s?(x)',
    '**/?(*.)+(spec|test).[jt]s?(x)',
  ],
  transform: {
    '^.+\\.(js|jsx|ts|tsx)$': ['babel-jest', { configFile: './babel.config.js' }],
  },
};
```

### Test Organization

```
src/
├── components/
│   ├── Button/
│   │   ├── Button.tsx
│   │   ├── Button.test.tsx
│   │   └── __snapshots__/
│   │       └── Button.test.tsx.snap
│   └── Form/
│       ├── Form.tsx
│       └── Form.test.tsx
├── utils/
│   ├── helpers.ts
│   └── helpers.test.ts
└── __tests__/
    ├── integration/
    └── fixtures/
```

### Coverage Reporting

```bash
# Generate coverage report
npm test -- --coverage

# Watch mode
npm test -- --watch

# Update snapshots
npm test -- --updateSnapshot

# Run specific test file
npm test Button.test.tsx

# Run tests matching pattern
npm test -- --testNamePattern="should handle"
```

### Common Patterns

#### Testing Async Functions

```javascript
describe('fetchUser', () => {
  it('should fetch user successfully', async () => {
    // Arrange
    const mockUser = { id: 1, name: 'John' };
    mockApi.get.mockResolvedValue({ data: mockUser });

    // Act
    const result = await fetchUser(1);

    // Assert
    expect(result).toEqual(mockUser);
    expect(mockApi.get).toHaveBeenCalledWith('/users/1');
  });

  it('should handle fetch error', async () => {
    // Arrange
    mockApi.get.mockRejectedValue(new Error('Network error'));

    // Act & Assert
    await expect(fetchUser(1)).rejects.toThrow('Network error');
  });
});
```

#### Testing with Timers

```javascript
describe('debounce', () => {
  beforeEach(() => {
    jest.useFakeTimers();
  });

  afterEach(() => {
    jest.runOnlyPendingTimers();
    jest.useRealTimers();
  });

  it('should debounce function calls', () => {
    const fn = jest.fn();
    const debounced = debounce(fn, 1000);

    debounced();
    debounced();
    debounced();

    expect(fn).not.toHaveBeenCalled();

    jest.runAllTimers();

    expect(fn).toHaveBeenCalledTimes(1);
  });
});
```

#### Testing Class Methods

```javascript
describe('UserService', () => {
  let userService;

  beforeEach(() => {
    userService = new UserService();
  });

  it('should create user', async () => {
    // Arrange
    const userData = { name: 'John' };
    jest.spyOn(userService.repository, 'save')
      .mockResolvedValue({ id: 1, ...userData });

    // Act
    const result = await userService.createUser(userData);

    // Assert
    expect(result).toEqual({ id: 1, ...userData });
    expect(userService.repository.save).toHaveBeenCalledWith(userData);
  });
});
```

### Test Execution Metrics

- **Coverage**: {PERCENTAGE}%
- **Test Count**: {NUMBER}
- **Duration**: {TIME}ms
- **Snapshots**: {NUMBER}

---

**Test Quality Score**: [X/10]
**Jest Version Compatibility**: [Compatible/Needs Update]
**Best Practices Applied**: [List key practices]
