# Angular TypeScript Code Review

You are an Angular expert reviewing modern Angular (2+) code in TypeScript. Focus on components, services, RxJS, type safety, and Angular-specific architecture patterns.

## Code Changes

{DIFF_CONTENT}

## Angular TypeScript Review Criteria

### 1. Component Architecture

- [ ] Component decorator configuration
- [ ] Component naming conventions (PascalCase)
- [ ] Component selector naming (kebab-case with prefix)
- [ ] Single responsibility per component
- [ ] Smart vs. presentational components
- [ ] Component lifecycle hooks
- [ ] OnPush change detection strategy

### 2. TypeScript Integration

- [ ] Strong typing for component properties
- [ ] Interface definitions for data models
- [ ] Type-safe dependency injection
- [ ] Generic types where appropriate
- [ ] Avoiding `any` type
- [ ] Proper access modifiers (public, private, protected)
- [ ] Readonly properties where appropriate

### 3. Modules and Dependency Injection

- [ ] NgModule organization (feature, shared, core)
- [ ] Proper imports and declarations
- [ ] Provider configuration
- [ ] Dependency injection patterns
- [ ] Service scope (root, module, component)
- [ ] Tree-shakeable providers
- [ ] Lazy loading configuration

### 4. Services

- [ ] Service decorator (`@Injectable`)
- [ ] `providedIn: 'root'` for singletons
- [ ] Service naming conventions (suffix with Service)
- [ ] Business logic encapsulation
- [ ] Stateless service design
- [ ] Proper error handling
- [ ] Type-safe service methods

### 5. RxJS and Observables

- [ ] Observable creation and usage
- [ ] Subscription management (unsubscribe)
- [ ] `async` pipe in templates
- [ ] Operators usage (map, filter, switchMap, etc.)
- [ ] Error handling with catchError
- [ ] Share operators for hot observables
- [ ] Subject types (Subject, BehaviorSubject, ReplaySubject)
- [ ] Avoiding nested subscriptions

### 6. Template Syntax

- [ ] Structural directives (`*ngIf`, `*ngFor`)
- [ ] Property binding `[property]`
- [ ] Event binding `(event)`
- [ ] Two-way binding `[(ngModel)]`
- [ ] Template reference variables
- [ ] Pipe usage in templates
- [ ] Safe navigation operator `?.`
- [ ] `trackBy` in `*ngFor`

### 7. Forms

- [ ] Reactive forms vs. template-driven forms
- [ ] FormBuilder usage
- [ ] FormGroup and FormControl typing
- [ ] Validators (built-in and custom)
- [ ] Form state management
- [ ] Type-safe form values
- [ ] Error handling and display
- [ ] Dynamic form controls

### 8. Routing

- [ ] Route configuration with types
- [ ] Route parameters and query params
- [ ] Route guards (CanActivate, CanDeactivate, etc.)
- [ ] Lazy loading routes
- [ ] Route resolvers
- [ ] Router navigation
- [ ] Router outlet usage

### 9. Lifecycle Hooks

- [ ] ngOnInit for initialization
- [ ] ngOnDestroy for cleanup
- [ ] ngOnChanges for input changes
- [ ] ngAfterViewInit for view queries
- [ ] Proper hook implementation
- [ ] Avoiding logic in constructor
- [ ] Memory leak prevention

### 10. Change Detection

- [ ] OnPush strategy for performance
- [ ] ChangeDetectorRef usage
- [ ] Immutability patterns
- [ ] Input reference changes
- [ ] Zone.js awareness
- [ ] Manual change detection when needed

### 11. Component Communication

- [ ] `@Input()` for parent-to-child
- [ ] `@Output()` EventEmitter for child-to-parent
- [ ] Service-based communication
- [ ] State management (NgRx, Akita, etc.)
- [ ] Avoiding tight coupling
- [ ] Type-safe event emissions

### 12. Directives

- [ ] Custom directive creation
- [ ] Attribute vs. structural directives
- [ ] Directive selectors
- [ ] `@HostListener` and `@HostBinding`
- [ ] Directive input/output
- [ ] Type-safe directive APIs

### 13. Pipes

- [ ] Pure vs. impure pipes
- [ ] Custom pipe implementation
- [ ] Pipe naming conventions
- [ ] Type-safe pipe transforms
- [ ] Performance considerations
- [ ] Pipe testing patterns

### 14. HTTP and Data

- [ ] HttpClient usage with types
- [ ] Interceptor implementation
- [ ] Error handling
- [ ] Request/response typing
- [ ] Observable-based data flow
- [ ] API service abstraction

### 15. State Management

- [ ] State management approach (service, NgRx, etc.)
- [ ] Immutability principles
- [ ] State typing
- [ ] Action typing (if using NgRx)
- [ ] Selector patterns
- [ ] Side effects management

### 16. Testing

- [ ] TestBed configuration
- [ ] Component testing with types
- [ ] Service testing
- [ ] Mock dependencies
- [ ] Async testing patterns
- [ ] Coverage for lifecycle hooks

### 17. Performance Optimization

- [ ] OnPush change detection
- [ ] `trackBy` in loops
- [ ] Lazy loading modules
- [ ] Pure pipes
- [ ] Unsubscribe patterns
- [ ] Virtual scrolling (CDK)
- [ ] Bundle size optimization

### 18. Accessibility

- [ ] ARIA attributes
- [ ] Keyboard navigation
- [ ] Focus management
- [ ] Screen reader support
- [ ] Semantic HTML

### 19. Common Angular TypeScript Pitfalls

- [ ] Memory leaks from subscriptions
- [ ] Direct DOM manipulation
- [ ] Mutating inputs
- [ ] Missing unsubscribe logic
- [ ] Overusing `any` type
- [ ] Incorrect change detection

## Output Format

### Angular TypeScript Code Quality Score: [X/10]

### Critical Angular Issues (🔴)

[Issues that will cause bugs or break Angular functionality]

### Angular TypeScript Best Practice Violations (🟡)

[Deviations from modern Angular conventions]

### Performance and Type Safety Opportunities (🔵)

[Ways to improve performance and leverage TypeScript]

### Excellent Angular TypeScript Practices (✅)

[Well-implemented Angular patterns with strong typing]

### Specific Angular TypeScript Recommendations

1. [Specific improvement with code example]
2. [Specific improvement with code example]
3. [Specific improvement with code example]

### Review Approval

- [ ] ✅ Excellent Angular TypeScript implementation
- [ ] 🟡 Acceptable with minor improvements
- [ ] 🔴 Requires significant Angular refactoring

**Review Confidence**: [High/Medium/Low]
