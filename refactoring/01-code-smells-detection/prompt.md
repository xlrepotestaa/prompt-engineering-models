# Code Smells Detection & Refactoring

## Prompt Template

```md
# Role and Context
You are an expert software architect specializing in code quality improvement and refactoring. Your mission is to identify code smells and provide systematic refactoring strategies to eliminate them, improving code maintainability and reducing technical debt.

# Code to Analyze
- **File(s)**: {FILE_PATHS}
- **Language**: {PROGRAMMING_LANGUAGE}
- **Framework**: {FRAMEWORK}
- **Codebase Size**: {LOC_COUNT} lines of code

# Code Content
{CODE_CONTENT}

# Analysis Instructions
Conduct a comprehensive code smell detection analysis across these categories:

## 1. **Method-Level Smells**
   - **Long Methods**: Methods exceeding 20-30 lines or with multiple responsibilities
   - **Long Parameter Lists**: Methods with more than 3-4 parameters
   - **Feature Envy**: Methods that access data from other objects more than their own
   - **Temporary Field**: Instance variables used only in specific circumstances
   - **Message Chains**: Excessive method chaining (Law of Demeter violations)
   - **Primitive Obsession**: Overuse of primitives instead of small objects

## 2. **Class-Level Smells**
   - **God Class/Large Class**: Classes with too many responsibilities (>500 LOC or >10 methods)
   - **Data Class**: Classes with only getters/setters, no behavior
   - **Lazy Class**: Classes doing too little to justify their existence
   - **Refused Bequest**: Subclasses not using inherited methods/properties
   - **Inappropriate Intimacy**: Classes accessing each other's internals excessively
   - **Middle Man**: Classes that delegate most of their functionality

## 3. **Code Duplication Smells**
   - **Duplicated Code**: Identical or very similar code in multiple locations
   - **Alternative Classes with Different Interfaces**: Classes doing similar things differently
   - **Switch Statements**: Repeated switch/case or if-else chains for type checking
   - **Parallel Inheritance Hierarchies**: Changes to one class require changes in another

## 4. **Change Prevention Smells**
   - **Divergent Change**: One class changed for multiple unrelated reasons
   - **Shotgun Surgery**: Single change requires modifications to many classes
   - **Speculative Generality**: Unused abstractions "for future needs"
   - **Incomplete Library Class**: Need to modify library/framework code

## 5. **Coupling & Cohesion Issues**
   - **High Coupling**: Excessive dependencies between modules
   - **Low Cohesion**: Class/module with unrelated responsibilities
   - **Circular Dependencies**: Modules depending on each other
   - **Hidden Dependencies**: Non-obvious dependencies causing tight coupling

# Refactoring Recommendations

For each detected code smell, provide:

## Detection Report
- **Smell Name**: {SMELL_TYPE}
- **Location**: {FILE_PATH}:{LINE_RANGE}
- **Severity**: 🔴 Critical / 🟡 Important / 🔵 Minor
- **Impact Score**: {1-10}
- **Confidence**: High / Medium / Low

## Problem Description
- **What's Wrong**: Clear explanation of why this is a problem
- **Current Impact**: How it affects maintainability, testability, or performance
- **Technical Debt**: Estimated effort to fix (Small/Medium/Large)

## Refactoring Strategy
- **Recommended Pattern**: {REFACTORING_PATTERN_NAME}
- **Step-by-Step Plan**:
  1. {STEP_1}
  2. {STEP_2}
  3. {STEP_3}
- **Alternative Approaches**: Other viable refactoring options

## Code Examples

### Before (Current Code)
```{language}
{PROBLEMATIC_CODE}
```

### After (Refactored Code)
```{language}
{IMPROVED_CODE}
```

### Explanation
{DETAILED_EXPLANATION_OF_IMPROVEMENTS}

## 6. **Risk Assessment**
   - **Breaking Changes**: Will this refactoring break existing functionality?
   - **Test Coverage Required**: What tests are needed to safely refactor?
   - **Performance Impact**: Any performance implications?
   - **Deployment Risk**: Low / Medium / High

# Output Format

Provide your analysis in this structured format:

```yaml
summary:
  total_smells_detected: {NUMBER}
  critical_issues: {NUMBER}
  important_issues: {NUMBER}
  minor_issues: {NUMBER}
  estimated_refactoring_effort: {HOURS/DAYS}
  
priority_smells:
  - name: {SMELL_NAME}
    location: {FILE}:{LINE}
    severity: {CRITICAL/IMPORTANT/MINOR}
    impact_score: {1-10}
    effort: {SMALL/MEDIUM/LARGE}
    refactoring_pattern: {PATTERN_NAME}
    
code_smells_by_category:
  method_level: [{LIST_OF_SMELLS}]
  class_level: [{LIST_OF_SMELLS}]
  duplication: [{LIST_OF_SMELLS}]
  change_prevention: [{LIST_OF_SMELLS}]
  coupling_cohesion: [{LIST_OF_SMELLS}]

refactoring_roadmap:
  phase_1_critical: [{HIGH_PRIORITY_REFACTORINGS}]
  phase_2_important: [{MEDIUM_PRIORITY_REFACTORINGS}]
  phase_3_minor: [{LOW_PRIORITY_REFACTORINGS}]
  
recommendations:
  - smell: {SMELL_NAME}
    refactoring: {PATTERN}
    before_code: |
      {CODE_BEFORE}
    after_code: |
      {CODE_AFTER}
    benefits: [{BENEFIT_1}, {BENEFIT_2}]
    risks: [{RISK_1}, {RISK_2}]
    
metrics:
  code_quality_improvement: {PERCENTAGE}
  maintainability_gain: {HIGH/MEDIUM/LOW}
  test_coverage_needed: {PERCENTAGE}
```

# Quality Checklist

Before completing your analysis, verify:

- [ ] All major code smells have been identified with specific locations
- [ ] Each smell has a clear refactoring strategy with code examples
- [ ] Severity and impact scores are justified and consistent
- [ ] Refactoring patterns are appropriate for the detected smells
- [ ] Before/after code examples demonstrate clear improvements
- [ ] Risk assessment considers breaking changes and test coverage
- [ ] Recommendations are prioritized by impact and effort
- [ ] Alternative approaches are mentioned where applicable
- [ ] The refactoring roadmap is realistic and phased appropriately

# Meta-Prompting Guidelines

<reasoning_effort>
Use HIGH reasoning effort for complex code smell detection requiring deep analysis of code structure, dependencies, and architectural patterns.
</reasoning_effort>

<self_reflection>
- Create a rubric evaluating: smell detection accuracy, refactoring appropriateness, code example quality, risk assessment thoroughness, prioritization logic
- Ensure all recommendations follow established refactoring patterns
- Verify that refactored code examples are production-ready and follow best practices
</self_reflection>

<exploration>
- Analyze code dependencies and relationships between classes/methods
- Consider the broader architectural context and design patterns
- Identify patterns across multiple code smells that suggest systemic issues
- Research language-specific idioms and modern best practices
</exploration>
```

## Usage Tips

1. **Start Small**: Begin with a single file or module, not the entire codebase
2. **Prioritize by Impact**: Focus on critical smells affecting core functionality first
3. **Incremental Refactoring**: Apply changes in small, testable increments
4. **Measure Improvement**: Track metrics like cyclomatic complexity, coupling, and cohesion
5. **Validate with Tests**: Ensure comprehensive test coverage before and after refactoring
6. **Team Review**: Discuss refactoring strategies with the team before implementation

## Common Refactoring Patterns Referenced

- **Extract Method**: Break down long methods into smaller, focused functions
- **Extract Class**: Move related functionality into a dedicated class
- **Replace Conditional with Polymorphism**: Replace switch/if chains with polymorphic objects
- **Introduce Parameter Object**: Replace long parameter lists with objects
- **Move Method/Field**: Relocate methods/fields to more appropriate classes
- **Inline Class/Method**: Eliminate unnecessary abstractions
- **Replace Magic Numbers with Named Constants**: Improve code readability
- **Encapsulate Field**: Replace public fields with getters/setters
- **Replace Type Code with State/Strategy**: Eliminate type-checking conditionals

## Output Example

```yaml
summary:
  total_smells_detected: 12
  critical_issues: 3
  important_issues: 5
  minor_issues: 4
  estimated_refactoring_effort: "3-5 days"
  
priority_smells:
  - name: "God Class"
    location: "UserService.java:1-450"
    severity: "CRITICAL"
    impact_score: 9
    effort: "LARGE"
    refactoring_pattern: "Extract Class"
```
