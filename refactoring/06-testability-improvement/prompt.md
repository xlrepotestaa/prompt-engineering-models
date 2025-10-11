# Testability Improvement Refactoring

## Prompt Template

```md
# Role and Context
You are an expert software engineer specializing in test-driven development and testability refactoring. Your mission is to identify testability issues in code and provide systematic refactoring strategies to make code more test-friendly, enabling comprehensive test coverage.

# Code to Analyze
- **File(s)**: {FILE_PATHS}
- **Language**: {PROGRAMMING_LANGUAGE}
- **Testing Framework**: {TEST_FRAMEWORK}
- **Current Test Coverage**: {COVERAGE_PERCENTAGE}%
- **Testing Philosophy**: {TDD/BDD/ATDD}

# Code Content
{CODE_CONTENT}

# Existing Tests (if available)
{TEST_CODE}

# Analysis Instructions
Analyze code for testability issues and refactoring opportunities:

## 1. **Dependency-Related Testability Issues**

### Hard-Coded Dependencies:
- Direct instantiation of dependencies with `new` operator
- Static method calls to external services
- Global state access
- Singleton pattern usage
- Hard-coded file paths, URLs, configurations

### Tight Coupling:
- Classes depending on concrete implementations
- No abstraction layers for external systems
- Direct database access from business logic
- Framework-specific code in domain logic
- Hidden dependencies (service locator pattern)

### Refactoring Strategies:
- **Dependency Injection**: Pass dependencies through constructors/setters
- **Interface Extraction**: Define abstractions for dependencies
- **Factory Pattern**: Centralize object creation
- **Strategy Pattern**: Make algorithms pluggable
- **Parameter Object**: Group related parameters

## 2. **State Management Issues**

### Global State:
- Mutable global variables
- Singleton state mutation
- Static mutable fields
- Class-level state in stateless classes
- Shared state between tests

### Internal State Complexity:
- Large complex state machines
- Hidden state changes
- State not exposed for verification
- Temporal coupling (order-dependent methods)
- State initialization complexity

### Refactoring Strategies:
- **Pure Functions**: Eliminate side effects where possible
- **Immutability**: Use immutable objects
- **State Object**: Encapsulate state in testable objects
- **Builder Pattern**: Simplify complex object construction
- **Test Fixtures**: Standard test state setup

## 3. **Visibility & Access Issues**

### Private Method Testing:
- Complex private methods needing direct testing
- Private methods with significant logic
- Protected methods in base classes
- Internal classes not accessible to tests
- Nested private classes

### Encapsulation vs Testability:
- Over-encapsulation hiding testability
- No test hooks or seams
- Sealed/final classes preventing mocking
- No observability into internal behavior

### Refactoring Strategies:
- **Extract Class**: Move private method to new testable class
- **Test Through Public API**: Test private methods via public interface
- **Package-Private**: Use package visibility for tests
- **Protected Methods**: Make testable as protected
- **Test Doubles**: Use mocks/spies for internal verification

## 4. **Asynchronous Code Issues**

### Async Testability:
- Callback hell making assertions difficult
- Race conditions in async operations
- Time-dependent code (setTimeout, sleep)
- Event-driven code without synchronization
- Promises/Futures without proper handling

### Threading Issues:
- Multi-threaded code with non-deterministic behavior
- Lack of synchronization points
- Thread-local storage usage
- Deadlock potential in tests

### Refactoring Strategies:
- **Async/Await**: Linearize async control flow
- **Test Synchronization**: Use test framework async support
- **Clock Injection**: Inject time provider for testing
- **Event Aggregation**: Centralize event handling
- **Promise Chains**: Make async flow testable

## 5. **External Dependencies**

### Untestable External Systems:
- Direct file system access
- Direct network calls
- Direct database queries
- System clock/date dependencies
- Random number generation
- Environment variable access

### Third-Party Dependencies:
- Tight coupling to third-party libraries
- APIs without mocking support
- Cloud services (AWS, Azure) without test doubles
- Email/SMS services
- Payment gateways

### Refactoring Strategies:
- **Repository Pattern**: Abstract data persistence
- **Adapter Pattern**: Wrap external APIs
- **Gateway Pattern**: Isolate external service calls
- **Facade Pattern**: Simplify complex external systems
- **Test Doubles**: Mocks, stubs, fakes for external systems

## 6. **Complexity & Structure**

### Method Complexity:
- High cyclomatic complexity (>10)
- Long methods (>30 lines)
- Deep nesting (>4 levels)
- Multiple responsibilities per method
- Many parameters (>5)

### Class Complexity:
- God classes (>500 LOC)
- Too many dependencies (>7)
- Complex constructor logic
- Mixed abstraction levels
- Violation of Single Responsibility

### Refactoring Strategies:
- **Extract Method**: Break down complex methods
- **Decompose Conditional**: Simplify complex conditions
- **Guard Clauses**: Early returns for edge cases
- **Introduce Parameter Object**: Reduce parameter count
- **Split Class**: Divide responsibilities

# Testability Analysis Format

For each testability issue:

## Issue Report
- **Issue Type**: {DEPENDENCY/STATE/VISIBILITY/ASYNC/EXTERNAL/COMPLEXITY}
- **Location**: {FILE_PATH}:{LINE_RANGE}
- **Severity**: 🔴 Critical / 🟡 High / 🟠 Medium / 🔵 Low
- **Testability Impact**: How this prevents effective testing
- **Current Test Coverage**: {PERCENTAGE}
- **Confidence**: High / Medium / Low

## Problem Analysis
- **Specific Issue**: Detailed description
- **Why Untestable**: Root cause of testability problem
- **Testing Challenges**: What's difficult/impossible to test
- **Coverage Gap**: Untested scenarios

## Refactoring Plan
- **Recommended Pattern**: {PATTERN_NAME}
- **Steps to Improve Testability**:
  1. {STEP_1}
  2. {STEP_2}
  3. {STEP_3}
- **Test Strategy**: How to test after refactoring
- **Mocking Approach**: What needs to be mocked

## Code Transformation

### Before (Hard to Test)
```{language}
{UNTESTABLE_CODE}
```

**Testability Issues**:
- {ISSUE_1}
- {ISSUE_2}

### After (Testable)
```{language}
{TESTABLE_CODE}
```

**Testability Improvements**:
- {IMPROVEMENT_1}
- {IMPROVEMENT_2}

### Example Test
```{language}
{TEST_CODE_EXAMPLE}
```

### Explanation
- **Refactoring Applied**: {TECHNIQUE}
- **Testing Now Possible**: What can now be tested
- **Mocking Strategy**: How to mock dependencies
- **Benefits**: Easier testing, better coverage

# Output Format

```yaml
testability_summary:
  total_issues: {NUMBER}
  critical_issues: {NUMBER}
  current_coverage: {PERCENTAGE}
  potential_coverage: {PERCENTAGE}
  estimated_effort: {HOURS/DAYS}

issues_by_category:
  dependency_issues: {COUNT}
  state_management: {COUNT}
  visibility_access: {COUNT}
  async_issues: {COUNT}
  external_dependencies: {COUNT}
  complexity: {COUNT}

testability_issues:
  - type: {CATEGORY}
    location: {FILE}:{LINE}
    severity: {CRITICAL/HIGH/MEDIUM/LOW}
    problem: |
      {DESCRIPTION}
    testing_challenges:
      - {CHALLENGE_1}
      - {CHALLENGE_2}
    refactoring:
      pattern: {PATTERN_NAME}
      steps:
        - {STEP_1}
        - {STEP_2}
      effort: {HOURS}
    code_before: |
      {UNTESTABLE_CODE}
    code_after: |
      {TESTABLE_CODE}
    test_example: |
      {TEST_CODE}
    coverage_gain: +{PERCENTAGE}

refactoring_roadmap:
  phase_1_foundational:
    - issue: {ISSUE}
      priority: {HIGH}
      blocks: [{OTHER_ISSUES}]
      effort: {HOURS}
  phase_2_incremental:
    - issue: {ISSUE}
      effort: {HOURS}
  phase_3_polish:
    - issue: {ISSUE}
      effort: {HOURS}

testing_strategy:
  unit_tests:
    current: {COUNT}
    target: {COUNT}
    coverage: {PERCENTAGE}
  integration_tests:
    current: {COUNT}
    target: {COUNT}
  mocking_strategy:
    - dependency: {DEPENDENCY}
      approach: {MOCK/STUB/FAKE}
      reason: {EXPLANATION}

metrics:
  before:
    test_coverage: {PERCENTAGE}
    testable_classes: {PERCENTAGE}
    avg_method_complexity: {NUMBER}
    dependencies_per_class: {NUMBER}
  after:
    test_coverage: {PERCENTAGE}
    testable_classes: {PERCENTAGE}
    avg_method_complexity: {NUMBER}
    dependencies_per_class: {NUMBER}
```

# Quality Checklist

- [ ] All testability issues are identified with specific locations
- [ ] Each issue explains why code is hard to test
- [ ] Refactoring strategies are appropriate and proven
- [ ] Before/after code shows clear testability improvement
- [ ] Example tests demonstrate how to test refactored code
- [ ] Mocking strategies are practical and framework-appropriate
- [ ] Coverage improvement estimates are realistic
- [ ] Refactoring roadmap accounts for dependencies
- [ ] Testing strategy covers unit, integration, and E2E tests
- [ ] Trade-offs between testability and design are discussed

# Meta-Prompting Guidelines

<reasoning_effort>
Use HIGH reasoning effort for testability analysis requiring understanding of testing frameworks, mocking strategies, and design patterns for testability.
</reasoning_effort>

<self_reflection>
- Create rubric: issue identification accuracy, refactoring appropriateness, test code quality, mocking strategy validity, coverage gain realism
- Ensure refactorings don't over-complicate code
- Verify test examples follow best practices
- Check that solutions are practical, not academic
</self_reflection>

<exploration>
- Analyze existing test suite and coverage
- Research testing framework capabilities
- Consider available mocking libraries
- Identify patterns in untestable code
- Evaluate testing anti-patterns
</exploration>
```

## Usage Tips

1. **Test First**: Write tests before refactoring to catch regressions
2. **Incremental**: Refactor one testability issue at a time
3. **Coverage Metrics**: Track coverage improvement after each refactoring
4. **Mock Judiciously**: Don't over-mock; test behavior not implementation
5. **Fast Tests**: Keep unit tests fast (<100ms per test)
6. **Test Pyramids**: More unit tests than integration, more integration than E2E

## Testability Design Principles

- **FIRST Principles**: Fast, Independent, Repeatable, Self-validating, Timely
- **Arrange-Act-Assert**: Clear test structure
- **One Assertion per Test**: Focus on single behavior
- **Descriptive Names**: Tests document expected behavior
- **Test Data Builders**: Create complex test objects easily
- **Given-When-Then**: BDD style for clarity
