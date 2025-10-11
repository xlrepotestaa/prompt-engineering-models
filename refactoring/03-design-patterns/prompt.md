# Design Patterns Application & Refactoring

## Prompt Template

```md
# Role and Context
You are an expert software architect specializing in design patterns and architectural refactoring. Your mission is to identify opportunities for design pattern application and refactor code to use appropriate patterns that improve maintainability, extensibility, and code organization.

# Code to Analyze
- **File(s)**: {FILE_PATHS}
- **Language**: {PROGRAMMING_LANGUAGE}
- **Framework**: {FRAMEWORK}
- **Current Architecture**: {ARCHITECTURE_DESCRIPTION}

# Code Content
{CODE_CONTENT}

# Analysis Instructions
Analyze the code for design pattern opportunities across all three GoF categories:

## 1. **Creational Patterns**

### Singleton
**Use When**: Need exactly one instance, global access point
**Indicators**: Global state management, configuration, logging, connection pools

### Factory Method
**Use When**: Class can't anticipate objects it must create
**Indicators**: Conditional object creation, subclass-specific instantiation

### Abstract Factory
**Use When**: System should be independent of product creation
**Indicators**: Families of related objects, platform-specific implementations

### Builder
**Use When**: Complex object construction with many optional parameters
**Indicators**: Telescoping constructors, 5+ constructor parameters

### Prototype
**Use When**: Need to create new objects by copying existing ones
**Indicators**: Expensive object creation, object cloning needs

## 2. **Structural Patterns**

### Adapter
**Use When**: Need to use existing class with incompatible interface
**Indicators**: Legacy code integration, third-party library wrapping

### Bridge
**Use When**: Separate abstraction from implementation
**Indicators**: Platform-specific implementations, multiple dimensions of variation

### Composite
**Use When**: Treat individual objects and compositions uniformly
**Indicators**: Tree structures, part-whole hierarchies

### Decorator
**Use When**: Add responsibilities to objects dynamically
**Indicators**: Subclass explosion, runtime behavior modification needs

### Facade
**Use When**: Simplify complex subsystem interfaces
**Indicators**: Complex library usage, multiple interdependent classes

### Flyweight
**Use When**: Support large numbers of fine-grained objects efficiently
**Indicators**: Memory concerns, many similar objects

### Proxy
**Use When**: Control access to another object
**Indicators**: Lazy initialization, access control, remote objects

## 3. **Behavioral Patterns**

### Chain of Responsibility
**Use When**: Multiple objects can handle request, handler unknown in advance
**Indicators**: Request processing pipeline, validation chains

### Command
**Use When**: Parameterize objects with operations
**Indicators**: Undo/redo functionality, operation queuing, transaction support

### Iterator
**Use When**: Access collection elements sequentially without exposing representation
**Indicators**: Custom collection traversal, multiple traversal algorithms

### Mediator
**Use When**: Reduce coupling between communicating objects
**Indicators**: Complex object interactions, many-to-many relationships

### Memento
**Use When**: Capture and restore object state
**Indicators**: Undo mechanism, state snapshots, checkpointing

### Observer
**Use When**: One-to-many dependency, notify dependents of state changes
**Indicators**: Event handling, publish-subscribe, data binding

### State
**Use When**: Object behavior depends on state, state-specific operations
**Indicators**: State machines, conditional behavior based on state

### Strategy
**Use When**: Define family of algorithms, make them interchangeable
**Indicators**: Algorithm selection at runtime, eliminate conditionals

### Template Method
**Use When**: Define algorithm skeleton, defer steps to subclasses
**Indicators**: Invariant algorithm structure, subclass customization points

### Visitor
**Use When**: Operations on objects without modifying their classes
**Indicators**: Operations across class hierarchy, adding new operations frequently

## 4. **Modern Patterns**

### Repository
**Use When**: Abstract data persistence layer
**Indicators**: Data access scattered throughout application

### Dependency Injection
**Use When**: Decouple object creation from usage
**Indicators**: Hard-coded dependencies, testing difficulties

### Service Locator
**Use When**: Centralized registry for services
**Indicators**: Service dependency management

### Event Sourcing
**Use When**: Capture all changes as sequence of events
**Indicators**: Audit trail requirements, time-travel debugging

# Pattern Recommendation Format

For each pattern opportunity:

## Opportunity Analysis
- **Pattern Name**: {PATTERN_NAME}
- **Pattern Category**: Creational / Structural / Behavioral
- **Location**: {FILE_PATH}:{LINE_RANGE}
- **Applicability Score**: {1-10}
- **Current Problem**: Description of the issue this pattern solves
- **Confidence**: High / Medium / Low

## Problem Description
- **Current Implementation**: How it's done now
- **Issues**: Pain points, code smells, violations
- **Motivation**: Why this pattern is appropriate
- **Alternative Patterns**: Other patterns considered

## Pattern Application Plan
- **Pattern Structure**: UML or textual description
- **Participants**: Classes/interfaces involved
- **Implementation Steps**:
  1. {STEP_1}
  2. {STEP_2}
  3. {STEP_3}
- **Migration Strategy**: How to transition from current code
- **Testing Approach**: How to verify correct implementation

## Code Transformation

### Before (Current Implementation)
```{language}
{CURRENT_CODE}
```

### After (With Pattern Applied)
```{language}
{REFACTORED_CODE_WITH_PATTERN}
```

### Pattern Components
```{language}
// Interface/Abstract Class
{PATTERN_INTERFACE}

// Concrete Implementations
{CONCRETE_CLASSES}

// Client Usage
{CLIENT_CODE}
```

## Benefits & Trade-offs
- **Benefits**:
  - {BENEFIT_1}
  - {BENEFIT_2}
  - {BENEFIT_3}
- **Trade-offs**:
  - {COMPLEXITY_ADDED}
  - {PERFORMANCE_IMPACT}
  - {LEARNING_CURVE}
- **When NOT to Use**: Situations where this pattern is inappropriate

# Output Format

```yaml
summary:
  patterns_identified: {NUMBER}
  high_priority: {NUMBER}
  medium_priority: {NUMBER}
  low_priority: {NUMBER}
  estimated_effort: {HOURS/DAYS}

pattern_opportunities:
  - pattern: {PATTERN_NAME}
    category: {CREATIONAL/STRUCTURAL/BEHAVIORAL}
    location: {FILE}:{LINE}
    priority: {HIGH/MEDIUM/LOW}
    applicability_score: {1-10}
    problem: |
      {PROBLEM_DESCRIPTION}
    benefits:
      - {BENEFIT_1}
      - {BENEFIT_2}
    complexity_impact: {LOW/MEDIUM/HIGH}
    
  - pattern: {PATTERN_NAME}
    # ... more patterns
    
recommended_implementation_order:
  phase_1:
    - pattern: {PATTERN_NAME}
      reason: {WHY_FIRST}
      dependencies: [{DEPENDENT_PATTERNS}]
      
  phase_2:
    - pattern: {PATTERN_NAME}
      reason: {WHY_SECOND}
      
  phase_3:
    - pattern: {PATTERN_NAME}
      reason: {WHY_THIRD}

code_examples:
  - pattern: {PATTERN_NAME}
    before: |
      {CURRENT_CODE}
    after: |
      {PATTERN_CODE}
    explanation: |
      {HOW_PATTERN_IMPROVES_CODE}

anti_patterns_detected:
  - name: {ANTI_PATTERN_NAME}
    location: {FILE}:{LINE}
    recommendation: {HOW_TO_FIX}
    related_pattern: {CORRECT_PATTERN_TO_USE}

architecture_impact:
  overall_improvement: {HIGH/MEDIUM/LOW}
  maintainability_gain: {PERCENTAGE}
  extensibility_gain: {PERCENTAGE}
  testability_gain: {PERCENTAGE}
  complexity_increase: {PERCENTAGE}
```

# Quality Checklist

- [ ] All applicable design patterns are identified with justification
- [ ] Each pattern recommendation includes clear problem statement
- [ ] Implementation plans are detailed with step-by-step guidance
- [ ] Before/after code examples demonstrate pattern correctly
- [ ] Benefits and trade-offs are honestly evaluated
- [ ] Anti-patterns are detected and flagged
- [ ] Pattern dependencies and implementation order are logical
- [ ] Alternative patterns are considered and discussed
- [ ] Testing strategy is provided for each pattern implementation
- [ ] Complexity impact is assessed realistically

# Meta-Prompting Guidelines

<reasoning_effort>
Use HIGH reasoning effort for design pattern analysis requiring deep understanding of software architecture, pattern interactions, and long-term maintainability implications.
</reasoning_effort>

<self_reflection>
- Create rubric: pattern identification accuracy, applicability assessment, implementation quality, code examples correctness, trade-off analysis
- Ensure patterns are not over-applied (avoid pattern-itis)
- Verify pattern implementations follow canonical forms
- Check that benefits justify added complexity
</self_reflection>

<exploration>
- Analyze existing architecture and design decisions
- Consider pattern interactions and synergies
- Identify architectural smells that patterns can address
- Research language-specific pattern implementations
- Consider modern alternatives to classic patterns
</exploration>

<context_understanding>
- Understand project scale and team size
- Consider performance requirements
- Evaluate team's pattern knowledge level
- Assess maintenance burden vs benefits
</context_understanding>
```

## Usage Tips

1. **Don't Over-Pattern**: Apply patterns only when they solve real problems
2. **Start Simple**: Begin with simpler patterns (Strategy, Factory) before complex ones
3. **Team Knowledge**: Consider team familiarity with patterns
4. **Incremental Application**: Apply one pattern at a time, validate, then proceed
5. **Documentation**: Document pattern usage for team understanding
6. **Performance**: Measure performance impact of pattern introduction

## Pattern Selection Guide

| Problem | Recommended Pattern |
|---------|-------------------|
| Complex object creation | Builder, Factory Method |
| Runtime behavior change | Strategy, State, Decorator |
| Interface incompatibility | Adapter, Facade |
| Object composition | Composite, Decorator |
| Event propagation | Observer, Mediator |
| Algorithm family | Strategy, Template Method |
| State-dependent behavior | State, Strategy |
| Undo/redo operations | Command, Memento |
| Access control | Proxy |
| Many similar objects | Flyweight, Prototype |

## Common Anti-Patterns to Avoid

- **God Object**: Use Facade or decompose into smaller classes
- **Lava Flow**: Remove dead code before applying patterns
- **Golden Hammer**: Don't force patterns where they don't fit
- **Copy-Paste Programming**: Use Template Method or Strategy
- **Spaghetti Code**: Apply Mediator or Chain of Responsibility
