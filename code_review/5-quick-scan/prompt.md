# Quick Code Review Scan

Perform a rapid assessment focused on the most common and critical code review issues. This is a fast-pass review for quick feedback.

## Pull Request
- **Title**: {PR_TITLE}
- **Files Changed**: {FILE_COUNT}

## Code Changes
{DIFF_CONTENT}

## Quick Scan Checklist (Priority Issues Only)

### 🔴 Critical Issues (Check First)
- [ ] Hardcoded credentials, API keys, or secrets
- [ ] SQL injection vulnerabilities
- [ ] XSS vulnerabilities
- [ ] Unhandled exceptions that could crash the app
- [ ] Infinite loops or recursion without base case
- [ ] Resource leaks (unclosed files, connections, etc.)
- [ ] Breaking API changes without version bump
- [ ] Data loss risks

### 🟡 High-Priority Issues
- [ ] Missing input validation
- [ ] Poor error messages or no error handling
- [ ] N+1 query problems
- [ ] Missing null/undefined checks
- [ ] Unused variables or imports
- [ ] Console.log / debug statements left in code
- [ ] TODO/FIXME comments without issue tracking
- [ ] Magic numbers without explanation
- [ ] Copy-pasted code (DRY violation)

### 🔵 Common Code Smells
- [ ] Long functions (>50 lines)
- [ ] Deep nesting (>3 levels)
- [ ] Too many parameters (>4)
- [ ] Unclear variable names
- [ ] Missing or inadequate comments for complex logic
- [ ] Inconsistent formatting or style
- [ ] Missing tests for new functionality

### ✅ Quick Wins (Good Practices to Note)
- [ ] Good naming conventions
- [ ] Adequate test coverage
- [ ] Clear error handling
- [ ] Proper documentation
- [ ] Clean, readable code

## Output Format (Concise)

### 🚦 Quick Assessment: [PASS / NEEDS WORK / FAIL]

### Issues Found: [Count by severity]
- 🔴 Critical: X
- 🟡 High: X
- 🔵 Medium: X

### Top 3 Issues to Fix
1. **[Issue Title]** - [File:Line] - [One-line description + quick fix]
2. **[Issue Title]** - [File:Line] - [One-line description + quick fix]
3. **[Issue Title]** - [File:Line] - [One-line description + quick fix]

### One-Sentence Summary
[Quick verdict on PR readiness]

### Next Steps
- [ ] Fix critical issues immediately
- [ ] Address high-priority issues before merge
- [ ] Create follow-up tickets for medium issues
- [ ] Ready to merge after fixes

**Review Time**: ~2 minutes | **Depth**: Surface-level scan
