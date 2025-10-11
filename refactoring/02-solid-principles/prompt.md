# SOLID Principles Refactoring

## Prompt Template

```md
# Role and Context
You are an expert software architect specializing in clean architecture and SOLID principles. Your goal is to analyze code for SOLID violations and provide systematic refactoring strategies to enforce clean architecture principles.

# Code to Analyze
- **File(s)**: {FILE_PATHS}
- **Language**: {PROGRAMMING_LANGUAGE}
- **Framework**: {FRAMEWORK}
- **Architecture Pattern**: {ARCHITECTURE_TYPE}

# Code Content
{CODE_CONTENT}

# Analysis Instructions
Analyze the code for SOLID principle violations and provide refactoring recommendations:

## 1. **Single Responsibility Principle (SRP)**

**Definition**: A class should have only one reason to change.

### Violations to Detect:
- Classes handling multiple unrelated concerns (e.g., business logic + persistence + UI)
- Methods doing multiple distinct operations
- Classes with more than 5-7 public methods (potential SRP violation)
- Classes mixing high-level and low-level operations
- God classes with 500+ lines of code

### Refactoring Strategies:
- **Extract Class**: Move related functionality to new dedicated classes
- **Facade Pattern**: Simplify complex subsystem interactions
- **Delegate Pattern**: Delegate responsibilities to specialized components
- **Move Method**: Relocate methods to more appropriate classes

## 2. **Open/Closed Principle (OCP)**

**Definition**: Software entities should be open for extension, closed for modification.

### Violations to Detect:
- Switch/case or if-else chains based on type checking
- Hard-coded dependencies requiring modification for new types
- Direct instantiation of concrete classes instead of abstractions
- Lack of extension points (interfaces, abstract classes)
- Modification of existing code to add new features

### Refactoring Strategies:
- **Strategy Pattern**: Define family of algorithms, make them interchangeable
- **Template Method**: Define algorithm skeleton, let subclasses override steps
- **Dependency Injection**: Inject dependencies rather than hard-coding them
- **Plugin Architecture**: Allow runtime extension through plugins
- **Factory Pattern**: Encapsulate object creation logic

## 3. **Liskov Substitution Principle (LSP)**

**Definition**: Subtypes must be substitutable for their base types without altering correctness.

### Violations to Detect:
- Subclasses throwing exceptions not thrown by base class
- Subclasses strengthening preconditions (more restrictive inputs)
- Subclasses weakening postconditions (less restrictive outputs)
- Subclasses removing/ignoring base class functionality
- Type checking to determine subclass type before calling methods
- Breaking contracts defined by base class/interface

### Refactoring Strategies:
- **Extract Interface**: Create proper abstractions that all implementations honor
- **Replace Inheritance with Delegation**: Use composition instead of inheritance
- **Redesign Hierarchy**: Restructure class hierarchy to honor contracts
- **Remove Unused Methods**: Eliminate inherited methods that don't apply

## 4. **Interface Segregation Principle (ISP)**

**Definition**: Clients should not be forced to depend on interfaces they don't use.

### Violations to Detect:
- Fat interfaces with 10+ methods
- Implementing classes that provide empty/stub implementations
- Clients importing interfaces but using only a fraction of methods
- Single interface serving multiple distinct client types
- High interface coupling forcing changes across many clients

### Refactoring Strategies:
- **Interface Splitting**: Break large interfaces into smaller, focused ones
- **Role Interfaces**: Create interfaces based on client needs
- **Adapter Pattern**: Adapt fat interfaces to client-specific needs
- **Extract Interface**: Create minimal interfaces for specific use cases

## 5. **Dependency Inversion Principle (DIP)**

**Definition**: High-level modules should not depend on low-level modules. Both should depend on abstractions.

### Violations to Detect:
- Direct instantiation of concrete classes (new operator everywhere)
- High-level business logic depending on database/framework details
- Tight coupling to specific implementations
- Hard-coded dependencies that can't be mocked/tested
- Lack of dependency injection containers/mechanisms
- Import statements from low-level modules in high-level modules

### Refactoring Strategies:
- **Dependency Injection**: Inject dependencies through constructors/setters
- **Abstract Factory**: Create families of related objects through abstractions
- **Service Locator**: Centralize dependency resolution
- **Inversion of Control (IoC)**: Framework manages object lifecycle
- **Extract Interface**: Define abstractions for concrete implementations

# Refactoring Analysis Format

For each SOLID violation detected:

## Violation Report
- **Principle Violated**: {SRP/OCP/LSP/ISP/DIP}
- **Location**: {FILE_PATH}:{LINE_RANGE}
- **Severity**: 🔴 Critical / 🟡 Important / 🔵 Minor
- **Impact**: How this violation affects code quality
- **Confidence**: High / Medium / Low

## Problem Analysis
- **Current Design Issue**: Detailed explanation of the violation
- **Consequences**: Impact on maintainability, testability, extensibility
- **Root Cause**: Why this violation exists

## Refactoring Plan
- **Recommended Pattern**: {PATTERN_NAME}
- **Implementation Steps**:
  1. {STEP_1}
  2. {STEP_2}
  3. {STEP_3}
- **Dependencies**: Classes/interfaces that need to change
- **Testing Strategy**: How to validate the refactoring

## Code Transformation

### Before (Violating SOLID)
```{language}
{PROBLEMATIC_CODE}
```

### After (SOLID-Compliant)
```{language}
{REFACTORED_CODE}
```

### Explanation
- **What Changed**: Summary of modifications
- **SOLID Compliance**: How this addresses the violation
- **Benefits**: Improved testability, maintainability, extensibility
- **Trade-offs**: Any added complexity or considerations

# Output Format

```yaml
summary:
  total_violations: {NUMBER}
  by_principle:
    srp: {COUNT}
    ocp: {COUNT}
    lsp: {COUNT}
    isp: {COUNT}
    dip: {COUNT}
  critical_violations: {NUMBER}
  estimated_effort: {HOURS/DAYS}

violations:
  - principle: {SRP/OCP/LSP/ISP/DIP}
    location: {FILE}:{LINE}
    severity: {CRITICAL/IMPORTANT/MINOR}
    description: |
      {DETAILED_PROBLEM_DESCRIPTION}
    impact: |
      {CONSEQUENCES_OF_VIOLATION}
    refactoring_pattern: {PATTERN_NAME}
    before_code: |
      {CURRENT_CODE}
    after_code: |
      {REFACTORED_CODE}
    benefits:
      - {BENEFIT_1}
      - {BENEFIT_2}
    effort: {SMALL/MEDIUM/LARGE}
    test_impact: {DESCRIPTION}

refactoring_roadmap:
  phase_1_critical_violations:
    - principle: {PRINCIPLE}
      action: {REFACTORING_ACTION}
      priority: {1-10}
  phase_2_important_violations:
    - principle: {PRINCIPLE}
      action: {REFACTORING_ACTION}
      priority: {1-10}
  phase_3_minor_improvements:
    - principle: {PRINCIPLE}
      action: {REFACTORING_ACTION}
      priority: {1-10}

architecture_recommendations:
  - recommendation: {ARCHITECTURAL_IMPROVEMENT}
    rationale: {WHY_THIS_HELPS}
    solid_principles_addressed: [{PRINCIPLES}]
    
compliance_score:
  srp: {0-100}%
  ocp: {0-100}%
  lsp: {0-100}%
  isp: {0-100}%
  dip: {0-100}%
  overall: {0-100}%
```

# Quality Checklist

Before completing your analysis:

- [ ] All SOLID violations are identified with specific code locations
- [ ] Each violation includes clear explanation and impact analysis
- [ ] Refactoring patterns are appropriate and well-established
- [ ] Before/after code examples demonstrate SOLID compliance
- [ ] Benefits and trade-offs are honestly assessed
- [ ] Refactoring roadmap is prioritized and realistic
- [ ] Testing strategy is provided for each major refactoring
- [ ] Architecture recommendations align with SOLID principles
- [ ] Compliance scores are justified and measurable
- [ ] Implementation steps are detailed and actionable

# Meta-Prompting Guidelines

<reasoning_effort>
Use HIGH reasoning effort for SOLID analysis requiring deep understanding of design principles, architectural patterns, and long-term code maintainability.
</reasoning_effort>

<self_reflection>
- Create rubric: violation accuracy, refactoring appropriateness, code quality, architectural soundness, explanation clarity
- Ensure recommendations follow proven design patterns
- Verify refactored code is more maintainable and testable
- Check that solutions don't introduce new SOLID violations
</self_reflection>

<exploration>
- Analyze class relationships and dependencies
- Consider architectural context and design patterns in use
- Identify systemic design issues across multiple classes
- Research language-specific SOLID implementation patterns
</exploration>
```

## Usage Tips

1. **Start with High-Level Design**: Review architecture before diving into code details
2. **Prioritize DIP and SRP**: These often have the highest impact on code quality
3. **Refactor Incrementally**: Apply SOLID principles gradually, not all at once
4. **Measure Progress**: Track coupling metrics, class size, and test coverage
5. **Balance Pragmatism**: Don't over-engineer; apply SOLID where it provides value
6. **Team Education**: Use violations as teaching moments for design principles

## Common Design Patterns for SOLID Compliance

- **Strategy**: OCP - Define algorithm families
- **Factory Method**: OCP, DIP - Defer instantiation to subclasses
- **Dependency Injection**: DIP - Inject dependencies from outside
- **Adapter**: ISP - Adapt interfaces to client needs
- **Facade**: SRP - Simplify complex subsystems
- **Composite**: OCP, LSP - Treat objects uniformly
- **Observer**: OCP - Define one-to-many dependencies
- **Template Method**: OCP - Define algorithm skeleton
