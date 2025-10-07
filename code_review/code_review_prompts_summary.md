# Code Review Prompts for Pull Requests

This document contains professional-grade prompts designed for AI-powered code review of pull requests. Each prompt is optimized for specific review scenarios and produces structured, actionable feedback.

---

## Table of Contents

### Review Prompt Types

1. **[Comprehensive PR Review](./1-comprehensive-pr-review/prompt.md)** - All-encompassing code review covering quality, security, performance, and architecture
2. **[Security-Focused Review](./2-security-focused-review/prompt.md)** - Security vulnerabilities analysis using STRIDE threat modeling
3. **[Performance Optimization Review](./3-performance-optimization-review/prompt.md)** - Performance bottlenecks and optimization opportunities
4. **[Architecture & Design Review](./4-architecture-design-review/prompt.md)** - SOLID principles, design patterns, and architectural soundness
5. **[Quick Scan for Common Issues](./5-quick-scan/prompt.md)** - Rapid ~2-minute triage for common problems
6. **[Language-Stack-Specific Reviews](./6-language-stack-specific/)** - 27 specialized prompts for different languages and frameworks
   - **Python**
     - [Python Review](./6-language-stack-specific/python-review.md) - Python-specific best practices and idioms
   - **JavaScript/TypeScript - Core** (6 prompts)
     - [Vanilla JS (Frontend)](./6-language-stack-specific/javascript-vanilla-generic.md) - DOM, browser APIs, ES5 patterns
     - [ES6+ JS (Frontend)](./6-language-stack-specific/javascript-es6-generic.md) - Modern JS for frontend
     - [TypeScript (Frontend)](./6-language-stack-specific/typescript-generic.md) - Type-safe frontend development
     - [Vanilla JS (Backend)](./6-language-stack-specific/javascript-vanilla-backend.md) - Node.js with classic patterns
     - [ES6+ JS (Backend)](./6-language-stack-specific/javascript-es6-backend.md) - Modern Node.js
     - [TypeScript (Backend)](./6-language-stack-specific/typescript-backend.md) - Type-safe backend/Node.js
   - **React** (5 prompts)
     - [React Hooks (JS)](./6-language-stack-specific/react-modern-javascript.md) - Functional components with Hooks
     - [React Hooks (TS)](./6-language-stack-specific/react-modern-typescript.md) - Type-safe React with Hooks
     - [React Classes (JS)](./6-language-stack-specific/react-legacy-javascript.md) - Class components (legacy)
     - [React Classes (TS)](./6-language-stack-specific/react-legacy-typescript.md) - Type-safe class components
     - [React Native](./6-language-stack-specific/react-native.md) - Mobile app development
   - **Angular** (2 prompts)
     - [AngularJS 1.x](./6-language-stack-specific/angular-javascript.md) - Legacy Angular with JavaScript
     - [Angular 2+](./6-language-stack-specific/angular-typescript.md) - Modern Angular with TypeScript
   - **Vue** (4 prompts)
     - [Vue 2 (JS)](./6-language-stack-specific/vue2-javascript.md) - Vue 2 with Options API
     - [Vue 2 (TS)](./6-language-stack-specific/vue2-typescript.md) - Type-safe Vue 2
     - [Vue 3 (JS)](./6-language-stack-specific/vue3-javascript.md) - Vue 3 with Composition API
     - [Vue 3 (TS)](./6-language-stack-specific/vue3-typescript.md) - Type-safe Vue 3
   - **Svelte** (2 prompts)
     - [Svelte (JS)](./6-language-stack-specific/svelte-javascript.md) - Svelte with JavaScript
     - [Svelte (TS)](./6-language-stack-specific/svelte-typescript.md) - Type-safe Svelte
   - **Meta-Frameworks** (2 prompts)
     - [Next.js](./6-language-stack-specific/nextjs.md) - Next.js with App/Pages Router, SSR/SSG
     - [Nuxt.js](./6-language-stack-specific/nuxtjs.md) - Nuxt 3 with auto-imports and composables
   - **Backend Frameworks** (2 prompts)
     - [NestJS](./6-language-stack-specific/nestjs.md) - Enterprise Node.js with decorators and DI
     - [Express.js](./6-language-stack-specific/expressjs.md) - Express web framework
   - **API & GraphQL** (1 prompt)
     - [GraphQL](./6-language-stack-specific/graphql.md) - Schema design, resolvers, performance
   - **Testing** (1 prompt)
     - [Jest/Vitest/Cypress](./6-language-stack-specific/testing-jest-vitest-cypress.md) - Unit, integration, and E2E testing
7. **[Test Coverage & Quality Review](./7-test-coverage-quality/prompt.md)** - F.I.R.S.T principles and test quality assessment
8. **[Breaking Changes & API Review](./8-breaking-changes-api/prompt.md)** - API compatibility and semantic versioning
9. **[Documentation Review](./9-documentation-review/prompt.md)** - Documentation quality, completeness, and accuracy
10. **[Cross-File Impact Analysis](./10-cross-file-impact/prompt.md)** - System-wide integration and ripple effect analysis

---

## Best Practices for Using These Prompts

### 1. Customization
- Replace `{PLACEHOLDERS}` with actual PR details
- Include relevant context about your project, team, and standards
- Adjust severity thresholds based on your risk tolerance

### 2. Combination Strategy
Use multiple prompts in sequence:
1. Start with **Quick Scan** for rapid triage
2. Apply **Comprehensive Review** for detailed analysis
3. Deep dive with **Security**, **Performance**, or **Architecture** reviews as needed
4. Always finish with **Test Coverage** and **Documentation** reviews

### 3. Prompt Chaining
For large PRs, use a divide-and-conquer approach:
```
1. Quick Scan → Identify problem areas
2. Focused Review → Deep dive on flagged areas
3. Integration Review → Check system-wide impact
4. Final Check → Test & documentation review
```

### 4. Output Post-Processing
- Parse structured output for automated workflows
- Create GitHub/GitLab comments from findings
- Track metrics (issues found, review time, etc.)
- Feed findings into CI/CD quality gates

### 5. Continuous Improvement
- Collect feedback on false positives/negatives
- Refine prompts based on your team's needs
- Add project-specific rules and standards
- Build a library of custom prompt variations

---

## Example Usage Scenarios

### Scenario 1: High-Risk Security Feature
```
PR: Adding payment processing module

Prompt Sequence:
1. Security-Focused Review (Critical)
2. Comprehensive PR Review
3. Test Coverage Review
4. API Review (for PCI compliance)
```

### Scenario 2: Performance-Critical Change
```
PR: Optimizing database query layer

Prompt Sequence:
1. Performance Optimization Review
2. Cross-File Impact Analysis
3. Test Coverage Review (benchmark tests)
4. Documentation Review
```

### Scenario 3: Routine Feature Addition
```
PR: Add user profile avatar upload

Prompt Sequence:
1. Quick Scan
2. Comprehensive Review
3. Test Coverage Review
```

### Scenario 4: Major Refactoring
```
PR: Refactor authentication system to use OAuth

Prompt Sequence:
1. Architecture & Design Review
2. Breaking Changes & API Review
3. Security-Focused Review
4. Cross-File Impact Analysis
5. Test Coverage Review
6. Documentation Review
```

### Scenario 5: React Component Development
```
PR: New dashboard component with TypeScript

Prompt Sequence:
1. React Hooks (TS) Language-Specific Review
2. Quick Scan
3. Test Coverage Review (component testing)
4. Documentation Review
```

### Scenario 6: Backend API Development
```
PR: New REST API endpoints with NestJS

Prompt Sequence:
1. NestJS Language-Specific Review
2. Security-Focused Review
3. API Review (breaking changes)
4. Testing Review (Jest/integration tests)
5. Documentation Review
```

### Scenario 7: Full-Stack Next.js Feature
```
PR: E-commerce checkout flow with Next.js

Prompt Sequence:
1. Next.js Language-Specific Review
2. Performance Optimization Review
3. Security-Focused Review
4. Cross-File Impact Analysis
5. Testing Review (E2E with Cypress)
```

---

## Advanced Techniques

### Progressive Enhancement
Start with a basic prompt and add context iteratively:
```
First pass: Run quick scan
If issues found: Run comprehensive review on problematic files
If security concerns: Run security-focused review
If performance concerns: Run performance review
```

### Context Injection
Enhance prompts with project-specific context:
```
Add to prompt:
- Team coding standards document
- Previous review findings for this developer
- Project-specific security requirements
- Known technical debt in the area
```

### Multi-Model Approach
Use different AI models for different review types:
- GPT-5 for general comprehensive reviews
- Security-specialized models for security reviews
- Code-optimized models for performance analysis

### Feedback Loop
```
1. Run AI review
2. Developer addresses findings
3. Re-review changed code
4. Iterate until approval
5. Log review metrics for future improvement
```

---

## Metrics & Evaluation

Track these metrics to evaluate prompt effectiveness:

### Review Quality Metrics
- **Accuracy**: % of findings that are valid issues
- **Coverage**: % of real issues caught by the review
- **False Positive Rate**: % of flagged items that aren't real issues
- **Time Saved**: Review time vs. manual review

### Issue Severity Distribution
- Critical issues found per review
- High/Medium/Low issue ratios
- Issue recurrence patterns

### Developer Satisfaction
- Feedback on review helpfulness
- Adoption rate of suggestions
- Time to address review findings

---

## Conclusion

These code review prompts provide a comprehensive framework for automated, high-quality code reviews. They are designed to:

✅ **Catch critical issues** before they reach production
✅ **Improve code quality** systematically
✅ **Educate developers** through detailed feedback
✅ **Save time** while maintaining thorough reviews
✅ **Standardize reviews** across teams

**Remember**: AI code review augments human review but doesn't replace it. Use these prompts as a first pass, then have experienced developers review critical changes and provide domain-specific insights.
