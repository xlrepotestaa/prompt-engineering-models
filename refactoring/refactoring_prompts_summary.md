# Refactoring Prompts for Code Improvement

This document contains professional-grade prompts designed for AI-powered code refactoring. Each prompt is optimized for specific refactoring scenarios and produces structured, actionable recommendations optimized for GPT-5 and Claude 4.5.

---

## Table of Contents

### Refactoring Prompt Types

1. **[Code Smells Detection](./01-code-smells-detection/prompt.md)** - Identify and eliminate code smells (long methods, god classes, duplicated code)
2. **[SOLID Principles](./02-solid-principles/prompt.md)** - Enforce clean architecture principles (SRP, OCP, LSP, ISP, DIP)
3. **[Design Patterns Application](./03-design-patterns/prompt.md)** - Strategic application of proven design patterns
4. **[Technical Debt Reduction](./04-technical-debt/prompt.md)** - Systematic identification and reduction of technical debt
5. **[Performance Refactoring](./05-performance-refactoring/prompt.md)** - Algorithmic and resource optimization strategies
6. **[Testability Improvement](./06-testability-improvement/prompt.md)** - Making code more test-friendly and mockable
7. **[Readability Enhancement](./07-readability-enhancement/prompt.md)** - Improve naming, structure, and documentation
8. **[Modularity & Decoupling](./08-modularity-decoupling/prompt.md)** - Reduce coupling and improve separation of concerns
9. **[Modernization](./09-modernization/prompt.md)** - Update to modern language features and best practices
10. **[Security Hardening](./10-security-hardening/prompt.md)** - Fix vulnerabilities and apply security best practices
11. **[Language & Stack-Specific](./11-language-stack-specific/)** - Tailored refactoring for specific languages and frameworks

---

## Best Practices for Using These Prompts

### 1. Customization

- Replace `{PLACEHOLDERS}` with actual code details and context
- Include relevant project context, team standards, and constraints
- Adjust severity thresholds based on your risk tolerance
- Add project-specific refactoring rules and conventions

### 2. Combination Strategy

Use multiple prompts in sequence for comprehensive refactoring:

1. Start with **Technical Debt** analysis to establish baseline
2. Apply **Code Smells Detection** to identify immediate issues
3. Use **SOLID Principles** for architectural improvements
4. Apply **Design Patterns** where appropriate
5. Implement **Testability Improvements** for safe refactoring
6. Apply **Performance Refactoring** for optimization
7. Use **Security Hardening** to fix vulnerabilities
8. Apply **Readability Enhancement** for maintainability
9. Use **Modernization** to adopt modern features
10. Finish with **Modularity & Decoupling** for clean architecture

### 3. Incremental Refactoring

For large codebases, use a phased approach:

```text
Phase 1: Assessment
- Technical Debt analysis
- Code Smells detection
- Establish baseline metrics

Phase 2: Quick Wins
- Fix critical code smells
- Apply readability improvements
- Update security vulnerabilities

Phase 3: Architectural Improvements
- Apply SOLID principles
- Introduce design patterns
- Improve modularity

Phase 4: Quality Enhancement
- Improve testability
- Optimize performance
- Modernize codebase

Phase 5: Continuous Improvement
- Regular refactoring sessions
- Monitor metrics
- Prevent new debt
```

### 4. Metrics & Measurement

Track these metrics to measure refactoring effectiveness:

- **Code Quality Metrics**: Cyclomatic complexity, code duplication, test coverage
- **Maintainability**: Time to understand code, time to modify, bug fix time
- **Performance**: Response times, resource usage, throughput
- **Security**: Vulnerability count, OWASP compliance score
- **Technical Debt**: Debt ratio, estimated interest cost
- **Team Velocity**: Features delivered, sprint completion rate
- **Developer Satisfaction**: Code quality ratings, refactoring time

### 5. Testing Strategy

Before refactoring:
- Ensure adequate test coverage (>80% for critical paths)
- Add missing tests for code being refactored
- Run full test suite to establish baseline

During refactoring:
- Run tests after each change
- Use TDD for new code
- Validate behavior preservation

After refactoring:
- Run full regression suite
- Perform exploratory testing
- Validate performance hasn't degraded

### 6. Continuous Improvement

- **Allocate Time**: Reserve 20% of sprint capacity for refactoring
- **Quality Gates**: Implement CI/CD checks to prevent new debt
- **Code Reviews**: Use code review prompts to catch issues early
- **Team Education**: Share refactoring knowledge and patterns
- **Documentation**: Maintain architectural decision records (ADRs)
- **Retrospectives**: Reflect on refactoring effectiveness

---

## Example Usage Scenarios

### Scenario 1: Legacy Codebase Takeover

```text
Project: 5-year-old monolithic application with no documentation

Refactoring Sequence:
1. Technical Debt analysis → Establish baseline, identify critical areas
2. Code Smells Detection → Find immediate issues
3. Readability Enhancement → Make code understandable
4. Testability Improvement → Add test coverage
5. SOLID Principles → Improve architecture
6. Modularity & Decoupling → Break up monolith
7. Modernization → Update to current language version
8. Security Hardening → Fix vulnerabilities
```

### Scenario 2: Performance Optimization Initiative

```text
Project: Application with slow response times and high resource usage

Refactoring Sequence:
1. Performance Refactoring → Identify bottlenecks
2. Code Smells Detection → Find performance-related smells
3. Design Patterns → Apply caching, pooling patterns
4. Technical Debt → Address performance debt
5. Modernization → Use modern language optimizations
```

### Scenario 3: Preparing for Scale

```text
Project: Application needs to handle 10x traffic

Refactoring Sequence:
1. Modularity & Decoupling → Enable horizontal scaling
2. Performance Refactoring → Optimize critical paths
3. Design Patterns → Apply scalable patterns (CQRS, Event Sourcing)
4. Technical Debt → Remove scalability blockers
5. Security Hardening → Secure distributed system
```

### Scenario 4: Security Audit Response

```text
Project: Security audit found multiple vulnerabilities

Refactoring Sequence:
1. Security Hardening → Fix identified vulnerabilities
2. Code Smells Detection → Find security anti-patterns
3. SOLID Principles → Reduce attack surface
4. Testability Improvement → Enable security testing
5. Modernization → Update vulnerable dependencies
```

### Scenario 5: New Team Member Onboarding

```text
Project: Making codebase more accessible to new developers

Refactoring Sequence:
1. Readability Enhancement → Improve naming and structure
2. Technical Debt → Document and fix known issues
3. Code Smells → Remove confusing patterns
4. Modularity & Decoupling → Clear boundaries
5. Documentation improvements (separate from refactoring)
```

### Scenario 6: Pre-Production Release

```text
Project: Major release requiring comprehensive quality check

Refactoring Sequence:
1. Technical Debt analysis → Assess overall health
2. Security Hardening → Fix all vulnerabilities
3. Performance Refactoring → Optimize critical paths
4. Code Smells Detection → Clean up before release
5. Testability Improvement → Ensure good coverage
6. Readability Enhancement → Final polish
```

---

## Advanced Techniques

### Pattern 1: Strangler Fig Refactoring

Gradually replace old system with new:

```text
1. Identify boundaries → Use Modularity & Decoupling prompt
2. Create abstraction layer → Apply Design Patterns (Facade, Adapter)
3. Implement new modules → Use SOLID Principles
4. Route traffic gradually → Modernization for new implementation
5. Remove old code → Technical Debt reduction
```

### Pattern 2: Branch by Abstraction

Support parallel implementations during migration:

```text
1. Extract interface → Use Modularity & Decoupling
2. Create abstraction → Apply Design Patterns (Strategy)
3. Implement new version → Use Modernization, SOLID Principles
4. Feature flag switching → Apply Testability patterns
5. Remove old implementation → Clean up Code Smells
```

### Pattern 3: Mikado Method

Dependencies-first refactoring:

```text
1. Identify end goal → Technical Debt analysis
2. Try change → Use appropriate refactoring prompt
3. Identify prerequisites → Technical Debt dependencies
4. Recursively refactor prerequisites → Bottom-up refactoring
5. Apply target refactoring → Final improvement
```

### Pattern 4: Automated Refactoring

Leverage tools and AI:

```text
1. Run static analysis → Identify mechanical refactorings
2. Apply IDE refactorings → Rename, extract, move
3. Use AI prompts → Complex refactorings requiring judgment
4. Validate with tests → Ensure behavior preservation
5. Manual review → Final quality check
```

---

## Metrics & Evaluation

Track these metrics to evaluate refactoring effectiveness:

### Code Quality Metrics

- **Cyclomatic Complexity**: Target <10 per method, <50 per class
- **Code Duplication**: Target <3% duplication
- **Test Coverage**: Target >80% line coverage, >70% branch coverage
- **Code Churn**: Lower churn after refactoring
- **Technical Debt Ratio**: Target <5% (debt hours / total hours)

### Maintainability Metrics

- **Time to Understand**: Reduce onboarding time by X%
- **Time to Modify**: Reduce feature development time by X%
- **Bug Fix Time**: Reduce average bug fix time by X%
- **Code Review Time**: Reduce review time by X%

### Performance Metrics

- **Response Time**: P50, P95, P99 latencies
- **Throughput**: Requests per second
- **Resource Usage**: CPU, memory, I/O utilization
- **Error Rate**: Reduce errors by X%

### Security Metrics

- **Vulnerability Count**: Track critical, high, medium, low
- **OWASP Compliance**: % of OWASP Top 10 addressed
- **Security Score**: Use CVSS or similar scoring
- **Time to Patch**: Reduce vulnerability fix time

### Team Metrics

- **Developer Velocity**: Story points per sprint
- **Developer Satisfaction**: Code quality surveys
- **Knowledge Sharing**: Team understanding of codebase
- **Incident Rate**: Production incidents per month

---

## Refactoring Anti-Patterns to Avoid

### 1. Big Bang Refactoring
**Problem**: Refactoring entire codebase at once
**Solution**: Incremental refactoring with frequent commits

### 2. Refactoring Without Tests
**Problem**: Changing code without safety net
**Solution**: Add tests first, then refactor

### 3. Premature Optimization
**Problem**: Optimizing before measuring
**Solution**: Profile first, optimize bottlenecks

### 4. Over-Engineering
**Problem**: Adding unnecessary abstractions
**Solution**: Apply YAGNI (You Aren't Gonna Need It)

### 5. Ignoring Technical Debt
**Problem**: Never allocating time for refactoring
**Solution**: Dedicate 20% capacity to debt reduction

### 6. Refactoring for Refactoring's Sake
**Problem**: Changing code without clear benefit
**Solution**: Justify each refactoring with metrics

### 7. Not Measuring Impact
**Problem**: Can't show value of refactoring
**Solution**: Track before/after metrics

### 8. Breaking Working Code
**Problem**: Refactoring changes behavior
**Solution**: Test-driven refactoring approach

---

## Tools & Automation

### Static Analysis Tools

- **SonarQube**: Code quality and security analysis
- **PMD**: Code smell detection
- **ESLint/Prettier**: JavaScript/TypeScript linting and formatting
- **Pylint/Black**: Python linting and formatting
- **RuboCop**: Ruby linting
- **StyleCop**: C# linting

### Refactoring Tools

- **IDE Refactoring**: IntelliJ IDEA, VS Code, Visual Studio
- **Refactoring Browsers**: Specialized refactoring tools
- **Codemods**: Automated code transformations
- **AST Manipulation**: jscodeshift, recast for JavaScript

### Metrics & Monitoring

- **Code Climate**: Maintainability and test coverage
- **CodeScene**: Behavioral code analysis
- **CAST**: Technical debt measurement
- **Snyk**: Security vulnerability scanning

### AI-Assisted Refactoring

- **GPT-5/Claude 4.5**: Use prompts from this collection
- **GitHub Copilot**: Inline refactoring suggestions
- **Cursor**: AI-powered code editor
- **Tabnine**: AI code completion

---

## Conclusion

These refactoring prompts provide a comprehensive framework for systematic code improvement. They are designed to:

✅ **Improve Code Quality** - Eliminate smells, apply best practices
✅ **Reduce Technical Debt** - Systematic debt identification and reduction
✅ **Enhance Maintainability** - Readable, testable, modular code
✅ **Boost Performance** - Optimize algorithms and resources
✅ **Strengthen Security** - Fix vulnerabilities, apply OWASP guidelines
✅ **Modernize Codebase** - Adopt modern language features
✅ **Enable Scaling** - Decouple and modularize architecture
✅ **Accelerate Development** - Faster feature delivery through better code

**Remember**: Refactoring is not a one-time activity but a continuous practice. Integrate these prompts into your regular development workflow for sustainable code quality.

**Pro Tip**: Combine these refactoring prompts with the [code review prompts](../code_review/) for a complete code quality solution. Use code review prompts to prevent issues and refactoring prompts to improve existing code.

---

**Optimized for**: GPT-5, Claude 4.5, and other advanced AI models with meta-prompting support for high-quality, context-aware refactoring recommendations.
