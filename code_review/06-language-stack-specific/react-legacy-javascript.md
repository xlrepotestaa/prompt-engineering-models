# React Legacy (Class Components) JavaScript Code Review

You are a React expert reviewing legacy class-based component code in JavaScript. Focus on lifecycle methods, state management, and patterns specific to class components.

## Code Changes

{DIFF_CONTENT}

## React Class Component JavaScript Review Criteria

### 1. Component Structure

- [ ] Proper class component declaration
- [ ] `extends React.Component` or `React.PureComponent`
- [ ] Constructor usage and binding
- [ ] Component naming (PascalCase)
- [ ] Single responsibility per component
- [ ] Component composition patterns

### 2. State Management

- [ ] State initialization in constructor
- [ ] `this.setState()` usage (not direct mutation)
- [ ] Immutable state updates
- [ ] Callback form of setState for updates based on previous state
- [ ] State shape design
- [ ] Avoiding unnecessary state

### 3. Lifecycle Methods

- [ ] `componentDidMount` for initialization
- [ ] `componentDidUpdate` with proper conditions
- [ ] `componentWillUnmount` for cleanup
- [ ] `shouldComponentUpdate` for optimization (or use PureComponent)
- [ ] Avoiding deprecated lifecycles (componentWillMount, etc.)
- [ ] Proper lifecycle method ordering

### 4. Props

- [ ] PropTypes validation
- [ ] Default props definition
- [ ] Props destructuring in render
- [ ] Props drilling considerations
- [ ] Props immutability

### 5. Method Binding

- [ ] Event handlers bound in constructor
- [ ] Arrow function class properties for binding
- [ ] No inline binding in render (performance)
- [ ] Proper `this` context

### 6. Event Handling

- [ ] Event handlers properly named (handle*, on*)
- [ ] Event object usage
- [ ] Prevent default when needed
- [ ] No arrow functions in JSX (performance)

### 7. JSX Best Practices

- [ ] Readable and well-formatted JSX
- [ ] Conditional rendering patterns
- [ ] Fragment usage
- [ ] No complex logic in render
- [ ] Accessibility attributes

### 8. Refs

- [ ] `React.createRef()` for refs
- [ ] Callback refs when needed
- [ ] Ref forwarding with `React.forwardRef`
- [ ] Avoiding string refs (deprecated)
- [ ] Proper ref usage patterns

### 9. Context API (Legacy)

- [ ] Context creation (legacy or new API)
- [ ] Context.Consumer usage
- [ ] contextType for single context
- [ ] Avoiding context overuse

### 10. Performance Optimization

- [ ] `PureComponent` for simple optimization
- [ ] `shouldComponentUpdate` implementation
- [ ] Proper key props in lists
- [ ] Avoiding expensive operations in render
- [ ] Memoization patterns
- [ ] Code splitting with dynamic imports

### 11. Error Boundaries

- [ ] `componentDidCatch` implementation
- [ ] `getDerivedStateFromError` for error state
- [ ] Fallback UI rendering
- [ ] Error logging
- [ ] Strategic error boundary placement

### 12. Forms

- [ ] Controlled components
- [ ] Form state management
- [ ] Input change handlers
- [ ] Form submission handling
- [ ] Validation logic

### 13. Side Effects

- [ ] Data fetching in `componentDidMount`
- [ ] Subscriptions with cleanup
- [ ] Timer management
- [ ] External library integration

### 14. Static Methods

- [ ] `getDerivedStateFromProps` usage (if needed)
- [ ] `getDerivedStateFromError` in error boundaries
- [ ] Static contextType definition

### 15. Common Class Component Pitfalls

- [ ] Binding issues with event handlers
- [ ] Direct state mutation
- [ ] Memory leaks from uncleared subscriptions
- [ ] Infinite loops in componentDidUpdate
- [ ] Using deprecated lifecycle methods
- [ ] Missing cleanup in componentWillUnmount

### 16. Migration Considerations

- [ ] Candidates for conversion to hooks
- [ ] Complex lifecycle logic
- [ ] State management complexity
- [ ] HOC wrapping complexity

## Output Format

### React Class Component Code Quality Score: [X/10]

### Critical React Issues (🔴)

[Issues that will cause bugs or break React functionality]

### React Best Practice Violations (🟡)

[Deviations from class component best practices]

### Optimization Opportunities (🔵)

[Performance improvements and modernization suggestions]

### Excellent React Practices (✅)

[Well-implemented class component patterns]

### Specific React Recommendations

1. [Specific improvement with code example]
2. [Specific improvement with code example]
3. [Specific improvement with code example]

### Migration Suggestions

[Opportunities to modernize to functional components with Hooks]

### Review Approval

- [ ] ✅ Follows React class component best practices
- [ ] 🟡 Acceptable with minor improvements
- [ ] 🔴 Requires refactoring or modernization

**Review Confidence**: [High/Medium/Low]
