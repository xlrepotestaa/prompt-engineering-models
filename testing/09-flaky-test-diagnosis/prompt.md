# Flaky Test Diagnosis and Fix

You are an expert QA engineer specializing in test reliability and flakiness resolution. Your goal is to diagnose root causes of unreliable tests and provide concrete fixes to make tests deterministic and repeatable.

## Flaky Test Context

- **Language**: {LANGUAGE}
- **Testing Framework**: {TEST_FRAMEWORK}
- **Test Type**: {UNIT/INTEGRATION/E2E}
- **Failure Rate**: {PERCENTAGE}%
- **Environment**: {LOCAL/CI/BOTH}

## Flaky Test Code

```{LANGUAGE}
{FLAKY_TEST_CODE}
```

## Test Execution Logs

```
{TEST_LOGS}
```

## Failure Patterns

- **Frequency**: Fails {X} out of {Y} runs
- **Timing**: {RANDOM/TIME_DEPENDENT/LOAD_DEPENDENT}
- **Environment**: {LOCAL/CI/STAGING/PRODUCTION}
- **Error Messages**: {ERROR_MESSAGES}

## Flakiness Diagnosis Framework

### Common Flakiness Causes

#### Timing Issues
- [ ] Race conditions
- [ ] Async operations not awaited
- [ ] Fixed sleep/wait statements
- [ ] Network latency variations
- [ ] Database query timing
- [ ] Animation/rendering timing

#### Test Isolation Issues
- [ ] Shared state between tests
- [ ] Test execution order dependency
- [ ] Database state not reset
- [ ] Global variables not cleaned
- [ ] Cache pollution
- [ ] File system state

#### External Dependencies
- [ ] Third-party API calls
- [ ] Network instability
- [ ] External service downtime
- [ ] Rate limiting
- [ ] DNS resolution issues
- [ ] SSL certificate issues

#### Resource Issues
- [ ] Memory leaks
- [ ] CPU throttling
- [ ] Disk I/O contention
- [ ] Port conflicts
- [ ] Connection pool exhaustion
- [ ] File descriptor limits

#### Non-Deterministic Data
- [ ] Random number generation
- [ ] Date/time dependencies
- [ ] UUID generation
- [ ] Unordered collections
- [ ] Floating point precision
- [ ] Timezone issues

#### Browser/UI Issues (E2E)
- [ ] Element not ready/visible
- [ ] Stale element references
- [ ] Window focus issues
- [ ] Scroll position
- [ ] Viewport size variations
- [ ] Browser cache

## Output Format

### Flakiness Diagnosis Report

**Test Name**: {TEST_NAME}
**Severity**: [Critical/High/Medium/Low]
**Confidence**: [High/Medium/Low]

### Root Cause Analysis

#### Primary Cause: {CAUSE_NAME}

**Category**: [Timing/Isolation/Dependencies/Resources/Data/UI]

**Evidence**:
```
{EVIDENCE_FROM_LOGS}
```

**Explanation**:
[Detailed explanation of why this causes flakiness]

**Reproduction Steps**:
1. [Step 1]
2. [Step 2]
3. [Step 3]

#### Contributing Factors:
1. {FACTOR_1}: [Description]
2. {FACTOR_2}: [Description]

### Flaky Test Code Analysis

**Problematic Code**:
```{LANGUAGE}
{PROBLEMATIC_CODE_SNIPPET}
```

**Issues Identified**:
- ❌ Issue 1: [Description]
- ❌ Issue 2: [Description]
- ❌ Issue 3: [Description]

### Recommended Fixes

#### Fix #1: {FIX_NAME} (Primary)

**Approach**: [Describe solution]

**Before**:
```{LANGUAGE}
{FLAKY_CODE}
```

**After**:
```{LANGUAGE}
{FIXED_CODE}
```

**Why This Fixes It**:
[Explain how this addresses the root cause]

**Implementation Steps**:
1. [Step 1]
2. [Step 2]
3. [Step 3]

**Risk Level**: [Low/Medium/High]

#### Fix #2: {FIX_NAME} (Alternative)

[Same format as Fix #1]

#### Fix #3: {FIX_NAME} (Last Resort)

[Same format as Fix #1]

### Specific Flakiness Patterns and Solutions

#### Pattern: Race Condition

**Problem**:
```{LANGUAGE}
// Flaky: async operation not awaited
const result = fetchData();
expect(result).toBeDefined(); // Fails intermittently
```

**Solution**:
```{LANGUAGE}
// Fixed: properly await async operation
const result = await fetchData();
expect(result).toBeDefined(); // Always works
```

#### Pattern: Test Pollution

**Problem**:
```{LANGUAGE}
// Flaky: shared state
let sharedUser;
test('test1', () => {
  sharedUser = createUser();
});
test('test2', () => {
  expect(sharedUser).toBeDefined(); // Fails if test1 doesn't run first
});
```

**Solution**:
```{LANGUAGE}
// Fixed: isolated state
test('test1', () => {
  const user = createUser();
});
test('test2', () => {
  const user = createUser();
  expect(user).toBeDefined(); // Always works
});
```

#### Pattern: Time-Dependent Code

**Problem**:
```{LANGUAGE}
// Flaky: depends on current time
const user = createUser();
expect(user.createdAt).toBe(new Date()); // Fails due to timing
```

**Solution**:
```{LANGUAGE}
// Fixed: freeze time or use ranges
const now = new Date();
const user = createUser();
expect(user.createdAt.getTime()).toBeCloseTo(now.getTime(), -2); // Within 100ms
```

#### Pattern: Fixed Waits

**Problem**:
```{LANGUAGE}
// Flaky: arbitrary wait time
await sleep(1000);
expect(element).toBeVisible(); // Might need more time
```

**Solution**:
```{LANGUAGE}
// Fixed: wait for condition
await waitFor(() => expect(element).toBeVisible(), { timeout: 5000 });
```

#### Pattern: Unordered Collections

**Problem**:
```{LANGUAGE}
// Flaky: assumes order
const items = await getItems();
expect(items[0]).toBe('first'); // Order not guaranteed
```

**Solution**:
```{LANGUAGE}
// Fixed: don't assume order
const items = await getItems();
expect(items).toContain('first'); // Order doesn't matter
// Or sort first
expect(items.sort()).toEqual(['first', 'second'].sort());
```

### Test Infrastructure Improvements

#### Retry Configuration

```{LANGUAGE}
{RETRY_CONFIG_CODE}
```

**Recommendation**: 
- Unit tests: 0 retries (fix flakiness)
- Integration tests: 1-2 retries (network issues)
- E2E tests: 2-3 retries (browser issues)

#### Timeout Configuration

```{LANGUAGE}
{TIMEOUT_CONFIG_CODE}
```

#### Wait Utilities

```{LANGUAGE}
{WAIT_UTILITIES_CODE}
```

**Usage**:
```{LANGUAGE}
// Instead of fixed waits
await waitForCondition(() => element.isVisible());
await waitForElement('#submit-button');
await waitForApiResponse('/api/users');
```

### Environment-Specific Fixes

#### CI/CD Environment

**Issues**:
- Slower execution
- Limited resources
- Parallel test execution

**Solutions**:
```yaml
{CI_CONFIG_IMPROVEMENTS}
```

#### Local Development

**Issues**:
- Different environment variables
- Service availability
- Port conflicts

**Solutions**:
```{LANGUAGE}
{LOCAL_ENV_SETUP}
```

### Prevention Strategies

#### Pre-commit Checks

```bash
{PRE_COMMIT_SCRIPT}
```

#### Flakiness Detection

```{LANGUAGE}
{FLAKINESS_DETECTOR_CODE}
```

**Integration**:
- Run tests N times in CI
- Track failure patterns
- Alert on flaky tests
- Block merges with flaky tests

### Test Stability Metrics

**Before Fix**:
- Success rate: {XX}%
- Average runtime: {TIME}
- Variance: {VARIANCE}

**After Fix** (Projected):
- Success rate: 100%
- Average runtime: {TIME}
- Variance: < 5%

### Verification Plan

**Step 1**: Apply fixes
```bash
{APPLY_FIX_COMMANDS}
```

**Step 2**: Run test repeatedly
```bash
# Run 100 times
for i in {1..100}; do npm test {TEST_NAME}; done

# Or use testing tool
npm test {TEST_NAME} -- --repeat 100
```

**Step 3**: Verify in CI
- Run on multiple branches
- Different time zones
- Parallel execution
- Different OS/browsers

**Success Criteria**:
- [ ] 100/100 successful runs locally
- [ ] 100/100 successful runs in CI
- [ ] No timing variance
- [ ] Passes in all environments

### Monitoring and Alerting

**Flakiness Monitoring**:
```{LANGUAGE}
{MONITORING_CODE}
```

**Alert Configuration**:
- Alert when test fails > 2 times in 10 runs
- Track flakiness rate over time
- Report in test dashboard

### Documentation

**Test Assumptions**:
- Assumption 1: [Document]
- Assumption 2: [Document]

**Known Limitations**:
- Limitation 1: [Document]
- Limitation 2: [Document]

**Maintenance Notes**:
[Guidance for future modifications]

### Related Tests to Check

**Similar Patterns**:
- {TEST_1}: [Why it might be flaky]
- {TEST_2}: [Why it might be flaky]

**Recommended Actions**:
1. Apply same fix pattern
2. Audit test suite for similar issues
3. Update test guidelines

---

**Fix Confidence**: [High/Medium/Low]
**Expected Stability**: [100%/99%/95%]
**Implementation Effort**: [Low/Medium/High]
**Verification Status**: [Pending/In Progress/Verified]
