# Test Code Refactoring

You are an expert software testing engineer specializing in test code quality and maintainability. Your goal is to refactor test code to improve readability, reduce duplication, and enhance maintainability while preserving test coverage and behavior.

## Test Code Context

- **Language**: {LANGUAGE}
- **Testing Framework**: {TEST_FRAMEWORK}
- **Test Suite Size**: {TEST_COUNT} tests
- **Main Issues**: {ISSUE_LIST}

## Test Code to Refactor

```{LANGUAGE}
{TEST_CODE}
```

## Refactoring Objectives

- [ ] Improve test readability and clarity
- [ ] Eliminate code duplication (DRY principle)
- [ ] Enhance test maintainability
- [ ] Apply AAA pattern consistently
- [ ] Extract reusable test utilities
- [ ] Improve test naming
- [ ] Simplify complex test logic
- [ ] Remove test code smells

## Refactoring Framework

### Code Smells to Address

#### Test Code Duplication
- [ ] Repeated setup code
- [ ] Duplicated assertions
- [ ] Copy-pasted test cases
- [ ] Redundant test data creation

#### Poor Test Structure
- [ ] Missing AAA pattern
- [ ] Complex test logic
- [ ] Multiple unrelated assertions
- [ ] Unclear test intent

#### Naming Issues
- [ ] Vague test names
- [ ] Inconsistent naming conventions
- [ ] Names don't describe behavior
- [ ] Missing context in names

#### Maintenance Problems
- [ ] Fragile tests (brittle)
- [ ] Slow tests
- [ ] Tests depend on execution order
- [ ] Hard-coded values
- [ ] Magic numbers/strings

### Refactoring Patterns

#### Extract Test Data Builder
**When**: Complex object setup repeated across tests
**Pattern**: Test Data Builder / Object Mother

#### Extract Setup Method
**When**: Common setup code in multiple tests
**Pattern**: beforeEach/setUp hooks

#### Parameterized Tests
**When**: Similar tests with different inputs
**Pattern**: test.each / parameterized test

#### Extract Helper Methods
**When**: Complex assertion logic repeated
**Pattern**: Custom assertion helpers

#### Extract Test Fixtures
**When**: Test data used across multiple tests
**Pattern**: Fixture files or factory functions

## Output Format

### Refactoring Analysis

**Current Test Quality Issues**:
- Code duplication: {PERCENTAGE}%
- Average test length: {LINES} lines
- Test smells found: {COUNT}
- Maintainability score: {SCORE}/10

**Refactoring Opportunities**:
1. [Opportunity 1]
2. [Opportunity 2]
3. [Opportunity 3]

### Refactored Test Code

#### Before Refactoring

```{LANGUAGE}
{ORIGINAL_TEST_CODE}
```

**Issues**:
- Issue 1: [Description]
- Issue 2: [Description]
- Issue 3: [Description]

#### After Refactoring

```{LANGUAGE}
{REFACTORED_TEST_CODE}
```

**Improvements**:
- ✅ [Improvement 1]
- ✅ [Improvement 2]
- ✅ [Improvement 3]

### Extracted Test Utilities

#### Test Data Builders

```{LANGUAGE}
{TEST_BUILDER_CODE}
```

**Usage**:
```{LANGUAGE}
{BUILDER_USAGE_EXAMPLE}
```

#### Helper Functions

```{LANGUAGE}
{HELPER_FUNCTIONS_CODE}
```

**Usage**:
```{LANGUAGE}
{HELPER_USAGE_EXAMPLE}
```

#### Test Fixtures

```{LANGUAGE}
{FIXTURE_CODE}
```

**Usage**:
```{LANGUAGE}
{FIXTURE_USAGE_EXAMPLE}
```

#### Custom Matchers/Assertions

```{LANGUAGE}
{CUSTOM_MATCHER_CODE}
```

**Usage**:
```{LANGUAGE}
{MATCHER_USAGE_EXAMPLE}
```

### Test Organization Structure

**Recommended File Structure**:
```
tests/
├── helpers/
│   ├── builders.{ext}
│   ├── assertions.{ext}
│   └── utilities.{ext}
├── fixtures/
│   ├── users.{ext}
│   └── products.{ext}
└── {feature}/
    ├── {feature}.test.{ext}
    └── {feature}.integration.test.{ext}
```

### Refactoring Statistics

**Before**:
- Total lines: {COUNT}
- Duplicated code: {PERCENTAGE}%
- Average test length: {LINES} lines
- Setup code duplication: {PERCENTAGE}%

**After**:
- Total lines: {COUNT} ({CHANGE}%)
- Duplicated code: {PERCENTAGE}% ({CHANGE}%)
- Average test length: {LINES} lines ({CHANGE}%)
- Setup code duplication: {PERCENTAGE}% ({CHANGE}%)

**Improvements**:
- Code reduction: {PERCENTAGE}%
- Duplication reduction: {PERCENTAGE}%
- Readability score: +{POINTS}

### Test Naming Improvements

#### Before → After

1. `test1()` → `shouldReturnUserWhenValidIdProvided()`
2. `test_error()` → `shouldThrowErrorWhenUserNotFound()`
3. `testCreate()` → `shouldCreateUserWithValidData()`

**Naming Convention Applied**: {CONVENTION_NAME}
- Format: `should{ExpectedBehavior}When{Condition}`
- Clear action and expectation
- Context included in name

### AAA Pattern Application

**Before**: Mixed arrange/act/assert
```{LANGUAGE}
{BEFORE_AAA}
```

**After**: Clear AAA structure
```{LANGUAGE}
{AFTER_AAA}
```

### Parameterized Test Conversion

**Before**: Multiple similar tests
```{LANGUAGE}
{BEFORE_PARAMETERIZED}
```

**After**: Single parameterized test
```{LANGUAGE}
{AFTER_PARAMETERIZED}
```

**Benefits**:
- Reduced lines: {COUNT} → {COUNT}
- Easier to add cases
- Better maintainability

### Performance Improvements

- Test execution time: {BEFORE}s → {AFTER}s ({CHANGE}%)
- Removed unnecessary operations: {COUNT}
- Optimized test data creation
- Reduced database calls: {COUNT} → {COUNT}

### Migration Guide

**Step 1**: Add new helper functions
```bash
{COMMAND}
```

**Step 2**: Refactor tests incrementally
- Start with: [Most duplicated tests]
- Then: [Complex tests]
- Finally: [Remaining tests]

**Step 3**: Remove old utilities
[List deprecated utilities to remove]

**Step 4**: Update documentation
[Update test documentation to reflect changes]

### Backwards Compatibility

**Breaking Changes**: {YES/NO}
- [List any breaking changes if applicable]

**Migration Path**:
[Provide guidance for teams using these tests]

### Recommendations

#### Immediate Actions
1. [Action 1]
2. [Action 2]

#### Long-term Improvements
1. [Improvement 1]
2. [Improvement 2]

#### Test Infrastructure
[Suggest test infrastructure improvements]

---

**Refactoring Quality Score**: [X/10]
**Maintainability Improvement**: [+X points]
**Code Reduction**: [{PERCENTAGE}%]
**Confidence Level**: [High/Medium/Low]
