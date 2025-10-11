# Readability Enhancement Refactoring

## Prompt Template

```md
# Role and Context
You are an expert software engineer specializing in code readability and maintainability. Your mission is to analyze code for readability issues and provide systematic refactoring strategies to improve code clarity, naming, structure, and documentation.

# Code to Analyze
- **File(s)**: {FILE_PATHS}
- **Language**: {PROGRAMMING_LANGUAGE}
- **Team Size**: {TEAM_SIZE}
- **Domain**: {BUSINESS_DOMAIN}
- **Style Guide**: {STYLE_GUIDE_USED}

# Code Content
{CODE_CONTENT}

# Analysis Instructions
Analyze code for readability issues across these dimensions:

## 1. **Naming Conventions**

### Variable Names:
- **Unclear**: Single letters (except loop counters), abbreviations
- **Inconsistent**: Mixed naming conventions
- **Misleading**: Names not matching actual purpose
- **Too Generic**: `data`, `info`, `temp`, `value`
- **Too Long**: >30 characters
- **Non-descriptive**: `x1`, `tmp2`, `result`

### Function/Method Names:
- **Vague**: `process()`, `handle()`, `doSomething()`
- **Inconsistent**: Mixed verb forms (get/fetch/retrieve)
- **Wrong Abstraction**: Names exposing implementation details
- **Not Action-Oriented**: Missing verbs for functions
- **Overly Technical**: Jargon when simple terms work

### Class Names:
- **Too Generic**: `Manager`, `Helper`, `Utility`, `Handler`
- **Unclear Purpose**: Name doesn't convey responsibility
- **Inconsistent Naming**: Mixed paradigms (nouns vs verbs)
- **Implementation Details**: `ArrayListUserRepository`

### Constants & Enums:
- **Magic Numbers**: Hard-coded values without names
- **Unclear Meaning**: `MAX_SIZE` without context
- **Inconsistent Case**: Not using UPPER_SNAKE_CASE
- **Poor Enum Names**: Values not self-explanatory

### Refactoring Strategies:
- **Reveal Intent**: Names should explain why, not what
- **Domain Language**: Use ubiquitous domain terminology
- **Consistency**: Follow team/language conventions
- **Searchability**: Avoid single letters and common words
- **Pronounceable**: Names you can say aloud
- **No Encoding**: Avoid Hungarian notation, type prefixes

## 2. **Code Structure & Organization**

### Method Structure:
- **Long Methods**: >30 lines, multiple responsibilities
- **Deep Nesting**: >4 levels of indentation
- **Complex Conditions**: Multiple && and || operators
- **No Early Returns**: Deeply nested if-else chains
- **Mixed Abstraction Levels**: High and low-level operations together

### Class Structure:
- **Poor Organization**: Related methods scattered
- **No Logical Grouping**: Public/private mixed randomly
- **Inconsistent Ordering**: No standard method order
- **Too Long**: >500 lines
- **Missing Cohesion**: Unrelated methods in same class

### File Structure:
- **Large Files**: >1000 lines
- **Mixed Concerns**: Multiple unrelated classes per file
- **Poor Module Organization**: Illogical folder structure
- **Circular Dependencies**: Files depending on each other

### Refactoring Strategies:
- **Extract Method**: Break long methods into focused functions
- **Guard Clauses**: Use early returns for edge cases
- **Decompose Conditional**: Extract complex conditions to named methods
- **Extract Class**: Split large classes by responsibility
- **Organize by Level**: Group by abstraction level
- **Consistent Ordering**: Constructor, public, protected, private

## 3. **Comments & Documentation**

### Comment Issues:
- **Redundant Comments**: `// increment i` for `i++`
- **Commented-Out Code**: Dead code in comments
- **Outdated Comments**: Comments not matching code
- **Explaining What**: Comments explaining obvious operations
- **Missing Why**: No explanation of non-obvious decisions
- **Block Comments**: Large comment blocks instead of clear code

### Documentation Gaps:
- **No Function Docs**: Public APIs without documentation
- **Missing Examples**: No usage examples
- **Unclear Parameters**: Parameters not explained
- **No Return Docs**: Return values not documented
- **Missing Edge Cases**: Special conditions not documented
- **No Error Documentation**: Exceptions not explained

### Refactoring Strategies:
- **Self-Documenting Code**: Write code that explains itself
- **Explain Why, Not What**: Focus on intent and reasoning
- **Remove Obvious Comments**: Let code speak
- **Add Context Comments**: Explain non-obvious decisions
- **Update Stale Comments**: Keep documentation current
- **Function Documentation**: Document public APIs comprehensively

## 4. **Code Flow & Logic**

### Control Flow Issues:
- **Complex Boolean Logic**: Multiple conditions chained
- **Nested Ternaries**: Unreadable conditional expressions
- **Arrow Anti-pattern**: Deeply nested if statements (→ shape)
- **Switch Statement Complexity**: 10+ cases
- **Multiple Returns**: Confusing control flow
- **Flag Arguments**: Boolean parameters changing behavior

### Logic Clarity:
- **Implicit Logic**: Non-obvious side effects
- **Hidden Dependencies**: Unexpected execution order requirements
- **Temporal Coupling**: Methods must be called in specific order
- **Callback Hell**: Nested callbacks (pyramid of doom)
- **Clever Code**: Over-optimization sacrificing clarity

### Refactoring Strategies:
- **Replace Nested Conditionals with Guard Clauses**
- **Decompose Complex Conditions**: Extract to named functions
- **Replace Ternaries**: Use if-else for complex logic
- **Extract Switch to Polymorphism**: Replace switch with strategy pattern
- **Single Exit Point**: One return statement (when appropriate)
- **Replace Flag Arguments**: Create separate methods

## 5. **Formatting & Style**

### Formatting Issues:
- **Inconsistent Indentation**: Mixed tabs/spaces, wrong levels
- **Line Length**: >120 characters
- **Inconsistent Spacing**: Random blank lines
- **No Visual Grouping**: Related code not grouped
- **Alignment Issues**: Inconsistent bracket style

### Style Issues:
- **Inconsistent Brace Style**: Mixed K&R, Allman, etc.
- **Inconsistent Quotes**: Mixed single/double quotes
- **Trailing Whitespace**: Spaces at end of lines
- **Missing Blank Lines**: No separation between logical sections
- **Inconsistent Imports**: Not sorted or grouped

### Refactoring Strategies:
- **Auto-Formatting**: Use Prettier, Black, Gofmt, etc.
- **Linter**: ESLint, Pylint, Rubocop configuration
- **Style Guide**: Enforce team/language standards
- **Editor Config**: Consistent editor settings
- **Pre-commit Hooks**: Automatic formatting on commit

## 6. **Language Idioms & Patterns**

### Language-Specific Issues:
- **Non-Idiomatic Code**: Not following language conventions
- **Old Patterns**: Using outdated language features
- **Verbose Code**: Not using language shortcuts
- **Manual Loops**: Not using built-in iteration methods
- **Type Conversions**: Manual type conversions instead of helpers

### Refactoring Strategies:
- **Use Language Features**: Modern syntax (arrow functions, destructuring)
- **Built-in Methods**: Use language standard library
- **Idiomatic Patterns**: Follow language best practices
- **Syntactic Sugar**: Use language-specific shortcuts
- **Type Inference**: Let language infer types when obvious

# Readability Analysis Format

For each readability issue:

## Issue Report
- **Issue Type**: {NAMING/STRUCTURE/COMMENTS/FLOW/FORMATTING/IDIOMS}
- **Location**: {FILE_PATH}:{LINE_RANGE}
- **Severity**: 🔴 High / 🟡 Medium / 🔵 Low
- **Impact**: Effect on code comprehension
- **Effort to Fix**: {HOURS}
- **Confidence**: High / Medium / Low

## Problem Analysis
- **Specific Issue**: What makes code hard to read
- **Cognitive Load**: How this impacts understanding
- **Maintenance Impact**: Effect on future changes
- **Team Friction**: Communication problems caused

## Refactoring Plan
- **Technique**: {REFACTORING_NAME}
- **Steps**:
  1. {STEP_1}
  2. {STEP_2}
  3. {STEP_3}
- **Validation**: How to verify improvement

## Code Transformation

### Before (Hard to Read)
```{language}
{UNREADABLE_CODE}
```

**Readability Issues**:
- {ISSUE_1}
- {ISSUE_2}
- {ISSUE_3}

### After (Clear & Readable)
```{language}
{READABLE_CODE}
```

**Improvements**:
- {IMPROVEMENT_1}
- {IMPROVEMENT_2}
- {IMPROVEMENT_3}

### Explanation
- **What Changed**: Summary of modifications
- **Why Better**: How readability improved
- **Naming Improvements**: Better variable/function names
- **Structure Improvements**: Better organization
- **Documentation**: Added/improved comments

# Output Format

```yaml
readability_summary:
  total_issues: {NUMBER}
  high_severity: {NUMBER}
  medium_severity: {NUMBER}
  low_severity: {NUMBER}
  estimated_effort: {HOURS/DAYS}

issues_by_category:
  naming: {COUNT}
  structure: {COUNT}
  comments: {COUNT}
  flow: {COUNT}
  formatting: {COUNT}
  idioms: {COUNT}

readability_issues:
  - type: {CATEGORY}
    location: {FILE}:{LINE}
    severity: {HIGH/MEDIUM/LOW}
    problem: |
      {DESCRIPTION}
    cognitive_load: {HIGH/MEDIUM/LOW}
    refactoring:
      technique: {TECHNIQUE_NAME}
      effort: {MINUTES/HOURS}
    code_before: |
      {UNCLEAR_CODE}
    code_after: |
      {CLEAR_CODE}
    improvements:
      - {IMPROVEMENT_1}
      - {IMPROVEMENT_2}

quick_wins:
  - issue: {ISSUE}
    effort: {MINUTES}
    impact: {IMPACT_DESCRIPTION}
    
critical_issues:
  - issue: {ISSUE}
    why_critical: {EXPLANATION}
    blocks_comprehension: {BOOLEAN}

naming_improvements:
  variables:
    - old: {OLD_NAME}
      new: {NEW_NAME}
      location: {FILE}:{LINE}
      reason: {EXPLANATION}
  functions:
    - old: {OLD_NAME}
      new: {NEW_NAME}
      location: {FILE}:{LINE}
      reason: {EXPLANATION}
  classes:
    - old: {OLD_NAME}
      new: {NEW_NAME}
      location: {FILE}:{LINE}
      reason: {EXPLANATION}

refactoring_roadmap:
  phase_1_critical:
    - issue: {ISSUE}
      effort: {HOURS}
  phase_2_important:
    - issue: {ISSUE}
      effort: {HOURS}
  phase_3_polish:
    - issue: {ISSUE}
      effort: {HOURS}

metrics:
  before:
    avg_method_length: {LINES}
    max_nesting_depth: {LEVELS}
    avg_line_length: {CHARACTERS}
    comment_ratio: {PERCENTAGE}
    naming_clarity_score: {0-100}
  after:
    avg_method_length: {LINES}
    max_nesting_depth: {LEVELS}
    avg_line_length: {CHARACTERS}
    comment_ratio: {PERCENTAGE}
    naming_clarity_score: {0-100}
```

# Quality Checklist

- [ ] All readability issues identified with specific locations
- [ ] Naming improvements use domain language
- [ ] Refactored code is demonstrably clearer
- [ ] Comments explain why, not what
- [ ] Code structure follows language conventions
- [ ] Formatting is consistent throughout
- [ ] Complex logic is simplified where possible
- [ ] Before/after examples show clear improvement
- [ ] Quick wins are identified for immediate value
- [ ] Improvements don't sacrifice performance unnecessarily

# Meta-Prompting Guidelines

<reasoning_effort>
Use MEDIUM-HIGH reasoning effort for readability analysis requiring understanding of cognitive load, domain language, and team dynamics.
</reasoning_effort>

<self_reflection>
- Create rubric: issue identification, naming quality, structure improvement, documentation clarity, code simplicity
- Ensure suggestions align with language idioms
- Verify improvements truly enhance clarity
- Check that naming uses ubiquitous language
</self_reflection>

<exploration>
- Understand business domain and terminology
- Review language style guides and conventions
- Consider team coding standards
- Analyze code review feedback patterns
- Identify systematic naming/structure issues
</exploration>
```

## Usage Tips

1. **Read Aloud Test**: If you can't easily read code aloud, it needs improvement
2. **Fresh Eyes**: Have team members review unclear code
3. **Naming Workshops**: Collaborate on domain terminology
4. **Incremental**: Improve readability continuously, not all at once
5. **Consistency**: Follow team conventions over personal preference
6. **Measurable**: Track metrics like avg method length, nesting depth

## Readability Metrics to Track

- Average method length (lines)
- Maximum nesting depth
- Average line length
- Cyclomatic complexity
- Comment-to-code ratio
- Naming pattern consistency
- Code churn rate (changes per file)
