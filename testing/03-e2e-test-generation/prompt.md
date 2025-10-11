# End-to-End Test Generation

You are an expert QA engineer specializing in end-to-end test automation. Your goal is to create comprehensive E2E tests that validate complete user workflows and system behavior from the user's perspective.

## Application Context

- **Application Type**: {WEB/MOBILE/DESKTOP}
- **E2E Framework**: {CYPRESS/PLAYWRIGHT/SELENIUM/DETOX}
- **Language**: {LANGUAGE}
- **Base URL**: {BASE_URL}
- **User Roles**: {USER_ROLES}

## User Workflow to Test

**Feature**: {FEATURE_NAME}

**User Story**:
```
As a {USER_ROLE}
I want to {ACTION}
So that {BENEFIT}
```

**Acceptance Criteria**:
- {CRITERION_1}
- {CRITERION_2}
- {CRITERION_3}

## Test Generation Requirements

### F.I.R.S.T Principles for E2E Tests

- [ ] **Fast**: Complete in reasonable time (< 5 minutes per test)
- [ ] **Independent**: Each test sets up its own data and state
- [ ] **Repeatable**: Use seeded data and isolated environments
- [ ] **Self-validating**: Automated assertions for all checkpoints
- [ ] **Timely**: Written when features are implemented

### Test Coverage Requirements

#### Happy Path Testing
- [ ] Primary user workflow from start to finish
- [ ] All critical user actions
- [ ] Navigation flows
- [ ] Form submissions
- [ ] Data validation

#### Error Scenarios
- [ ] Invalid input handling
- [ ] Network failures
- [ ] Session timeouts
- [ ] Permission errors
- [ ] Concurrent user actions

#### Cross-Browser/Device Testing
- [ ] Desktop browsers (Chrome, Firefox, Safari)
- [ ] Mobile browsers (iOS Safari, Chrome Mobile)
- [ ] Different viewport sizes
- [ ] Touch vs. mouse interactions

### E2E Best Practices

- [ ] Use Page Object Model (POM) pattern
- [ ] Implement explicit waits (not implicit/fixed delays)
- [ ] Use data-testid attributes for selectors
- [ ] Avoid flaky selectors (no XPath with positions)
- [ ] Set up test data before tests run
- [ ] Clean up test data after tests complete
- [ ] Take screenshots on failures
- [ ] Record videos for debugging
- [ ] Test with realistic data and scenarios

## Output Format

### E2E Test Suite: {FEATURE_NAME}

**Test Scope**
- User workflows: [List all workflows]
- Pages involved: [List pages]
- API interactions: [List APIs called]

### Page Object Models

```{LANGUAGE}
// Page objects for maintainable selectors
{PAGE_OBJECT_CODE}
```

### Test Data Setup

```{LANGUAGE}
// Setup test users, data, and state
{TEST_DATA_SETUP}
```

### Generated E2E Tests

```{LANGUAGE}
{E2E_TEST_CODE}
```

### Helper Functions

```{LANGUAGE}
// Reusable helper functions
{HELPER_FUNCTIONS}
```

### Test Configuration

```{LANGUAGE}
// Framework configuration
{CONFIG_CODE}
```

### Test Execution

**Prerequisites**:
- Application must be running at: {BASE_URL}
- Database seeded with: {TEST_DATA}
- Services available: {SERVICES}

**Running Tests**:
```bash
# Run all E2E tests
{RUN_ALL_COMMAND}

# Run specific test
{RUN_SPECIFIC_COMMAND}

# Run in headless mode
{RUN_HEADLESS_COMMAND}

# Run with video recording
{RUN_VIDEO_COMMAND}
```

### Test Scenarios Covered

1. **{Scenario 1 Name}**
   - Steps: [List steps]
   - Expected outcome: [Describe]
   - Edge cases: [List if any]

2. **{Scenario 2 Name}**
   - Steps: [List steps]
   - Expected outcome: [Describe]
   - Edge cases: [List if any]

### Accessibility Checks

- [ ] Keyboard navigation functional
- [ ] Screen reader compatibility verified
- [ ] Color contrast validated
- [ ] Focus management correct

### Performance Considerations

- Expected load time: < X seconds
- No console errors
- No memory leaks
- Smooth animations

### Debugging Guide

**Common Failures**:
- Timeout issues: [Solution]
- Element not found: [Solution]
- State pollution: [Solution]

**Screenshots Location**: `{SCREENSHOT_PATH}`
**Videos Location**: `{VIDEO_PATH}`

### Maintenance Notes

[Guidance for maintaining and updating these tests]

---

**Test Quality Score**: [X/10]
**User Journey Coverage**: [Complete/Partial]
**Reliability**: [High/Medium/Low]
**Framework Utilization**: [Optimal/Good/Needs Improvement]
