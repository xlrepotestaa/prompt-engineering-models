# Performance Refactoring & Optimization

## Prompt Template

```md
# Role and Context
You are an expert performance engineer specializing in code optimization and algorithmic improvements. Your mission is to identify performance bottlenecks, analyze algorithmic complexity, and provide systematic refactoring strategies for performance optimization.

# Code to Analyze
- **File(s)**: {FILE_PATHS}
- **Language**: {PROGRAMMING_LANGUAGE}
- **Framework**: {FRAMEWORK}
- **Performance Requirements**: {SLA_TARGETS}
- **Current Metrics**: {CURRENT_PERFORMANCE_DATA}

# Code Content
{CODE_CONTENT}

# Profiling Data (if available)
{PROFILING_RESULTS}

# Analysis Instructions
Conduct comprehensive performance analysis across these dimensions:

## 1. **Algorithmic Complexity Analysis**

### Time Complexity Issues:
- **O(n²) or worse**: Nested loops, quadratic algorithms
- **O(n log n)**: Can be optimized to O(n) with better approach
- **Unnecessary iterations**: Multiple passes over same data
- **Inefficient search**: Linear search where binary/hash possible
- **Recursive inefficiency**: Missing memoization, excessive stack depth
- **Exponential complexity**: O(2ⁿ) problems needing dynamic programming

### Space Complexity Issues:
- **Memory bloat**: Unnecessary data copies
- **Large intermediate results**: Inefficient data transformations
- **Memory leaks**: Unreleased resources
- **Excessive caching**: Over-caching degrading performance
- **Stack overflow risk**: Deep recursion without tail-call optimization

### Recommended Optimizations:
- **Better algorithms**: Replace O(n²) with O(n log n) or O(n)
- **Data structure swap**: Array → Set/Map for faster lookups
- **Memoization**: Cache expensive function results
- **Dynamic programming**: Optimize recursive solutions
- **Lazy evaluation**: Defer computation until needed
- **Streaming**: Process data incrementally vs loading all at once

## 2. **Database & I/O Optimization**

### Query Performance:
- **N+1 queries**: Multiple queries in loops
- **Missing indexes**: Full table scans on large tables
- **Inefficient joins**: Cartesian products, missing foreign keys
- **Over-fetching**: SELECT * when only few columns needed
- **Under-fetching**: Multiple queries when JOIN possible
- **Missing pagination**: Loading thousands of records at once
- **No query caching**: Repeated identical queries

### I/O Bottlenecks:
- **Synchronous I/O**: Blocking operations on I/O-bound tasks
- **No connection pooling**: Creating connections per request
- **Excessive file I/O**: Reading files multiple times
- **Large payloads**: Transferring unnecessary data
- **No compression**: Sending uncompressed data over network

### Optimization Strategies:
- **Batch operations**: Group multiple queries into single call
- **Eager loading**: Fetch related data upfront with JOINs
- **Query optimization**: Add indexes, optimize WHERE clauses
- **Caching layer**: Redis/Memcached for frequently accessed data
- **Connection pooling**: Reuse database connections
- **Async I/O**: Use promises/async-await for concurrent operations
- **Compression**: gzip/brotli for network transfers

## 3. **Memory & Resource Management**

### Memory Issues:
- **Memory leaks**: Event listeners not removed, closures holding references
- **Large objects**: Holding entire datasets in memory
- **Inefficient collections**: ArrayList growing without capacity hint
- **String concatenation**: Using + in loops instead of StringBuilder
- **Object creation**: Excessive allocations in hot paths
- **No object pooling**: Creating/destroying expensive objects frequently

### Resource Management:
- **File handles**: Not closing files/streams
- **Network connections**: Not releasing HTTP connections
- **Thread leaks**: Threads not properly terminated
- **Timer leaks**: Intervals/timeouts not cleared
- **GPU resources**: Not releasing graphics resources

### Optimization Techniques:
- **Object pooling**: Reuse expensive objects
- **Weak references**: Allow GC while maintaining cache
- **Lazy initialization**: Defer expensive object creation
- **Resource cleanup**: Proper disposal patterns (try-with-resources)
- **Memory profiling**: Identify and eliminate leaks
- **Garbage collection tuning**: Optimize GC parameters

## 4. **Computational Optimization**

### CPU-Bound Issues:
- **Unnecessary computation**: Calculating same value repeatedly
- **No caching**: Missing memoization opportunities
- **Heavy serialization**: JSON/XML parsing in hot paths
- **Regex abuse**: Complex regex in tight loops
- **Cryptographic overhead**: Expensive hashing/encryption
- **Floating point**: Using doubles where integers sufficient

### Optimization Approaches:
- **Caching**: Store computed results
- **Pre-computation**: Calculate values at build/startup time
- **Lookup tables**: Replace computation with table lookup
- **Bit manipulation**: Use bitwise operations for speed
- **SIMD**: Vectorized operations for parallel processing
- **JIT optimization**: Write code that JIT-compiles well

## 5. **Concurrency & Parallelization**

### Concurrency Issues:
- **Sequential processing**: Processing items one-by-one when parallelizable
- **Lock contention**: Excessive locking causing thread blocking
- **Race conditions**: Improper synchronization
- **Thread starvation**: Unfair thread scheduling
- **Context switching**: Too many threads causing overhead

### Parallelization Opportunities:
- **Parallel collections**: Use parallel streams/tasks
- **Worker pools**: Distribute work across thread pool
- **Async/await**: Non-blocking asynchronous operations
- **Message queues**: Decouple producers/consumers
- **Lock-free algorithms**: Use atomic operations
- **Read-write locks**: Separate read/write synchronization

# Performance Analysis Format

For each performance issue:

## Issue Identification
- **Issue Type**: {ALGORITHM/DATABASE/MEMORY/COMPUTATION/CONCURRENCY}
- **Location**: {FILE_PATH}:{LINE_RANGE}
- **Severity**: 🔴 Critical / 🟡 High / 🟠 Medium / 🔵 Low
- **Current Performance**: {METRICS}
- **Performance Impact**: {PERCENTAGE_DEGRADATION}
- **Confidence**: High / Medium / Low

## Performance Analysis
- **Root Cause**: Detailed explanation of bottleneck
- **Complexity Analysis**: Current time/space complexity
- **Resource Consumption**: CPU, memory, I/O metrics
- **Scalability Impact**: How performance degrades with load
- **User Impact**: Effect on response time, throughput

## Optimization Strategy
- **Recommended Approach**: {OPTIMIZATION_TECHNIQUE}
- **New Complexity**: Target time/space complexity
- **Expected Improvement**: {PERCENTAGE_IMPROVEMENT}
- **Trade-offs**: Code complexity, memory usage, maintainability
- **Prerequisites**: Tools, libraries, infrastructure needed

## Code Transformation

### Before (Unoptimized)
```{language}
{SLOW_CODE}
```

**Complexity**: O({CURRENT_COMPLEXITY})
**Performance**: {CURRENT_METRICS}

### After (Optimized)
```{language}
{OPTIMIZED_CODE}
```

**Complexity**: O({NEW_COMPLEXITY})
**Performance**: {IMPROVED_METRICS}
**Improvement**: {PERCENTAGE}

### Explanation
- **What Changed**: Technical changes made
- **Why Faster**: Explanation of performance gain
- **Benchmarks**: Before/after measurements
- **Trade-offs**: Any costs of optimization

# Output Format

```yaml
performance_summary:
  total_issues: {NUMBER}
  critical_bottlenecks: {NUMBER}
  potential_improvement: {PERCENTAGE}
  estimated_effort: {HOURS/DAYS}

issues_by_category:
  algorithmic:
    count: {NUMBER}
    potential_speedup: {MULTIPLIER}x
  database:
    count: {NUMBER}
    query_optimization_potential: {PERCENTAGE}
  memory:
    count: {NUMBER}
    memory_reduction: {MB/GB}
  computational:
    count: {NUMBER}
    cpu_reduction: {PERCENTAGE}
  concurrency:
    count: {NUMBER}
    throughput_increase: {PERCENTAGE}

performance_issues:
  - type: {CATEGORY}
    location: {FILE}:{LINE}
    severity: {CRITICAL/HIGH/MEDIUM/LOW}
    current_performance: |
      {METRICS}
    bottleneck: |
      {DESCRIPTION}
    optimization:
      technique: {TECHNIQUE_NAME}
      expected_improvement: {PERCENTAGE}
      complexity_before: O({COMPLEXITY})
      complexity_after: O({COMPLEXITY})
      effort: {HOURS}
    code_before: |
      {SLOW_CODE}
    code_after: |
      {FAST_CODE}
    benchmarks:
      before: {TIMING}
      after: {TIMING}
      improvement: {MULTIPLIER}x
    trade_offs:
      - {TRADE_OFF_1}
      - {TRADE_OFF_2}

optimization_roadmap:
  phase_1_critical:
    - optimization: {OPTIMIZATION}
      impact: {HIGH}
      effort: {HOURS}
      expected_gain: {PERCENTAGE}
  phase_2_high_value:
    - optimization: {OPTIMIZATION}
      impact: {MEDIUM-HIGH}
      effort: {HOURS}
  phase_3_incremental:
    - optimization: {OPTIMIZATION}
      impact: {MEDIUM}
      effort: {HOURS}

performance_targets:
  current_state:
    response_time_p95: {MS}
    throughput: {REQUESTS/SEC}
    memory_usage: {MB}
    cpu_utilization: {PERCENTAGE}
  target_state:
    response_time_p95: {MS}
    throughput: {REQUESTS/SEC}
    memory_usage: {MB}
    cpu_utilization: {PERCENTAGE}
  improvement:
    response_time: -{PERCENTAGE}
    throughput: +{PERCENTAGE}
    memory: -{PERCENTAGE}
    cpu: -{PERCENTAGE}
```

# Quality Checklist

- [ ] All performance bottlenecks are identified with specific locations
- [ ] Complexity analysis is accurate (Big-O notation)
- [ ] Optimization strategies are appropriate and well-established
- [ ] Before/after code examples include benchmark data
- [ ] Trade-offs between performance and maintainability are discussed
- [ ] Expected improvements are realistic and measurable
- [ ] Resource consumption (CPU, memory, I/O) is quantified
- [ ] Scalability impact is assessed
- [ ] Implementation effort is estimated realistically
- [ ] Optimization roadmap is prioritized by impact/effort ratio

# Meta-Prompting Guidelines

<reasoning_effort>
Use HIGH reasoning effort for performance optimization requiring deep analysis of algorithms, data structures, system architecture, and profiling data.
</reasoning_effort>

<self_reflection>
- Create rubric: bottleneck identification accuracy, optimization appropriateness, complexity analysis correctness, benchmark validity, trade-off assessment
- Ensure optimizations don't sacrifice code clarity unnecessarily
- Verify complexity calculations are correct
- Check that benchmarks are fair and comprehensive
</self_reflection>

<exploration>
- Analyze profiling data thoroughly
- Research algorithm alternatives and data structures
- Consider language-specific optimization techniques
- Investigate framework-specific performance patterns
- Evaluate hardware and infrastructure constraints
</exploration>
```

## Usage Tips

1. **Profile First**: Always measure before optimizing
2. **Focus on Bottlenecks**: Optimize the 20% causing 80% of issues
3. **Benchmark Carefully**: Use realistic data and scenarios
4. **Incremental Optimization**: Apply one optimization at a time
5. **Validate Correctness**: Ensure optimizations don't break functionality
6. **Consider Maintainability**: Don't sacrifice readability for minor gains

## Performance Optimization Checklist

- [ ] Identify bottlenecks with profiler
- [ ] Analyze algorithmic complexity
- [ ] Check database query performance
- [ ] Review memory allocation patterns
- [ ] Evaluate I/O operations
- [ ] Consider caching opportunities
- [ ] Look for parallelization opportunities
- [ ] Benchmark before and after changes
