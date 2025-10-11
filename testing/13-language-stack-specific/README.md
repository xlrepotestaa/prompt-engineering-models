# Language and Framework-Specific Testing Prompts

This directory contains specialized testing prompts tailored to specific programming languages, frameworks, and testing tools. Each prompt incorporates framework-specific best practices, testing patterns, and utilities.

## 📁 Structure

### JavaScript/TypeScript Testing

- **jest-testing.md** - Jest unit and integration testing
- **vitest-testing.md** - Vitest modern testing framework
- **mocha-testing.md** - Mocha flexible testing framework
- **react-testing-library.md** - React component testing
- **cypress-testing.md** - Cypress E2E testing
- **playwright-testing.md** - Playwright E2E testing

### Python Testing

- **pytest-testing.md** - pytest unit and integration testing
- **unittest-testing.md** - Python unittest framework
- **python-integration-testing.md** - Python integration testing patterns

### Backend Framework Testing

- **nestjs-testing.md** - NestJS testing with dependency injection
- **express-supertest-testing.md** - Express API testing with Supertest
- **fastapi-testing.md** - FastAPI testing with TestClient

### Mobile Testing

- **react-native-testing.md** - React Native testing patterns
- **detox-testing.md** - Detox E2E mobile testing

### API Testing

- **rest-api-testing.md** - REST API testing strategies
- **graphql-testing.md** - GraphQL API testing

## 🎯 Framework-Specific Testing Patterns

Each prompt includes:

- **Framework Setup**: Configuration and dependencies
- **Test Structure**: Best practices for organizing tests
- **Mocking Patterns**: Framework-specific mocking utilities
- **Assertions**: Framework-specific matchers and assertions
- **Lifecycle Hooks**: Setup/teardown patterns
- **Best Practices**: Framework-recommended testing patterns
- **Common Pitfalls**: Framework-specific issues to avoid
- **CI/CD Integration**: Running tests in pipelines

## 🚀 Usage

1. **Select Framework**: Choose the prompt matching your tech stack
2. **Customize Context**: Fill in the placeholders with your project details
3. **Generate Tests**: Use the prompt with GPT-5 or Claude 4.5
4. **Review and Adapt**: Adjust generated tests to your needs
5. **Integrate**: Add tests to your CI/CD pipeline

## 📚 Testing Patterns by Framework

### Jest/Vitest
- Snapshot testing
- Mock functions and modules
- Test.each for parameterized tests
- Custom matchers
- Test coverage reporting

### React Testing Library
- User-centric testing
- Query priorities
- Async utilities (waitFor, findBy)
- User event simulation
- Accessibility testing

### Cypress/Playwright
- Page Object Model
- Custom commands
- Network stubbing/mocking
- Visual regression testing
- Cross-browser testing

### pytest
- Fixtures
- Parameterized tests
- Markers
- Plugins ecosystem
- Async testing

### NestJS
- Testing modules
- Dependency injection mocking
- E2E testing with supertest
- Guards and interceptors testing
- GraphQL resolver testing

## 🔧 Test Quality Criteria

All framework-specific prompts enforce:

- **F.I.R.S.T Principles**: Fast, Independent, Repeatable, Self-validating, Timely
- **AAA Pattern**: Arrange-Act-Assert
- **Test Coverage**: Edge cases and error scenarios
- **Best Practices**: Framework-specific patterns
- **Maintainability**: Readable and DRY tests

## 📖 Additional Resources

- [Jest Documentation](https://jestjs.io/)
- [Vitest Documentation](https://vitest.dev/)
- [React Testing Library](https://testing-library.com/react)
- [Cypress Documentation](https://www.cypress.io/)
- [Playwright Documentation](https://playwright.dev/)
- [pytest Documentation](https://docs.pytest.org/)

---

**Note**: These prompts are designed for GPT-5 and Claude 4.5, leveraging their advanced understanding of framework-specific testing patterns.
