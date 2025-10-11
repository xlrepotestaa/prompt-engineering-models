# Refactoring Prompts Collection

This directory contains a comprehensive collection of AI-powered refactoring prompts designed for systematic code improvement. Each prompt is optimized for specific refactoring scenarios and produces structured, actionable recommendations for GPT-5, Claude 4.5, and other advanced AI models.

## 📁 Structure

```text
refactoring/
├── refactoring_prompts_summary.md           # Main guide with TOC and usage instructions
├── 01-code-smells-detection/                # Detect and eliminate code smells
│   └── prompt.md
├── 02-solid-principles/                     # Enforce clean architecture principles
│   └── prompt.md
├── 03-design-patterns/                      # Strategic pattern application
│   └── prompt.md
├── 04-technical-debt/                       # Systematic debt reduction
│   └── prompt.md
├── 05-performance-refactoring/              # Algorithmic & resource optimization
│   └── prompt.md
├── 06-testability-improvement/              # Making code test-friendly
│   └── prompt.md
├── 07-readability-enhancement/              # Clear naming, structure, documentation
│   └── prompt.md
├── 08-modularity-decoupling/                # Decoupling and separation of concerns
│   └── prompt.md
├── 09-modernization/                        # Updating to modern language features
│   └── prompt.md
├── 10-security-hardening/                   # Hardening through refactoring
│   └── prompt.md
├── 11-language-stack-specific/              # Language-specific refactoring
│   ├── README.md
│   ├── python-refactoring.md
│   ├── javascript-typescript-refactoring.md
│   └── react-refactoring.md
├── 12-comprehensive-refactoring/            # Holistic multi-dimensional refactoring
│   └── prompt.md
├── 13-extract-and-simplify/                 # Breaking down complex code
│   └── prompt.md
└── 14-legacy-modernization/                 # Legacy code transformation
    └── prompt.md
```

## 🚀 Quick Start

1. **Start here**: Read [refactoring_prompts_summary.md](./refactoring_prompts_summary.md) for an overview and usage guidance

2. **Choose your refactoring type**: Select the appropriate prompt based on your needs:
   - **Code smells?** → Use [01-code-smells-detection](./01-code-smells-detection/prompt.md)
   - **Architecture issues?** → Use [02-solid-principles](./02-solid-principles/prompt.md)
   - **Need design patterns?** → Use [03-design-patterns](./03-design-patterns/prompt.md)
   - **High technical debt?** → Use [04-technical-debt](./04-technical-debt/prompt.md)
   - **Performance problems?** → Use [05-performance-refactoring](./05-performance-refactoring/prompt.md)
   - **Hard to test?** → Use [06-testability-improvement](./06-testability-improvement/prompt.md)
   - **Unclear code?** → Use [07-readability-enhancement](./07-readability-enhancement/prompt.md)
   - **Tight coupling?** → Use [08-modularity-decoupling](./08-modularity-decoupling/prompt.md)
   - **Outdated code?** → Use [09-modernization](./09-modernization/prompt.md)
   - **Security concerns?** → Use [10-security-hardening](./10-security-hardening/prompt.md)
   - **Need holistic approach?** → Use [12-comprehensive-refactoring](./12-comprehensive-refactoring/prompt.md)
   - **Complex code to simplify?** → Use [13-extract-and-simplify](./13-extract-and-simplify/prompt.md)
   - **Legacy system to modernize?** → Use [14-legacy-modernization](./14-legacy-modernization/prompt.md)

3. **Customize the prompt**: Replace `{PLACEHOLDERS}` with your code details

4. **Run the analysis**: Feed the prompt to your AI model (GPT-5, Claude 4.5, etc.)

5. **Apply refactorings**: Implement recommended changes incrementally

## 📋 Refactoring Categories

### Core Refactoring Types

- **Code Smells Detection**: Identify long methods, god classes, duplicated code, and other smells
- **SOLID Principles**: Enforce SRP, OCP, LSP, ISP, DIP for clean architecture
- **Design Patterns**: Apply proven patterns (creational, structural, behavioral)
- **Technical Debt**: Quantify and systematically reduce technical debt

### Quality Improvements

- **Performance Refactoring**: Optimize algorithms, databases, memory usage, and concurrency
- **Testability Improvement**: Make code test-friendly with dependency injection and clear interfaces
- **Readability Enhancement**: Improve naming, structure, comments, and code flow
- **Modularity & Decoupling**: Reduce coupling, increase cohesion, define clear boundaries

### Modernization & Security

- **Modernization**: Update to modern language features, APIs, and best practices
- **Security Hardening**: Fix vulnerabilities, apply OWASP guidelines, implement security controls

### Strategic Refactoring

- **Comprehensive Refactoring**: Holistic approach addressing multiple quality dimensions
- **Extract & Simplify**: Break down complex code using extraction techniques
- **Legacy Modernization**: Systematic transformation of legacy systems

### Language-Specific

- **Language & Stack-Specific**: Tailored refactoring for specific languages and frameworks (Python, JavaScript/TypeScript, React, and more)

## 🎯 Usage Patterns

### Pattern 1: Quick Improvement
```text
1. Code Smells Detection
2. Readability Enhancement
3. Quick wins from Technical Debt analysis
```

### Pattern 2: Architecture Refactoring
```text
1. SOLID Principles Analysis
2. Design Patterns Application
3. Modularity & Decoupling
4. Technical Debt Reduction
```

### Pattern 3: Performance Optimization
```text
1. Performance Refactoring
2. Code Smells (performance-related)
3. Modernization (for language optimizations)
```

### Pattern 4: Security Hardening
```text
1. Security Hardening
2. Input Validation (Code Smells)
3. SOLID Principles (reduce attack surface)
4. Testability (for security testing)
```

### Pattern 5: Legacy Code Modernization
```text
1. Modernization
2. Technical Debt Assessment
3. Code Smells Detection
4. Testability Improvement
5. SOLID Principles
```

### Pattern 6: Comprehensive Refactoring
```text
1. Technical Debt Assessment (baseline)
2. Code Smells Detection
3. SOLID Principles
4. Design Patterns
5. Testability Improvement
6. Performance Refactoring
7. Security Hardening
8. Readability Enhancement
9. Modernization
```

## 🔍 When to Use Which Prompt

| Scenario | Recommended Prompts |
|----------|-------------------|
| Legacy codebase takeover | Technical Debt → Code Smells → Modernization |
| Performance issues | Performance → Code Smells → Design Patterns |
| Hard to maintain | Readability → Code Smells → SOLID Principles |
| Difficult to test | Testability → Modularity → SOLID Principles |
| Security audit | Security Hardening → Code Smells → SOLID Principles |
| Scaling challenges | Modularity → Design Patterns → Performance |
| Onboarding new developers | Readability → Technical Debt → Documentation |
| Pre-major release | Comprehensive sequence (all prompts) |
| Modernizing tech stack | Modernization → Technical Debt → Testing |

## ⚡ Pro Tips

1. **Baseline First**: Run Technical Debt analysis to establish baseline metrics
2. **Incremental Refactoring**: Apply one type of refactoring at a time
3. **Test Coverage**: Ensure good test coverage before refactoring
4. **Version Control**: Commit frequently during refactoring
5. **Measure Impact**: Track metrics before and after refactoring
6. **Team Review**: Discuss refactoring strategies with team
7. **Automate**: Use refactoring tools and IDE support where available
8. **Prioritize by ROI**: Focus on high-impact, low-effort refactorings first
9. **Document Decisions**: Keep architectural decision records (ADRs)
10. **Continuous Improvement**: Make refactoring part of regular workflow

## 🔧 Customization

Each prompt can be customized by:

- Adding project-specific coding standards
- Adjusting severity thresholds for your context
- Including team conventions and preferences
- Adding domain-specific refactoring rules
- Modifying output formats for your workflow
- Integrating with your CI/CD pipeline

## 📊 Output Format

All prompts produce structured output with:

- **Severity levels**: Critical 🔴, High 🟡, Medium 🟠, Low 🔵
- **Actionable recommendations**: Specific refactorings with code examples
- **Before/after code**: Clear demonstrations of improvements
- **Metrics**: Quantifiable improvement measurements
- **Effort estimates**: Realistic time estimates for each refactoring
- **Priority rankings**: Impact/effort based prioritization
- **Roadmaps**: Phased implementation plans

## 🎓 Learning Path

1. Start with **Code Smells Detection** to understand common issues
2. Move to **Readability Enhancement** for quick improvements
3. Apply **SOLID Principles** for better architecture
4. Add **Design Patterns** where appropriate
5. Use **Testability Improvement** to enable safe refactoring
6. Apply **Performance Refactoring** for optimization
7. Implement **Security Hardening** for security improvements
8. Use **Modernization** to adopt modern features
9. Apply **Modularity & Decoupling** for better structure
10. Master **Technical Debt** management for long-term health

## 🤝 Contributing

To add new prompts or improve existing ones:

1. Follow the established structure and format
2. Include comprehensive analysis criteria
3. Provide clear before/after code examples
4. Add usage examples and scenarios
5. Update the summary document
6. Include meta-prompting guidelines for GPT-5/Claude 4.5

## 📖 Additional Resources

- **Best Practices**: See [refactoring_prompts_summary.md](./refactoring_prompts_summary.md#best-practices)
- **Example Scenarios**: Check the summary for real-world usage examples
- **Metrics & Evaluation**: Learn how to measure refactoring effectiveness
- **Related Code Review Prompts**: See [../code_review/](../code_review/) for complementary prompts

## 🔗 Integration with Code Review

Refactoring and code review prompts work together:

1. **Code Review First**: Use code review prompts to identify issues
2. **Plan Refactoring**: Use refactoring prompts to plan improvements
3. **Implement Changes**: Apply refactorings incrementally
4. **Review Again**: Use code review prompts to validate improvements

## 📈 Measuring Success

Track these metrics to evaluate refactoring effectiveness:

- **Code Quality**: Complexity, duplication, test coverage
- **Maintainability**: Time to understand, modify, debug code
- **Performance**: Response times, resource usage, throughput
- **Security**: Vulnerabilities found, security score
- **Team Velocity**: Features delivered per sprint
- **Bug Rate**: Defects per 1000 lines of code
- **Technical Debt**: Debt ratio, interest cost
- **Developer Satisfaction**: Team feedback on code quality

---

**Note**: All prompts are optimized for GPT-5 and Claude 4.5, leveraging advanced reasoning capabilities and meta-prompting techniques for high-quality refactoring recommendations.
