# Testing Prompts Collection

This directory contains comprehensive testing prompts designed for generating high-quality tests across different testing domains. Each prompt is engineered to produce tests that follow F.I.R.S.T principles, AAA pattern, and industry best practices.

## 📁 Structure

```text
testing/
├── README.md                                   # This file
├── 01-unit-test-generation/                    # Generate unit tests from source code
│   └── prompt.md
├── 02-integration-test-generation/             # Create integration tests for APIs/services
│   └── prompt.md
├── 03-e2e-test-generation/                     # Build end-to-end test scenarios
│   └── prompt.md
├── 04-test-quality-assessment/                 # Evaluate test suite quality (F.I.R.S.T principles)
│   └── prompt.md
├── 05-coverage-gap-analysis/                   # Identify untested code paths and edge cases
│   └── prompt.md
├── 06-test-refactoring/                        # Improve test readability, maintainability, DRY
│   └── prompt.md
├── 07-mock-stub-strategy/                      # Design mocking approaches for dependencies
│   └── prompt.md
├── 08-test-data-factory/                       # Create test fixtures and data builders
│   └── prompt.md
├── 09-flaky-test-diagnosis/                    # Debug and fix unreliable tests
│   └── prompt.md
├── 10-performance-testing/                     # Load, stress, and benchmark testing
│   └── prompt.md
├── 11-security-testing/                        # Vulnerability scanning and penetration testing
│   └── prompt.md
├── 12-accessibility-testing/                   # WCAG compliance and a11y testing
│   └── prompt.md
└── 13-language-stack-specific/                 # Framework-specific testing patterns
    ├── README.md
    ├── jest-testing.md                         # Jest (JavaScript/TypeScript)
    ├── react-testing-library.md                # React Testing Library
    ├── pytest-testing.md                       # pytest (Python)
    ├── cypress-testing.md                      # Cypress (E2E)
    └── [Additional framework prompts]
```

## 🚀 Quick Start

1. **Identify your testing need**: Choose from unit, integration, E2E, or specialized testing
2. **Select the appropriate prompt**: Navigate to the relevant category
3. **Customize the context**: Fill in placeholders with your project details
4. **Generate tests**: Use the prompt with GPT-5 or Claude 4.5
5. **Review and integrate**: Adjust generated tests to fit your codebase

## 📋 Prompt Categories

### General Testing Prompts

#### Test Generation
- **[01-unit-test-generation](./01-unit-test-generation/prompt.md)** - Generate comprehensive unit tests with edge cases and error handling
- **[02-integration-test-generation](./02-integration-test-generation/prompt.md)** - Create integration tests for APIs, databases, and service interactions
- **[03-e2e-test-generation](./03-e2e-test-generation/prompt.md)** - Build complete user workflow tests with Page Object Model

#### Test Quality & Maintenance
- **[04-test-quality-assessment](./04-test-quality-assessment/prompt.md)** - Evaluate test suite against F.I.R.S.T principles and best practices
- **[05-coverage-gap-analysis](./05-coverage-gap-analysis/prompt.md)** - Identify untested code paths, edge cases, and coverage gaps
- **[06-test-refactoring](./06-test-refactoring/prompt.md)** - Improve test code readability, reduce duplication, apply DRY

#### Test Infrastructure
- **[07-mock-stub-strategy](./07-mock-stub-strategy/prompt.md)** - Design effective mocking strategies and test doubles
- **[08-test-data-factory](./08-test-data-factory/prompt.md)** - Create test data builders, fixtures, and object mothers
- **[09-flaky-test-diagnosis](./09-flaky-test-diagnosis/prompt.md)** - Debug and fix unreliable tests with timing, isolation, or state issues

#### Specialized Testing
- **[10-performance-testing](./10-performance-testing/prompt.md)** - Load, stress, spike, and endurance testing strategies
- **[11-security-testing](./11-security-testing/prompt.md)** - OWASP Top 10, vulnerability scanning, and penetration testing
- **[12-accessibility-testing](./12-accessibility-testing/prompt.md)** - WCAG 2.1/2.2 compliance, a11y testing, and screen reader validation

### Framework-Specific Testing

See **[13-language-stack-specific](./13-language-stack-specific/README.md)** for detailed framework prompts:

- **JavaScript/TypeScript**: Jest, Vitest, Mocha
- **React**: React Testing Library
- **Python**: pytest, unittest
- **E2E**: Cypress, Playwright
- **Backend**: NestJS, Express + Supertest
- **API**: REST, GraphQL testing

## 🎯 Testing Prompt Quality Criteria

All prompts in this collection incorporate:

### F.I.R.S.T Principles
- **Fast**: Tests execute quickly
- **Independent**: No dependencies between tests
- **Repeatable**: Consistent results in any environment
- **Self-validating**: Clear pass/fail without manual inspection
- **Timely**: Written alongside or before production code

### AAA Pattern
- **Arrange**: Set up test data and dependencies
- **Act**: Execute the code under test
- **Assert**: Verify expected outcomes

### Test Coverage
- Edge cases and boundary conditions
- Error scenarios and exception handling
- Integration points with dependencies
- State transitions and workflows
- Performance and security concerns

### Best Practices
- Clear, descriptive test names
- Proper test isolation
- Effective mocking strategies
- Realistic test data
- Maintainable test code (DRY principle)
- Framework-specific patterns and utilities

## 🎓 Usage Patterns

### Test Generation Workflow

```
1. Write/Modify Code
   ↓
2. Select Test Prompt
   ↓
3. Customize Context
   ↓
4. Generate Tests
   ↓
5. Review & Refine
   ↓
6. Run Tests
   ↓
7. Iterate
```

### Test Maintenance Workflow

```
1. Identify Issues
   (flaky, slow, hard to maintain)
   ↓
2. Use Quality Assessment Prompt
   ↓
3. Apply Refactoring Prompt
   ↓
4. Fix Identified Issues
   ↓
5. Verify Improvements
```

### Coverage Improvement Workflow

```
1. Run Coverage Analysis
   ↓
2. Use Coverage Gap Analysis Prompt
   ↓
3. Identify Critical Gaps
   ↓
4. Generate Missing Tests
   ↓
5. Verify Coverage Goals Met
```

## 📊 When to Use Which Prompt

| Scenario | Prompt to Use |
|----------|---------------|
| New feature needs tests | 01-unit-test-generation |
| API integration needs testing | 02-integration-test-generation |
| User workflow needs validation | 03-e2e-test-generation |
| Test suite feels brittle | 04-test-quality-assessment |
| Coverage is low | 05-coverage-gap-analysis |
| Tests are hard to maintain | 06-test-refactoring |
| Need mocking strategy | 07-mock-stub-strategy |
| Test data is messy | 08-test-data-factory |
| Tests fail randomly | 09-flaky-test-diagnosis |
| Need load testing | 10-performance-testing |
| Security audit needed | 11-security-testing |
| Need a11y compliance | 12-accessibility-testing |
| Framework-specific help | 13-language-stack-specific |

## 🔧 Customization Tips

### Placeholder Patterns

Most prompts use these common placeholders:

```
{LANGUAGE} - Programming language (JavaScript, Python, etc.)
{FRAMEWORK} - Framework name (React, NestJS, etc.)
{TEST_FRAMEWORK} - Testing framework (Jest, pytest, etc.)
{SOURCE_CODE} - Actual code to test
{COMPONENT_NAME} - Name of component/module
{FILE_PATH} - Path to source file
```

### Context Optimization

For best results, provide:

1. **Clear requirements**: What behavior should be tested
2. **Edge cases**: Known boundary conditions
3. **Error scenarios**: Expected failure modes
4. **Dependencies**: External systems or services
5. **Constraints**: Performance, security requirements

## 🤝 Contributing

To add new testing prompts:

1. Follow the established structure
2. Include F.I.R.S.T principles
3. Provide comprehensive examples
4. Document framework-specific patterns
5. Test with real scenarios
6. Update this README

## 📖 Additional Resources

### Testing Fundamentals
- [F.I.R.S.T Principles](https://github.com/ghsukumar/SFDC_Best_Practices/wiki/F.I.R.S.T-Principles-of-Unit-Testing)
- [AAA Pattern](https://medium.com/@pjbgf/title-testing-code-ocd-and-the-aaa-pattern-df453975ab80)
- [Test Pyramid](https://martinfowler.com/articles/practical-test-pyramid.html)

### Framework Documentation
- [Jest](https://jestjs.io/) - JavaScript testing
- [React Testing Library](https://testing-library.com/react) - React components
- [pytest](https://docs.pytest.org/) - Python testing
- [Cypress](https://www.cypress.io/) - E2E testing
- [Playwright](https://playwright.dev/) - Cross-browser E2E

### Best Practices
- [Google Testing Blog](https://testing.googleblog.com/)
- [Martin Fowler on Testing](https://martinfowler.com/testing/)
- [Test Automation Patterns](http://xunitpatterns.com/)

---

## 📝 Notes

- These prompts are optimized for **GPT-5** and **Claude 4.5**
- All prompts produce **production-ready test code**
- Tests follow **industry best practices** and **framework conventions**
- Prompts can be **customized** for specific project needs
- Regular updates based on **framework evolution** and **testing trends**

---

**Maintained by**: [Repository Contributors]
**Last Updated**: 2025-10
**Version**: 1.0.0
