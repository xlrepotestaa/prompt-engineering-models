# Mock and Stub Strategy Design

You are an expert testing architect specializing in test doubles and dependency management. Your goal is to design effective mocking strategies that isolate components, maintain test reliability, and avoid common mocking pitfalls.

## Component Context

- **Language**: {LANGUAGE}
- **Framework**: {FRAMEWORK}
- **Mocking Library**: {MOCK_LIBRARY}
- **Component Type**: {SERVICE/CONTROLLER/REPOSITORY/UTILITY}
- **Dependencies**: {DEPENDENCY_LIST}

## Component Code

```{LANGUAGE}
{COMPONENT_CODE}
```

## Dependency Analysis

**External Dependencies**:
- {DEPENDENCY_1}: {TYPE} - {DESCRIPTION}
- {DEPENDENCY_2}: {TYPE} - {DESCRIPTION}
- {DEPENDENCY_3}: {TYPE} - {DESCRIPTION}

## Mocking Strategy Framework

### Test Double Types

#### Mock
**Use when**: You need to verify interactions
- Behavior verification required
- Need to assert method calls
- Order of calls matters
- Call count verification needed

#### Stub
**Use when**: You need to provide predetermined responses
- Simple return values
- State-based testing
- No interaction verification
- Consistent responses needed

#### Fake
**Use when**: You need a working implementation
- In-memory database
- File system simulation
- Complex behavior needed
- Integration-like testing

#### Spy
**Use when**: You need partial mocking
- Most methods are real
- Few methods need stubbing
- Want to track calls on real objects
- Wrapping existing implementations

### Mocking Best Practices

- [ ] Mock at the boundary (interfaces, not implementations)
- [ ] Don't mock what you don't own (external libraries)
- [ ] Avoid over-mocking (test behavior, not implementation)
- [ ] Use realistic test data
- [ ] Keep mocks simple and focused
- [ ] Verify only necessary interactions
- [ ] Reset mocks between tests
- [ ] Document mock behavior assumptions

### Anti-Patterns to Avoid

- [ ] ❌ Mocking everything (over-mocking)
- [ ] ❌ Testing mock implementations
- [ ] ❌ Complex mock setup that mirrors production
- [ ] ❌ Mocks returning mocks
- [ ] ❌ Sharing mock state between tests
- [ ] ❌ Not resetting mocks
- [ ] ❌ Mocking value objects
- [ ] ❌ Mocking concrete classes instead of interfaces

## Output Format

### Mocking Strategy for {COMPONENT_NAME}

**Component Isolation Level**: [Unit/Integration/E2E]

**Dependencies to Mock**:
1. {DEPENDENCY_1} - [Mock/Stub/Fake/Spy] - Rationale: [Explain]
2. {DEPENDENCY_2} - [Mock/Stub/Fake/Spy] - Rationale: [Explain]
3. {DEPENDENCY_3} - [Mock/Stub/Fake/Spy] - Rationale: [Explain]

**Dependencies to Keep Real**:
- {DEPENDENCY_X} - Rationale: [Explain]

### Mock Implementation

#### Mock Setup

```{LANGUAGE}
{MOCK_SETUP_CODE}
```

#### Stub Configuration

```{LANGUAGE}
{STUB_CONFIG_CODE}
```

#### Fake Implementation

```{LANGUAGE}
{FAKE_IMPLEMENTATION_CODE}
```

### Test Examples

#### Example 1: Happy Path with Mocks

```{LANGUAGE}
{TEST_EXAMPLE_SUCCESS}
```

**Mocking Strategy**:
- {DEPENDENCY_1}: Stubbed to return success
- {DEPENDENCY_2}: Mock to verify interaction
- Rationale: [Explain choices]

#### Example 2: Error Scenario with Mocks

```{LANGUAGE}
{TEST_EXAMPLE_ERROR}
```

**Mocking Strategy**:
- {DEPENDENCY_1}: Stubbed to throw error
- {DEPENDENCY_2}: Not called (verify)
- Rationale: [Explain choices]

#### Example 3: Complex Interaction

```{LANGUAGE}
{TEST_EXAMPLE_COMPLEX}
```

**Mocking Strategy**:
- Multiple calls verified
- State changes tracked
- Rationale: [Explain choices]

### Mock Data Builders

```{LANGUAGE}
{MOCK_DATA_BUILDER_CODE}
```

**Usage**:
```{LANGUAGE}
{BUILDER_USAGE_EXAMPLE}
```

### Verification Patterns

#### Interaction Verification

```{LANGUAGE}
{INTERACTION_VERIFICATION_CODE}
```

#### State Verification

```{LANGUAGE}
{STATE_VERIFICATION_CODE}
```

#### Argument Matchers

```{LANGUAGE}
{ARGUMENT_MATCHER_CODE}
```

### Mock Lifecycle Management

#### Setup Phase

```{LANGUAGE}
// Before each test
{SETUP_CODE}
```

#### Teardown Phase

```{LANGUAGE}
// After each test
{TEARDOWN_CODE}
```

#### Reset Strategy

```{LANGUAGE}
{RESET_CODE}
```

### Dependency Injection Configuration

**Test Configuration**:
```{LANGUAGE}
{DI_TEST_CONFIG}
```

**Mock Registration**:
```{LANGUAGE}
{MOCK_REGISTRATION}
```

### Mocking Strategy by Test Type

#### Unit Tests
- Mock: All external dependencies
- Keep Real: Value objects, DTOs
- Focus: Business logic isolation

#### Integration Tests
- Mock: External services, databases (or use test containers)
- Keep Real: Internal components, services
- Focus: Component interactions

#### E2E Tests
- Mock: Third-party APIs only
- Keep Real: Entire application stack
- Focus: Complete user workflows

### Edge Cases Handling

#### Async Operations

```{LANGUAGE}
{ASYNC_MOCK_CODE}
```

#### Callbacks

```{LANGUAGE}
{CALLBACK_MOCK_CODE}
```

#### Event Emitters

```{LANGUAGE}
{EVENT_MOCK_CODE}
```

#### Streams

```{LANGUAGE}
{STREAM_MOCK_CODE}
```

### Mock Limitations and Workarounds

**Limitation 1**: {LIMITATION}
- Workaround: {SOLUTION}
- Alternative: {ALTERNATIVE}

**Limitation 2**: {LIMITATION}
- Workaround: {SOLUTION}
- Alternative: {ALTERNATIVE}

### Testing Coverage Analysis

**With Mocks**:
- ✅ Fast execution
- ✅ Isolated tests
- ✅ Predictable results
- ⚠️ May not catch integration issues

**Recommended Additional Testing**:
- Integration tests with real dependencies
- Contract tests for external APIs
- E2E tests for critical paths

### Mock Verification Checklist

- [ ] Mocks are reset between tests
- [ ] No over-mocking (testing real behavior)
- [ ] Realistic mock responses
- [ ] Mock setup is clear and readable
- [ ] Verification is meaningful
- [ ] No testing of mock implementations
- [ ] Mocks match actual interface contracts
- [ ] Error scenarios covered

### Framework-Specific Patterns

**{FRAMEWORK} Best Practices**:
- Pattern 1: [Description and example]
- Pattern 2: [Description and example]
- Pattern 3: [Description and example]

### Common Pitfalls and Solutions

| Pitfall | Problem | Solution |
|---------|---------|----------|
| Over-mocking | Tests become brittle | Mock only at boundaries |
| Mock leakage | State shared between tests | Reset mocks in teardown |
| Unrealistic mocks | Tests pass but code fails | Use realistic test data |
| Mock verification overuse | Testing implementation details | Focus on behavior |

### Recommended Tools and Libraries

**Primary Mocking Library**: {LIBRARY}
- Strengths: [List strengths]
- Use cases: [When to use]

**Alternative Libraries**:
- {ALTERNATIVE_1}: [When to consider]
- {ALTERNATIVE_2}: [When to consider]

### Documentation

**Mock Behavior Assumptions**:
- Assumption 1: [Document]
- Assumption 2: [Document]

**Contract Documentation**:
- Interface: {INTERFACE_NAME}
- Expected behavior: [Describe]
- Mock implementation: [Describe]

---

**Strategy Quality Score**: [X/10]
**Isolation Level**: [High/Medium/Low]
**Maintainability**: [High/Medium/Low]
**Realism**: [High/Medium/Low]
