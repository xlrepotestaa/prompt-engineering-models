# React-Specific Refactoring

You are a React expert specializing in React refactoring patterns. Focus on modern React patterns, Hooks migration, performance optimization, and component design.

## Code to Refactor

{CODE_CONTENT}

## React Refactoring Patterns

### 1. Class Components → Functional Components with Hooks

**Basic Conversion**:
```jsx
// Before (Class)
class Counter extends React.Component {
    constructor(props) {
        super(props);
        this.state = { count: 0 };
    }
    
    increment = () => {
        this.setState(prev => ({ count: prev.count + 1 }));
    }
    
    render() {
        return (
            <div>
                <p>Count: {this.state.count}</p>
                <button onClick={this.increment}>Increment</button>
            </div>
        );
    }
}

// After (Functional with Hooks)
function Counter() {
    const [count, setCount] = useState(0);
    
    const increment = () => {
        setCount(prev => prev + 1);
    };
    
    return (
        <div>
            <p>Count: {count}</p>
            <button onClick={increment}>Increment</button>
        </div>
    );
}
```

**Lifecycle Methods → useEffect**:
```jsx
// Before (Class)
class DataFetcher extends React.Component {
    componentDidMount() {
        this.fetchData();
    }
    
    componentDidUpdate(prevProps) {
        if (prevProps.userId !== this.props.userId) {
            this.fetchData();
        }
    }
    
    componentWillUnmount() {
        this.cancelRequests();
    }
    
    fetchData() { /* ... */ }
    cancelRequests() { /* ... */ }
}

// After (Functional with Hooks)
function DataFetcher({ userId }) {
    useEffect(() => {
        fetchData();
        return () => cancelRequests();
    }, [userId]);
    
    const fetchData = () => { /* ... */ };
    const cancelRequests = () => { /* ... */ };
}
```

### 2. Custom Hooks for Logic Reuse

**Extract Logic to Custom Hook**:
```jsx
// Before (Duplicated Logic)
function UserProfile() {
    const [user, setUser] = useState(null);
    const [loading, setLoading] = useState(true);
    
    useEffect(() => {
        fetch('/api/user')
            .then(res => res.json())
            .then(data => {
                setUser(data);
                setLoading(false);
            });
    }, []);
    
    if (loading) return <div>Loading...</div>;
    return <div>{user.name}</div>;
}

// After (Custom Hook)
function useUser() {
    const [user, setUser] = useState(null);
    const [loading, setLoading] = useState(true);
    const [error, setError] = useState(null);
    
    useEffect(() => {
        fetch('/api/user')
            .then(res => res.json())
            .then(data => {
                setUser(data);
                setLoading(false);
            })
            .catch(err => {
                setError(err);
                setLoading(false);
            });
    }, []);
    
    return { user, loading, error };
}

function UserProfile() {
    const { user, loading, error } = useUser();
    
    if (loading) return <div>Loading...</div>;
    if (error) return <div>Error: {error.message}</div>;
    return <div>{user.name}</div>;
}
```

### 3. Performance Optimization

**useMemo for Expensive Calculations**:
```jsx
// Before
function ProductList({ products, filter }) {
    const filteredProducts = products.filter(p => 
        p.name.toLowerCase().includes(filter.toLowerCase())
    );
    
    return <div>{filteredProducts.map(renderProduct)}</div>;
}

// After
function ProductList({ products, filter }) {
    const filteredProducts = useMemo(() => 
        products.filter(p => 
            p.name.toLowerCase().includes(filter.toLowerCase())
        ),
        [products, filter]
    );
    
    return <div>{filteredProducts.map(renderProduct)}</div>;
}
```

**useCallback for Stable Function References**:
```jsx
// Before
function Parent() {
    const [count, setCount] = useState(0);
    
    const handleClick = () => {
        console.log('Clicked');
    };
    
    return <ChildComponent onClick={handleClick} />;
}

// After
function Parent() {
    const [count, setCount] = useState(0);
    
    const handleClick = useCallback(() => {
        console.log('Clicked');
    }, []);
    
    return <ChildComponent onClick={handleClick} />;
}
```

**React.memo for Component Memoization**:
```jsx
// Before
function ExpensiveComponent({ data }) {
    // Expensive rendering logic
    return <div>{/* ... */}</div>;
}

// After
const ExpensiveComponent = React.memo(function ExpensiveComponent({ data }) {
    // Expensive rendering logic
    return <div>{/* ... */}</div>;
});

// Or with custom comparison
const ExpensiveComponent = React.memo(
    function ExpensiveComponent({ data }) {
        return <div>{/* ... */}</div>;
    },
    (prevProps, nextProps) => prevProps.data.id === nextProps.data.id
);
```

### 4. State Management Patterns

**useState → useReducer for Complex State**:
```jsx
// Before
function Form() {
    const [name, setName] = useState('');
    const [email, setEmail] = useState('');
    const [phone, setPhone] = useState('');
    const [errors, setErrors] = useState({});
    
    // Many setter functions...
}

// After
const initialState = {
    name: '',
    email: '',
    phone: '',
    errors: {}
};

function formReducer(state, action) {
    switch (action.type) {
        case 'SET_FIELD':
            return { ...state, [action.field]: action.value };
        case 'SET_ERROR':
            return { ...state, errors: { ...state.errors, [action.field]: action.error } };
        case 'RESET':
            return initialState;
        default:
            return state;
    }
}

function Form() {
    const [state, dispatch] = useReducer(formReducer, initialState);
    
    const setField = (field, value) => {
        dispatch({ type: 'SET_FIELD', field, value });
    };
}
```

**Context API for Prop Drilling**:
```jsx
// Before (Prop Drilling)
function App() {
    const [theme, setTheme] = useState('light');
    return <Layout theme={theme} setTheme={setTheme} />;
}

function Layout({ theme, setTheme }) {
    return <Header theme={theme} setTheme={setTheme} />;
}

function Header({ theme, setTheme }) {
    return <ThemeToggle theme={theme} setTheme={setTheme} />;
}

// After (Context)
const ThemeContext = createContext();

function ThemeProvider({ children }) {
    const [theme, setTheme] = useState('light');
    return (
        <ThemeContext.Provider value={{ theme, setTheme }}>
            {children}
        </ThemeContext.Provider>
    );
}

function useTheme() {
    return useContext(ThemeContext);
}

function ThemeToggle() {
    const { theme, setTheme } = useTheme();
    return <button onClick={() => setTheme(theme === 'light' ? 'dark' : 'light')}>
        Toggle
    </button>;
}
```

### 5. Component Composition

**Render Props → Custom Hooks**:
```jsx
// Before (Render Props)
function MouseTracker({ render }) {
    const [position, setPosition] = useState({ x: 0, y: 0 });
    
    useEffect(() => {
        const handleMove = (e) => setPosition({ x: e.clientX, y: e.clientY });
        window.addEventListener('mousemove', handleMove);
        return () => window.removeEventListener('mousemove', handleMove);
    }, []);
    
    return render(position);
}

// Usage
<MouseTracker render={pos => <div>x: {pos.x}, y: {pos.y}</div>} />

// After (Custom Hook)
function useMousePosition() {
    const [position, setPosition] = useState({ x: 0, y: 0 });
    
    useEffect(() => {
        const handleMove = (e) => setPosition({ x: e.clientX, y: e.clientY });
        window.addEventListener('mousemove', handleMove);
        return () => window.removeEventListener('mousemove', handleMove);
    }, []);
    
    return position;
}

// Usage
function Component() {
    const pos = useMousePosition();
    return <div>x: {pos.x}, y: {pos.y}</div>;
}
```

**HOCs → Hooks**:
```jsx
// Before (HOC)
function withAuth(Component) {
    return function AuthenticatedComponent(props) {
        const [user, setUser] = useState(null);
        
        useEffect(() => {
            checkAuth().then(setUser);
        }, []);
        
        if (!user) return <Login />;
        return <Component {...props} user={user} />;
    };
}

// After (Hook)
function useAuth() {
    const [user, setUser] = useState(null);
    const [loading, setLoading] = useState(true);
    
    useEffect(() => {
        checkAuth()
            .then(setUser)
            .finally(() => setLoading(false));
    }, []);
    
    return { user, loading };
}

function ProtectedComponent() {
    const { user, loading } = useAuth();
    
    if (loading) return <div>Loading...</div>;
    if (!user) return <Login />;
    return <div>Welcome {user.name}</div>;
}
```

### 6. Event Handlers

**Inline Functions → Extracted Handlers**:
```jsx
// Before
function Form() {
    const [name, setName] = useState('');
    
    return (
        <input 
            value={name}
            onChange={(e) => setName(e.target.value)}
        />
    );
}

// After (for complex logic or reuse)
function Form() {
    const [name, setName] = useState('');
    
    const handleNameChange = useCallback((e) => {
        const value = e.target.value;
        // Complex validation or transformation
        setName(value.trim());
    }, []);
    
    return <input value={name} onChange={handleNameChange} />;
}
```

### 7. Conditional Rendering

**Simplify Conditional Logic**:
```jsx
// Before
function UserStatus({ user }) {
    if (user === null) {
        return <div>Loading...</div>;
    } else {
        if (user.isActive) {
            return <div>Active User: {user.name}</div>;
        } else {
            return <div>Inactive User: {user.name}</div>;
        }
    }
}

// After
function UserStatus({ user }) {
    if (!user) return <div>Loading...</div>;
    
    const status = user.isActive ? 'Active' : 'Inactive';
    return <div>{status} User: {user.name}</div>;
}
```

### 8. Fragment & Key Optimization

**Use Fragments**:
```jsx
// Before
function List({ items }) {
    return (
        <div>
            {items.map(item => (
                <div key={item.id}>
                    <h3>{item.title}</h3>
                    <p>{item.description}</p>
                </div>
            ))}
        </div>
    );
}

// After
function List({ items }) {
    return (
        <>
            {items.map(item => (
                <Fragment key={item.id}>
                    <h3>{item.title}</h3>
                    <p>{item.description}</p>
                </Fragment>
            ))}
        </>
    );
}
```

## React Refactoring Checklist

### Modernization
- [ ] Convert class components to functional components
- [ ] Replace lifecycle methods with useEffect
- [ ] Migrate from HOCs to custom hooks
- [ ] Replace render props with hooks
- [ ] Use modern context API

### Performance
- [ ] Add React.memo where appropriate
- [ ] Use useMemo for expensive calculations
- [ ] Apply useCallback for stable function references
- [ ] Implement code splitting with lazy loading
- [ ] Optimize list rendering with keys

### State Management
- [ ] Use useReducer for complex state
- [ ] Extract logic to custom hooks
- [ ] Apply context for prop drilling
- [ ] Consider external state management if needed
- [ ] Avoid unnecessary state

### Component Design
- [ ] Extract reusable components
- [ ] Apply composition over inheritance
- [ ] Keep components focused (single responsibility)
- [ ] Use proper prop types or TypeScript
- [ ] Implement error boundaries

### Code Quality
- [ ] Simplify conditional rendering
- [ ] Extract complex JSX to components
- [ ] Use fragments appropriately
- [ ] Proper event handler naming
- [ ] Consistent naming conventions

## Output Format

```yaml
react_refactoring:
  hooks_migration:
    - component: {COMPONENT_NAME}
      before: CLASS
      after: FUNCTIONAL
      hooks_used: [useState, useEffect, useCallback]
      lines_reduced: {NUMBER}
  
  performance_optimizations:
    - optimization: {TECHNIQUE}
      location: {COMPONENT}
      expected_improvement: {DESCRIPTION}
      code: |
        {OPTIMIZED_CODE}
  
  custom_hooks_extracted:
    - hook_name: {NAME}
      logic: {DESCRIPTION}
      reused_in: [{COMPONENTS}]
      code: |
        {HOOK_CODE}
  
  state_management:
    - before: {APPROACH}
      after: {APPROACH}
      benefit: {EXPLANATION}
```

## Meta-Prompting Guidelines

<reasoning_effort>
Use HIGH reasoning effort for React refactoring requiring understanding of component lifecycle, hooks rules, performance implications, and React patterns.
</reasoning_effort>

<self_reflection>
- Ensure hooks follow rules of hooks
- Verify performance optimizations don't over-complicate
- Check that custom hooks are genuinely reusable
- Validate that refactorings maintain correct behavior
</self_reflection>

<exploration>
- Consider React version constraints
- Evaluate component rendering patterns
- Analyze state management needs
- Check for React-specific anti-patterns
- Consider TypeScript integration
</exploration>

## Common React Anti-Patterns to Refactor

1. **Class Components**: Migrate to functional with hooks
2. **Inline Object/Array Creation**: Extract to variables or useMemo
3. **Missing Keys in Lists**: Add proper unique keys
4. **Prop Drilling**: Use context or composition
5. **Large Components**: Extract smaller focused components
6. **Side Effects in Render**: Move to useEffect
7. **Direct State Mutation**: Use functional updates
8. **Missing Cleanup**: Add cleanup in useEffect
9. **Over-Optimization**: Don't memo everything
10. **God Components**: Split responsibilities
