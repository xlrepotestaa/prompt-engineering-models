# Comprehensive Refactoring Strategy

## Prompt Template

```md
# Role and Context
You are an expert software architect specializing in comprehensive code refactoring. Your mission is to analyze code holistically across all quality dimensions and provide an integrated refactoring strategy that addresses multiple concerns simultaneously while maintaining code stability.

# Code to Analyze
- **Project**: {PROJECT_NAME}
- **Files/Modules**: {FILE_PATHS}
- **Language**: {PROGRAMMING_LANGUAGE}
- **Framework**: {FRAMEWORK}
- **Codebase Size**: {LOC_COUNT} lines
- **Team Size**: {TEAM_SIZE}
- **Timeline**: {AVAILABLE_TIMEFRAME}

# Code Content
{CODE_CONTENT}

# Current Metrics (if available)
- **Test Coverage**: {COVERAGE_PERCENTAGE}%
- **Cyclomatic Complexity**: {AVG_COMPLEXITY}
- **Technical Debt Ratio**: {DEBT_RATIO}%
- **Performance Baseline**: {PERFORMANCE_METRICS}
- **Security Score**: {SECURITY_SCORE}

# Analysis Instructions
Conduct a holistic refactoring analysis integrating multiple quality dimensions:

## 1. **Multi-Dimensional Assessment**

### Quality Dimensions to Evaluate:
- **Code Smells**: Long methods, god classes, duplication, coupling
- **Architecture**: SOLID violations, design pattern opportunities
- **Performance**: Algorithmic inefficiencies, resource waste
- **Security**: Vulnerabilities, OWASP compliance gaps
- **Testability**: Hard-to-test code, missing test coverage
- **Readability**: Poor naming, confusing structure
- **Modularity**: High coupling, low cohesion
- **Modernization**: Outdated patterns, deprecated APIs
- **Technical Debt**: Accumulated shortcuts and workarounds

### Cross-Cutting Concerns:
- **Dependencies**: How different quality issues interact
- **Priorities**: Which issues block progress on others
- **Synergies**: Refactorings that solve multiple problems
- **Risks**: Changes that could introduce new issues
- **ROI**: Impact vs. effort for each refactoring

## 2. **Integrated Analysis Approach**

### Phase 1: Discovery
- Map all quality issues across dimensions
- Identify root causes vs. symptoms
- Find patterns in code problems
- Assess current state comprehensively
- Establish baseline metrics

### Phase 2: Dependency Analysis
- Determine which issues must be fixed first
- Identify blocking relationships
- Find refactorings with cascading benefits
- Assess risk interdependencies
- Map refactoring prerequisites

### Phase 3: Strategy Formulation
- Group related refactorings into themes
- Sequence refactorings for safety and efficiency
- Identify quick wins for early momentum
- Plan for continuous validation
- Balance short-term and long-term goals

### Phase 4: Implementation Planning
- Break down into manageable increments
- Define success criteria for each phase
- Establish rollback strategies
- Plan testing and validation approach
- Allocate resources and timeline

## 3. **Refactoring Dimensions Integration**

### Code Quality + Architecture:
- Extract classes to fix both god classes and SRP violations
- Apply design patterns while eliminating code smells
- Improve coupling while enhancing readability

### Performance + Testability:
- Optimize algorithms while making code testable
- Extract performance-critical code into testable units
- Mock expensive operations for faster tests

### Security + Modularity:
- Isolate security concerns into dedicated modules
- Apply principle of least privilege through decoupling
- Centralize validation and sanitization

### Modernization + Readability:
- Update syntax while improving clarity
- Replace verbose patterns with modern idioms
- Enhance type safety and naming together

## 4. **Refactoring Strategies**

### Strategy 1: Bottom-Up (Foundation First)
```text
1. Fix code smells at method/class level
2. Improve testability and add tests
3. Apply SOLID principles
4. Introduce design patterns
5. Optimize performance
6. Harden security
7. Modernize codebase
```

### Strategy 2: Top-Down (Architecture First)
```text
1. Define target architecture
2. Establish module boundaries
3. Apply design patterns strategically
4. Refactor modules incrementally
5. Improve code quality within modules
6. Optimize and secure
7. Modernize implementation
```

### Strategy 3: Risk-Based (Critical Path First)
```text
1. Fix critical security vulnerabilities
2. Address performance bottlenecks
3. Reduce high-impact technical debt
4. Improve testability of critical paths
5. Refactor high-change areas
6. Apply patterns to stable areas
7. Modernize low-risk components
```

### Strategy 4: Value-Based (ROI First)
```text
1. Implement quick wins (high impact, low effort)
2. Address blocking technical debt
3. Improve most-changed code areas
4. Optimize user-facing performance
5. Enhance developer productivity areas
6. Refactor for future feature velocity
7. Polish and modernize
```

### Strategy 5: Incremental (Continuous Improvement)
```text
1. Allocate 20% time for refactoring
2. Apply boy scout rule (leave better than found)
3. Refactor during feature development
4. Address issues as they cause friction
5. Continuously improve metrics
6. Iterate based on feedback
```

## 5. **Comprehensive Refactoring Plan**

### Assessment Summary
- **Overall Code Quality Score**: {0-100}
- **Primary Issues**: {TOP_3_ISSUE_CATEGORIES}
- **Root Causes**: {SYSTEMIC_PROBLEMS}
- **Blocking Factors**: {WHAT_PREVENTS_IMPROVEMENT}
- **Recommended Strategy**: {STRATEGY_NAME}

### Refactoring Roadmap
Provide a phased, integrated refactoring plan:

#### Phase 0: Preparation (Week 1-2)
- Increase test coverage to {TARGET}%
- Set up refactoring tools and CI checks
- Establish baseline metrics
- Create rollback procedures
- Document current architecture

#### Phase 1: Foundation (Week 3-6)
**Priority Refactorings**:
- {REFACTORING_1} - Addresses: {DIMENSIONS}
- {REFACTORING_2} - Addresses: {DIMENSIONS}
- {REFACTORING_3} - Addresses: {DIMENSIONS}

**Expected Outcomes**:
- Quality improvement: {METRICS}
- Enabled refactorings: {WHAT_THIS_UNBLOCKS}

#### Phase 2: Core Improvements (Week 7-12)
**Priority Refactorings**:
- {REFACTORING_4} - Addresses: {DIMENSIONS}
- {REFACTORING_5} - Addresses: {DIMENSIONS}
- {REFACTORING_6} - Addresses: {DIMENSIONS}

**Expected Outcomes**:
- Quality improvement: {METRICS}
- Business value: {IMPACT}

#### Phase 3: Optimization (Week 13-16)
**Priority Refactorings**:
- {REFACTORING_7} - Addresses: {DIMENSIONS}
- {REFACTORING_8} - Addresses: {DIMENSIONS}

**Expected Outcomes**:
- Quality improvement: {METRICS}
- Long-term benefits: {IMPACT}

#### Phase 4: Polish & Modernization (Week 17-20)
**Priority Refactorings**:
- {REFACTORING_9} - Addresses: {DIMENSIONS}
- {REFACTORING_10} - Addresses: {DIMENSIONS}

**Expected Outcomes**:
- Final quality state: {METRICS}
- Team velocity improvement: {PERCENTAGE}

### Continuous Validation
- Run full test suite after each refactoring
- Track metrics after each phase
- Conduct code reviews for all changes
- Monitor production performance
- Gather team feedback

## 6. **Integration Points**

### With Existing Workflows:
- **Code Reviews**: Apply refactorings during PR review
- **Feature Development**: Refactor code touched by new features
- **Bug Fixes**: Improve code while fixing bugs
- **Sprint Planning**: Allocate refactoring capacity
- **Retrospectives**: Identify refactoring opportunities

### With Other Prompts:
- **Code Review Prompts**: Identify issues needing refactoring
- **Specific Refactoring Prompts**: Deep dive into dimensions
- **Testing Prompts**: Ensure adequate test coverage
- **Documentation Prompts**: Update docs post-refactoring

# Output Format

```yaml
comprehensive_assessment:
  overall_score: {0-100}
  dimensions:
    code_smells: {SCORE}
    architecture: {SCORE}
    performance: {SCORE}
    security: {SCORE}
    testability: {SCORE}
    readability: {SCORE}
    modularity: {SCORE}
    modernization: {SCORE}
    technical_debt: {SCORE}
  
  critical_issues:
    - issue: {ISSUE_DESCRIPTION}
      dimensions_affected: [{DIMENSIONS}]
      severity: {CRITICAL/HIGH/MEDIUM/LOW}
      impact: |
        {IMPACT_DESCRIPTION}
  
  root_causes:
    - cause: {ROOT_CAUSE}
      manifestations: [{SYMPTOMS}]
      fix_strategy: {STRATEGY}

refactoring_strategy:
  recommended_approach: {STRATEGY_NAME}
  rationale: |
    {WHY_THIS_STRATEGY}
  
  phases:
    - phase: {PHASE_NAME}
      duration: {WEEKS}
      refactorings:
        - name: {REFACTORING}
          dimensions: [{DIMENSIONS_ADDRESSED}]
          priority: {1-10}
          effort: {HOURS/DAYS}
          impact: {HIGH/MEDIUM/LOW}
          dependencies: [{PREREQUISITES}]
          risks: [{RISKS}]
          expected_outcomes:
            metrics: {METRIC_IMPROVEMENTS}
            enables: [{FUTURE_REFACTORINGS}]
      
      success_criteria:
        - {CRITERION_1}
        - {CRITERION_2}
      
      validation:
        - {VALIDATION_STEP_1}
        - {VALIDATION_STEP_2}

integrated_refactorings:
  - refactoring_group: {GROUP_NAME}
    description: |
      {WHAT_THIS_GROUP_ACHIEVES}
    refactorings:
      - {REFACTORING_1}
      - {REFACTORING_2}
      - {REFACTORING_3}
    combined_benefits:
      - {SYNERGY_1}
      - {SYNERGY_2}
    dimensions_improved: [{DIMENSIONS}]

dependencies:
  blocking_issues:
    - issue: {ISSUE}
      blocks: [{REFACTORINGS}]
      must_fix_first: {YES/NO}
  
  enabling_refactorings:
    - refactoring: {REFACTORING}
      enables: [{FUTURE_REFACTORINGS}]
      priority: {HIGH/MEDIUM/LOW}

quick_wins:
  - refactoring: {REFACTORING}
    effort: {HOURS}
    impact: {IMPACT_DESCRIPTION}
    dimensions: [{DIMENSIONS}]
    roi: {RATIO}

metrics_tracking:
  baseline:
    code_quality: {SCORE}
    test_coverage: {PERCENTAGE}
    performance: {METRICS}
    security: {SCORE}
    tech_debt_ratio: {PERCENTAGE}
  
  targets:
    phase_1: {METRICS}
    phase_2: {METRICS}
    phase_3: {METRICS}
    final: {METRICS}
  
  tracking_frequency: {WEEKLY/BIWEEKLY/MONTHLY}

risk_mitigation:
  high_risk_refactorings:
    - refactoring: {REFACTORING}
      risk: {RISK_DESCRIPTION}
      mitigation: {MITIGATION_STRATEGY}
      rollback_plan: {ROLLBACK_STEPS}
  
  validation_strategy:
    - {VALIDATION_APPROACH_1}
    - {VALIDATION_APPROACH_2}

resource_allocation:
  total_effort: {HOURS/DAYS/WEEKS}
  team_capacity: {PERCENTAGE}
  timeline: {WEEKS/MONTHS}
  parallel_work_streams: {NUMBER}
```

# Quality Checklist

- [ ] All quality dimensions assessed comprehensively
- [ ] Root causes identified beyond symptoms
- [ ] Refactorings prioritized by dependencies and ROI
- [ ] Integrated strategy addresses multiple dimensions
- [ ] Phases are realistic and achievable
- [ ] Success criteria are measurable
- [ ] Risks are identified with mitigation plans
- [ ] Quick wins identified for early momentum
- [ ] Metrics tracking plan established
- [ ] Resource allocation is realistic
- [ ] Strategy aligns with business goals
- [ ] Team capacity and skills considered

# Meta-Prompting Guidelines

<reasoning_effort>
Use VERY HIGH reasoning effort for comprehensive refactoring requiring deep analysis across multiple dimensions, complex dependency resolution, and strategic planning.
</reasoning_effort>

<self_reflection>
- Create rubric: assessment completeness, strategy appropriateness, dependency analysis accuracy, risk assessment thoroughness, ROI calculation validity, timeline realism
- Ensure strategy is pragmatic and achievable
- Verify that phases build on each other logically
- Check that all dimensions are integrated, not siloed
- Validate that quick wins are truly quick and impactful
</self_reflection>

<exploration>
- Analyze all code quality dimensions systematically
- Identify patterns and root causes across issues
- Consider team capacity and organizational constraints
- Research industry benchmarks and best practices
- Evaluate tool support for refactoring activities
</exploration>

<persistence>
- Provide complete, actionable roadmap
- Don't skip difficult refactorings
- Address all quality dimensions
- Include realistic timeline estimates
- Plan for continuous improvement
</persistence>
```

## Usage Tips

1. **Start Holistic**: Assess all dimensions before focusing on one
2. **Find Synergies**: Look for refactorings that solve multiple problems
3. **Sequence Wisely**: Fix blocking issues before dependent ones
4. **Validate Continuously**: Test after each change, measure after each phase
5. **Stay Flexible**: Adjust strategy based on results and feedback
6. **Celebrate Progress**: Recognize improvements to maintain momentum

## Comprehensive Refactoring Benefits

- **Integrated Approach**: Addresses multiple quality dimensions simultaneously
- **Strategic Planning**: Sequences refactorings for maximum effectiveness
- **Risk Mitigation**: Plans for validation and rollback at every step
- **Team Alignment**: Clear roadmap and success criteria for everyone
- **Measurable Progress**: Concrete metrics to track improvement
- **Sustainable Improvement**: Builds foundation for continuous enhancement

## When to Use This Prompt

- **Major Refactoring Initiative**: Planning comprehensive codebase improvement
- **Technical Debt Crisis**: Need strategic approach to reduce significant debt
- **Team Onboarding**: New team needs roadmap for code improvement
- **Pre-Major Release**: Comprehensive cleanup before big launch
- **Architecture Evolution**: Systematic transformation of codebase
- **Quality Improvement Program**: Establishing sustainable quality practices
