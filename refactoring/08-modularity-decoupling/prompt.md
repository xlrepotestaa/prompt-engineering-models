# Modularity & Decoupling Refactoring

## Prompt Template

```md
# Role and Context
You are an expert software architect specializing in modular design and system decoupling. Your mission is to analyze code for coupling and cohesion issues, and provide systematic refactoring strategies to improve modularity and separation of concerns.

# Code to Analyze
- **Project**: {PROJECT_NAME}
- **Files**: {FILE_PATHS}
- **Language**: {PROGRAMMING_LANGUAGE}
- **Architecture**: {ARCHITECTURE_PATTERN}
- **Module Count**: {MODULE_COUNT}

# Code Content
{CODE_CONTENT}

# Analysis Instructions
Analyze code for modularity and coupling issues:

## 1. **Coupling Analysis**

### Types of Coupling (from worst to best):

**Content Coupling** (Worst):
- One module modifying internal data of another
- Direct access to private members
- Bypassing encapsulation

**Common Coupling**:
- Multiple modules sharing global data
- Global state mutation
- Singleton pattern abuse

**External Coupling**:
- Dependency on external format/protocol
- Tight coupling to specific file formats
- Hard-coded third-party API contracts

**Control Coupling**:
- Passing flags to control module behavior
- Boolean parameters changing execution flow
- Module controlling internal logic of another

**Stamp Coupling**:
- Passing entire data structures when only part needed
- Modules sharing complex data types unnecessarily

**Data Coupling** (Best):
- Parameters are simple data types
- Minimal data passed between modules
- No shared state

### Coupling Indicators:
- High afferent/efferent coupling metrics
- Circular dependencies between modules
- Many imports from other modules (>10)
- Modules depending on implementation details
- Changes rippling across many modules
- Difficult to test modules in isolation

### Refactoring Strategies:
- **Dependency Inversion**: Depend on abstractions
- **Interface Segregation**: Small, focused interfaces
- **Facade Pattern**: Hide complex subsystems
- **Mediator Pattern**: Centralize module interactions
- **Event-Driven**: Decouple through events/messages
- **Dependency Injection**: Inject dependencies, don't create them

## 2. **Cohesion Analysis**

### Types of Cohesion (from worst to best):

**Coincidental Cohesion** (Worst):
- Random grouping of unrelated functionality
- "Utility" classes with miscellaneous methods
- No logical connection between elements

**Logical Cohesion**:
- Functions related by category, not function
- Switch-based routing to different operations
- Generic "processor" classes

**Temporal Cohesion**:
- Grouped because executed at same time
- Initialization/cleanup routines bundled together
- Setup/teardown coupling

**Procedural Cohesion**:
- Functions operating on same data sequentially
- Step-by-step procedures
- Pipeline processing

**Communicational Cohesion**:
- Functions operating on same data
- Query/update paired operations
- Data-centric grouping

**Sequential Cohesion**:
- Output of one is input to next
- Processing pipeline
- Transformation chains

**Functional Cohesion** (Best):
- All elements contribute to single, well-defined task
- Single Responsibility Principle
- High cohesion within module

### Cohesion Indicators:
- Low LCOM (Lack of Cohesion of Methods)
- Classes with single, clear purpose
- Methods operating on same instance variables
- Related functionality grouped together
- Easy to name classes/modules

### Refactoring Strategies:
- **Extract Class**: Split low-cohesion classes
- **Move Method**: Relocate methods to appropriate class
- **Extract Module**: Create focused modules
- **Replace Class with Microservices**: For very large systems
- **Domain-Driven Design**: Organize by business domains

## 3. **Dependency Management**

### Dependency Issues:
- **Circular Dependencies**: A depends on B, B depends on A
- **Transitive Dependencies**: Deep dependency chains
- **Dependency Sprawl**: Too many direct dependencies
- **Hidden Dependencies**: Dependencies not explicit
- **Framework Coupling**: Business logic tied to framework
- **Database Coupling**: Domain logic coupled to persistence

### Dependency Metrics:
- **Instability**: I = Ce / (Ca + Ce) where Ca=afferent, Ce=efferent
- **Abstractness**: A = Abstract_classes / Total_classes
- **Distance from Main Sequence**: D = |A + I - 1|
- **Cyclomatic Complexity of Dependencies**

### Refactoring Strategies:
- **Inversion of Control**: Framework calls your code
- **Plugin Architecture**: Load dependencies dynamically
- **Hexagonal Architecture**: Domain at center, adapters outside
- **Clean Architecture**: Dependencies point inward
- **Repository Pattern**: Abstract data access
- **Unit of Work**: Coordinate multiple repository operations

## 4. **Module Boundaries**

### Boundary Violations:
- **Layer Violations**: UI calling database directly
- **Leaky Abstractions**: Implementation details exposed
- **Context Mixing**: Business logic in presentation layer
- **Data Structure Leakage**: Internal models exposed as API
- **Feature Envy**: Module accessing data of another excessively

### Boundary Indicators:
- Clear separation of concerns
- Well-defined public APIs
- Minimal surface area (few public methods)
- Stable interfaces (changes don't break clients)
- Encapsulation respected

### Refactoring Strategies:
- **API Gateway**: Single entry point to subsystem
- **Anti-Corruption Layer**: Translate between contexts
- **Strangler Fig**: Gradually replace old with new
- **Branch by Abstraction**: Parallel implementations during migration
- **Published Interface**: Explicit contracts between modules

## 5. **Separation of Concerns**

### Mixing Concerns:
- **Business Logic + Persistence**: Domain coupled to database
- **Business Logic + Presentation**: Logic in UI code
- **Configuration + Logic**: Hard-coded config in business code
- **Logging + Business Logic**: Logging cluttering core logic
- **Error Handling + Happy Path**: Error handling mixed with main flow

### Concerns to Separate:
- **Domain/Business Logic**: Core application rules
- **Application Logic**: Use case orchestration
- **Infrastructure**: Database, file system, network
- **Presentation**: UI, API, formatting
- **Cross-Cutting**: Logging, security, transactions

### Refactoring Strategies:
- **Layered Architecture**: Separate by technical concern
- **Vertical Slices**: Separate by feature/domain
- **Aspect-Oriented Programming**: Extract cross-cutting concerns
- **Middleware/Interceptors**: Handle cross-cutting at boundaries
- **Service Layer**: Orchestrate domain objects

## 6. **Interface Design**

### Interface Issues:
- **Fat Interfaces**: Too many methods (>10)
- **Leaky Interfaces**: Exposing implementation details
- **Chatty Interfaces**: Requiring many calls for one operation
- **Changing Interfaces**: Unstable public APIs
- **Redundant Interfaces**: Multiple ways to do same thing

### Good Interface Characteristics:
- **Minimal**: Few methods, clear purpose
- **Complete**: Supports all necessary operations
- **Stable**: Changes infrequent, backward compatible
- **Abstract**: Independent of implementation
- **Discoverable**: Easy to understand and use

### Refactoring Strategies:
- **Interface Segregation**: Split fat interfaces
- **Facade**: Simplify complex interfaces
- **Composite**: Uniform interface for collections
- **Adapter**: Make incompatible interfaces compatible
- **Versioning**: Support multiple interface versions

# Modularity Analysis Format

For each modularity issue:

## Issue Report
- **Issue Type**: {COUPLING/COHESION/DEPENDENCY/BOUNDARY/SEPARATION/INTERFACE}
- **Modules Involved**: {MODULE_NAMES}
- **Location**: {FILE_PATHS}
- **Severity**: 🔴 Critical / 🟡 High / 🟠 Medium / 🔵 Low
- **Coupling Type**: {CONTENT/COMMON/CONTROL/STAMP/DATA}
- **Cohesion Level**: {COINCIDENTAL/LOGICAL/FUNCTIONAL}
- **Confidence**: High / Medium / Low

## Problem Analysis
- **Current Structure**: How modules are organized now
- **Coupling Issues**: How modules are too tightly coupled
- **Cohesion Issues**: How module lacks focus
- **Impact**: Effect on maintainability, testability, reusability
- **Root Cause**: Why this structure exists

## Refactoring Plan
- **Target Architecture**: Desired module structure
- **Decoupling Strategy**: How to reduce coupling
- **Steps**:
  1. {STEP_1}
  2. {STEP_2}
  3. {STEP_3}
- **Migration Approach**: How to transition safely
- **Testing Strategy**: Ensure behavior preserved

## Code Transformation

### Before (Tightly Coupled)
```{language}
{COUPLED_CODE}
```

**Coupling Issues**:
- {ISSUE_1}
- {ISSUE_2}

**Cohesion Issues**:
- {ISSUE_3}

### After (Modular & Decoupled)
```{language}
{DECOUPLED_CODE}
```

**Improvements**:
- {IMPROVEMENT_1}
- {IMPROVEMENT_2}
- {IMPROVEMENT_3}

### Architecture Diagram
```
[Module A] --> [Interface] <-- [Module B]
   |                              |
   v                              v
[Data A]                      [Data B]
```

### Explanation
- **Decoupling Applied**: {TECHNIQUE}
- **Abstractions Introduced**: {INTERFACES/ABSTRACTIONS}
- **Dependency Direction**: How dependencies now flow
- **Benefits**: Testability, maintainability, reusability improvements

# Output Format

```yaml
modularity_summary:
  total_issues: {NUMBER}
  high_coupling: {NUMBER}
  low_cohesion: {NUMBER}
  circular_dependencies: {NUMBER}
  boundary_violations: {NUMBER}
  estimated_effort: {DAYS/WEEKS}

coupling_metrics:
  average_afferent: {NUMBER}
  average_efferent: {NUMBER}
  average_instability: {0.0-1.0}
  modules_with_high_coupling: {NUMBER}
  circular_dependency_groups: {NUMBER}

cohesion_metrics:
  average_lcom: {NUMBER}
  functionally_cohesive_modules: {PERCENTAGE}
  low_cohesion_modules: {NUMBER}

modularity_issues:
  - type: {CATEGORY}
    modules: [{MODULE_LIST}]
    severity: {CRITICAL/HIGH/MEDIUM/LOW}
    coupling_type: {TYPE}
    cohesion_level: {LEVEL}
    problem: |
      {DESCRIPTION}
    impact:
      maintainability: {HIGH/MEDIUM/LOW}
      testability: {HIGH/MEDIUM/LOW}
      reusability: {HIGH/MEDIUM/LOW}
    refactoring:
      strategy: {STRATEGY_NAME}
      effort: {HOURS/DAYS}
      risk: {LOW/MEDIUM/HIGH}
    code_before: |
      {COUPLED_CODE}
    code_after: |
      {DECOUPLED_CODE}
    architecture_change: |
      {DIAGRAM_OR_DESCRIPTION}

circular_dependencies:
  - cycle: [{MODULE_A}, {MODULE_B}, {MODULE_C}]
    severity: {HIGH/MEDIUM/LOW}
    break_strategy: {STRATEGY}
    effort: {HOURS}

boundary_violations:
  - violation: {DESCRIPTION}
    layers: [{LAYER_A}, {LAYER_B}]
    fix: {SOLUTION}

refactoring_roadmap:
  phase_1_foundation:
    - task: {TASK}
      impact: {HIGH}
      effort: {DAYS}
  phase_2_decoupling:
    - task: {TASK}
      dependencies: [{PHASE_1_TASKS}]
  phase_3_optimization:
    - task: {TASK}

target_architecture:
  layers:
    - name: {LAYER_NAME}
      responsibility: {DESCRIPTION}
      dependencies: [{OTHER_LAYERS}]
  modules:
    - name: {MODULE_NAME}
      cohesion: {FUNCTIONAL/SEQUENTIAL/...}
      coupling: {DATA/STAMP/...}
      public_api: [{METHODS}]

metrics:
  before:
    avg_coupling: {NUMBER}
    avg_cohesion_score: {NUMBER}
    modularity_index: {0-100}
  after:
    avg_coupling: {NUMBER}
    avg_cohesion_score: {NUMBER}
    modularity_index: {0-100}
```

# Quality Checklist

- [ ] All coupling and cohesion issues identified
- [ ] Coupling types accurately classified
- [ ] Circular dependencies detected
- [ ] Boundary violations flagged
- [ ] Refactoring strategies are appropriate
- [ ] Before/after code shows clear improvement
- [ ] Architecture diagrams illustrate changes
- [ ] Metrics quantify improvement
- [ ] Migration approach is safe and incremental
- [ ] Testing strategy ensures behavior preservation

# Meta-Prompting Guidelines

<reasoning_effort>
Use HIGH reasoning effort for modularity analysis requiring deep understanding of software architecture, dependency management, and system design principles.
</reasoning_effort>

<self_reflection>
- Create rubric: coupling/cohesion assessment accuracy, refactoring strategy appropriateness, architectural soundness, metrics validity
- Ensure decoupling doesn't over-complicate
- Verify abstractions are justified
- Check that module boundaries make business sense
</self_reflection>

<exploration>
- Analyze dependency graphs thoroughly
- Understand domain boundaries and contexts
- Research architectural patterns applicable
- Consider team structure (Conway's Law)
- Evaluate deployment and scaling needs
</exploration>
```

## Usage Tips

1. **Visualize Dependencies**: Use dependency graphs to see coupling
2. **Measure Metrics**: Track coupling/cohesion metrics over time
3. **Incremental Decoupling**: Break circular deps first, then reduce coupling
4. **Domain-Driven**: Organize by business domains, not technical layers
5. **Interface First**: Define interfaces before implementation
6. **Test in Isolation**: Each module should be testable independently

## Modularity Principles

- **High Cohesion, Low Coupling**: The fundamental goal
- **Stable Dependencies**: Depend on stable abstractions
- **Acyclic Dependencies**: No circular dependencies
- **Single Responsibility**: Each module has one reason to change
- **Open/Closed**: Open for extension, closed for modification
