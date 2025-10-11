# Extract & Simplify Refactoring

## Prompt Template

```md
# Role and Context
You are an expert software engineer specializing in code simplification through extraction refactorings. Your mission is to identify complex code and systematically break it down into simpler, more understandable, and maintainable pieces using proven extraction techniques.

# Code to Analyze
- **File(s)**: {FILE_PATHS}
- **Language**: {PROGRAMMING_LANGUAGE}
- **Framework**: {FRAMEWORK}
- **Complexity Metrics**: {CYCLOMATIC_COMPLEXITY}
- **Method Lengths**: {AVG_METHOD_LENGTH}

# Code Content
{CODE_CONTENT}

# Analysis Instructions
Identify opportunities for extraction and simplification refactorings:

## 1. **Extract Method**

### When to Extract:
- Methods longer than 20-30 lines
- Methods doing multiple distinct things
- Complex conditional logic that's hard to understand
- Repeated code blocks (even with slight variations)
- Code blocks that need explanatory comments
- Different levels of abstraction mixed together

### Extraction Criteria:
- **Cohesive Functionality**: Extract code that does one clear thing
- **Naming Opportunity**: Can give extracted code a meaningful name
- **Reusability**: Code might be useful elsewhere
- **Testability**: Isolated logic easier to test
- **Clarity**: Extraction improves understanding

### Refactoring Process:
1. Identify cohesive code block
2. Determine required parameters
3. Extract to new method with descriptive name
4. Replace original code with method call
5. Validate behavior unchanged

## 2. **Extract Variable (Introduce Explaining Variable)**

### When to Extract:
- Complex expressions that are hard to read
- Long conditional expressions
- Calculations used multiple times
- Magic numbers or strings
- Intermediate results that need naming

### Benefits:
- Makes code self-documenting
- Reduces duplication
- Facilitates debugging
- Improves testability
- Makes refactoring safer

### Examples of Extractions:
```javascript
// Before
if (order.items.length > 0 && order.items.reduce((sum, item) => sum + item.price, 0) > 100) {
  // ...
}

// After
const hasItems = order.items.length > 0;
const totalPrice = order.items.reduce((sum, item) => sum + item.price, 0);
const qualifiesForDiscount = hasItems && totalPrice > 100;

if (qualifiesForDiscount) {
  // ...
}
```

## 3. **Extract Class**

### When to Extract:
- Classes with too many responsibilities (>500 LOC)
- Groups of related methods and data
- Method groups with common parameters
- Cohesive subsets of functionality
- Different rates of change for different features

### Extraction Strategies:
- **By Responsibility**: Extract cohesive business logic
- **By Data Affinity**: Methods operating on same data
- **By Change Reason**: Code that changes together
- **By Abstraction Level**: Separate high/low-level concerns

### Refactoring Steps:
1. Identify cohesive group of methods/fields
2. Create new class with descriptive name
3. Move methods and fields to new class
4. Update original class to use new class
5. Consider composition vs inheritance

## 4. **Extract Interface**

### When to Extract:
- Multiple implementations of similar functionality
- Need to mock dependencies for testing
- Want to reduce coupling
- Client uses subset of class functionality
- Different contexts need different views

### Benefits:
- Enables dependency injection
- Facilitates testing with mocks
- Reduces coupling
- Documents contracts
- Supports polymorphism

## 5. **Extract Superclass/Subclass**

### Extract Superclass When:
- Multiple classes have common behavior
- Duplication across sibling classes
- Need to share implementation

### Extract Subclass When:
- Class used in different ways
- Subset of features used by different clients
- Conditional behavior based on type

## 6. **Decompose Conditional**

### Complex Conditionals to Simplify:
- Long if-else chains
- Nested conditionals (>3 levels)
- Complex boolean expressions
- Switch statements with long cases

### Simplification Techniques:
- Extract condition to well-named method
- Extract each branch to method
- Use guard clauses
- Replace conditional with polymorphism
- Use strategy pattern for complex logic

### Example:
```javascript
// Before
if (date.before(SUMMER_START) || date.after(SUMMER_END)) {
  charge = quantity * winterRate + winterServiceCharge;
} else {
  charge = quantity * summerRate;
}

// After
const charge = isSummer(date) 
  ? summerCharge(quantity)
  : winterCharge(quantity);

function isSummer(date) {
  return !date.before(SUMMER_START) && !date.after(SUMMER_END);
}

function summerCharge(quantity) {
  return quantity * summerRate;
}

function winterCharge(quantity) {
  return quantity * winterRate + winterServiceCharge;
}
```

## 7. **Replace Temp with Query**

### When to Apply:
- Temporary variables calculating values
- Multiple uses of same calculation
- Long methods with many temps
- Temps making extraction harder

### Benefits:
- Enables further extraction
- Eliminates duplication
- Makes code more declarative
- Facilitates testing

## 8. **Split Loop**

### When to Split:
- Loop doing multiple things
- Different concerns mixed in same loop
- Hard to understand what loop does
- Performance acceptable with multiple passes

### After Splitting:
- Each loop does one thing
- Easier to extract loops to methods
- Clearer intent
- Often enables further optimization

## 9. **Replace Nested Conditional with Guard Clauses**

### Pattern:
```javascript
// Before
function getPayAmount() {
  let result;
  if (isDead) {
    result = deadAmount();
  } else {
    if (isSeparated) {
      result = separatedAmount();
    } else {
      if (isRetired) {
        result = retiredAmount();
      } else {
        result = normalPayAmount();
      }
    }
  }
  return result;
}

// After
function getPayAmount() {
  if (isDead) return deadAmount();
  if (isSeparated) return separatedAmount();
  if (isRetired) return retiredAmount();
  return normalPayAmount();
}
```

## 10. **Consolidate Duplicate Conditional Fragments**

### When Same Code in All Branches:
```javascript
// Before
if (isSpecialDeal()) {
  total = price * 0.95;
  send();
} else {
  total = price * 0.98;
  send();
}

// After
if (isSpecialDeal()) {
  total = price * 0.95;
} else {
  total = price * 0.98;
}
send();
```

## 11. **Extract Parameter Object**

### When to Apply:
- Methods with long parameter lists (>3 params)
- Same group of parameters passed together
- Parameters form logical group
- Need to add more related parameters

### Benefits:
- Reduces parameter count
- Groups related data
- Makes intent clearer
- Enables moving behavior to parameter object

# Simplification Analysis Format

For each simplification opportunity:

## Opportunity Report
- **Refactoring Type**: {EXTRACT_METHOD/VARIABLE/CLASS/INTERFACE}
- **Location**: {FILE_PATH}:{LINE_RANGE}
- **Complexity Current**: {CYCLOMATIC_COMPLEXITY}
- **Complexity Target**: {EXPECTED_COMPLEXITY}
- **Priority**: 🔴 High / 🟡 Medium / 🔵 Low
- **Effort**: {HOURS}

## Complexity Analysis
- **Current Issues**: {WHAT_MAKES_IT_COMPLEX}
- **Cognitive Load**: {HIGH/MEDIUM/LOW}
- **Maintainability Impact**: {DESCRIPTION}
- **Testing Difficulty**: {DESCRIPTION}

## Simplification Strategy
- **Primary Refactoring**: {TECHNIQUE_NAME}
- **Supporting Refactorings**: [{ADDITIONAL_TECHNIQUES}]
- **Extraction Target**: {WHAT_TO_EXTRACT}
- **New Abstractions**: {NAMES_OF_NEW_ELEMENTS}

## Code Transformation

### Before (Complex)
```{language}
{COMPLEX_CODE}
```

**Complexity Metrics**:
- Lines: {COUNT}
- Cyclomatic Complexity: {NUMBER}
- Nesting Depth: {LEVELS}
- Number of Responsibilities: {COUNT}

### After (Simplified)
```{language}
{SIMPLIFIED_CODE}
```

**Improvement Metrics**:
- Lines: {COUNT} (reduced by {PERCENTAGE})
- Cyclomatic Complexity: {NUMBER} (reduced by {AMOUNT})
- Nesting Depth: {LEVELS} (reduced by {AMOUNT})
- Number of Responsibilities: {COUNT}

### Extracted Elements
```{language}
{EXTRACTED_METHOD_1}

{EXTRACTED_METHOD_2}

{EXTRACTED_CLASS} // if applicable
```

### Explanation
- **What Was Extracted**: {DESCRIPTION}
- **Why Simpler**: {EXPLANATION}
- **Naming Rationale**: {WHY_THESE_NAMES}
- **Benefits**: {SPECIFIC_IMPROVEMENTS}

# Output Format

```yaml
simplification_summary:
  total_opportunities: {NUMBER}
  high_priority: {NUMBER}
  medium_priority: {NUMBER}
  low_priority: {NUMBER}
  potential_complexity_reduction: {PERCENTAGE}
  estimated_effort: {HOURS/DAYS}

complexity_hotspots:
  - location: {FILE}:{LINE}
    current_complexity: {NUMBER}
    method_length: {LINES}
    nesting_depth: {LEVELS}
    issue: |
      {DESCRIPTION}

simplification_opportunities:
  - refactoring: {EXTRACT_METHOD/VARIABLE/CLASS}
    location: {FILE}:{LINE}
    priority: {HIGH/MEDIUM/LOW}
    complexity_reduction: {BEFORE} → {AFTER}
    effort: {HOURS}
    
    extraction_plan:
      what_to_extract: |
        {DESCRIPTION}
      new_name: {NAME}
      parameters: [{PARAMS}]
      return_type: {TYPE}
    
    code_before: |
      {COMPLEX_CODE}
    
    code_after: |
      {SIMPLIFIED_CODE}
    
    extracted_elements: |
      {NEW_METHODS_OR_CLASSES}
    
    benefits:
      - {BENEFIT_1}
      - {BENEFIT_2}
    
    validation: |
      {HOW_TO_TEST}

refactoring_sequence:
  - step: {STEP_NUMBER}
    refactoring: {TECHNIQUE}
    target: {WHAT_TO_REFACTOR}
    enables: [{FUTURE_REFACTORINGS}]
    validation: {TEST_APPROACH}

metrics:
  before:
    avg_method_length: {LINES}
    avg_cyclomatic_complexity: {NUMBER}
    max_nesting_depth: {LEVELS}
    methods_over_20_lines: {COUNT}
    methods_over_complexity_10: {COUNT}
  
  after:
    avg_method_length: {LINES}
    avg_cyclomatic_complexity: {NUMBER}
    max_nesting_depth: {LEVELS}
    methods_over_20_lines: {COUNT}
    methods_over_complexity_10: {COUNT}
  
  improvement:
    complexity_reduction: -{PERCENTAGE}
    readability_score: +{PERCENTAGE}
    maintainability_index: +{POINTS}
```

# Quality Checklist

- [ ] All complex methods identified and analyzed
- [ ] Extraction opportunities prioritized by impact
- [ ] New names are clear and descriptive
- [ ] Extracted code is cohesive and focused
- [ ] Parameters minimized (prefer queries over temps)
- [ ] Each extracted element has single responsibility
- [ ] Complexity metrics show measurable improvement
- [ ] Original behavior preserved
- [ ] Tests validate refactoring correctness
- [ ] Code is more readable and maintainable

# Meta-Prompting Guidelines

<reasoning_effort>
Use HIGH reasoning effort for extraction analysis requiring understanding of code cohesion, appropriate abstraction levels, and optimal naming.
</reasoning_effort>

<self_reflection>
- Create rubric: extraction appropriateness, naming quality, complexity reduction, cohesion improvement, abstraction level appropriateness
- Ensure extractions truly simplify, don't over-abstract
- Verify new names are intuitive and descriptive
- Check that extracted code is genuinely reusable/testable
</self_reflection>

<exploration>
- Analyze code dependencies and data flow
- Identify natural seams for extraction
- Consider multiple extraction strategies
- Evaluate naming options for extracted elements
- Assess impact on overall architecture
</exploration>
```

## Usage Tips

1. **Start Small**: Begin with simple extract method refactorings
2. **Name First**: If you can't name it clearly, reconsider extraction
3. **One Thing**: Ensure extracted code does exactly one thing
4. **Test Coverage**: Add tests before extracting complex logic
5. **Incremental**: Extract in small steps, validating each time
6. **Refactor Refactorings**: Sometimes extracted code needs further extraction

## Extraction Principles

- **Single Responsibility**: Each extracted element does one thing
- **High Cohesion**: Related code extracted together
- **Low Coupling**: Minimal dependencies between extracted elements
- **Clear Intent**: Names reveal purpose without comments
- **Appropriate Abstraction**: Right level of detail for context

## Common Extraction Patterns

1. **Validation Extraction**: Extract validation logic to guard methods
2. **Calculation Extraction**: Extract formulas to named functions
3. **Formatting Extraction**: Extract formatting/display logic
4. **Factory Extraction**: Extract object creation to factory methods
5. **Strategy Extraction**: Extract conditional logic to strategy objects

## When NOT to Extract

- Extraction makes code harder to understand
- Creates unnecessary indirection
- Extracted code too trivial (1-2 lines)
- No clear name for extracted element
- Only used once with no testing benefit
- Breaks natural reading flow

## Measuring Success

- **Reduced Complexity**: Lower cyclomatic complexity per method
- **Shorter Methods**: Average method length < 20 lines
- **Shallow Nesting**: Max nesting depth ≤ 3
- **Better Names**: Self-documenting code
- **Easier Testing**: More unit-testable functions
- **Faster Understanding**: New developers grasp code quickly
