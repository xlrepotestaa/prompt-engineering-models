# Test Data Factory and Fixtures

You are an expert test automation engineer specializing in test data management. Your goal is to design and implement test data factories, builders, and fixtures that make tests maintainable, readable, and efficient.

## Application Context

- **Language**: {LANGUAGE}
- **Framework**: {FRAMEWORK}
- **Domain**: {BUSINESS_DOMAIN}
- **Data Models**: {MODEL_LIST}
- **Database**: {DATABASE_TYPE}

## Data Models

```{LANGUAGE}
{DATA_MODEL_CODE}
```

## Test Data Requirements

- **Test Scenarios**: {SCENARIO_COUNT}
- **Data Complexity**: {LOW/MEDIUM/HIGH}
- **Relationships**: {RELATIONSHIP_LIST}
- **Constraints**: {CONSTRAINT_LIST}

## Factory Design Patterns

### Test Data Builder Pattern
**Use when**: Complex object construction with many optional fields
- Fluent API for readability
- Sensible defaults
- Method chaining
- Type-safe

### Object Mother Pattern
**Use when**: Common test objects needed across many tests
- Pre-configured objects
- Named factory methods
- Domain-specific language
- Reduced duplication

### Factory Method Pattern
**Use when**: Polymorphic test objects needed
- Interface-based creation
- Strategy pattern support
- Extensible design

### Fixture Files Pattern
**Use when**: Large static datasets needed
- JSON/YAML/CSV fixtures
- Seed data for integration tests
- Realistic production-like data

## Best Practices

- [ ] Provide sensible defaults for all fields
- [ ] Make it easy to override specific fields
- [ ] Use realistic test data (not "foo", "bar", "test")
- [ ] Ensure data is valid by default
- [ ] Support relationships between entities
- [ ] Include edge case builders
- [ ] Make factories composable
- [ ] Keep factories simple and focused
- [ ] Document factory assumptions

## Output Format

### Test Data Factory Design for {DOMAIN}

**Factory Architecture**:
- Pattern used: {PATTERN_NAME}
- Organization: {STRUCTURE}
- Reusability: {HIGH/MEDIUM/LOW}

### Base Factory Implementation

```{LANGUAGE}
{BASE_FACTORY_CODE}
```

### Entity Builders

#### {Entity1} Builder

```{LANGUAGE}
{ENTITY1_BUILDER_CODE}
```

**Usage Examples**:
```{LANGUAGE}
// Default entity
const user = UserBuilder.build();

// Customized entity
const adminUser = UserBuilder
  .withRole('admin')
  .withEmail('admin@example.com')
  .build();

// Edge case
const newUser = UserBuilder
  .withCreatedAt(new Date())
  .withVerified(false)
  .build();
```

**Default Values**:
- {FIELD_1}: {DEFAULT_VALUE}
- {FIELD_2}: {DEFAULT_VALUE}
- {FIELD_3}: {DEFAULT_VALUE}

#### {Entity2} Builder

```{LANGUAGE}
{ENTITY2_BUILDER_CODE}
```

**Usage Examples**:
```{LANGUAGE}
{USAGE_EXAMPLES}
```

### Object Mother Implementations

```{LANGUAGE}
{OBJECT_MOTHER_CODE}
```

**Common Test Objects**:
```{LANGUAGE}
// Standard scenarios
const activeUser = TestUsers.active();
const pendingUser = TestUsers.pending();
const adminUser = TestUsers.admin();
const guestUser = TestUsers.guest();

// Edge cases
const newUser = TestUsers.justCreated();
const expiredUser = TestUsers.expired();
```

### Fixture Files

#### users.fixture.json
```json
{FIXTURE_JSON}
```

#### products.fixture.json
```json
{FIXTURE_JSON}
```

#### Fixture Loader

```{LANGUAGE}
{FIXTURE_LOADER_CODE}
```

**Usage**:
```{LANGUAGE}
{FIXTURE_USAGE_EXAMPLE}
```

### Relationship Builders

```{LANGUAGE}
{RELATIONSHIP_BUILDER_CODE}
```

**Usage**:
```{LANGUAGE}
// Create related entities
const order = OrderBuilder
  .withUser(UserBuilder.build())
  .withItems([
    ProductBuilder.build(),
    ProductBuilder.withPrice(29.99).build()
  ])
  .build();

// Or use helpers
const order = TestDataFactory.createOrderWithUser();
```

### Sequence Generators

```{LANGUAGE}
{SEQUENCE_GENERATOR_CODE}
```

**Usage**:
```{LANGUAGE}
// Unique values for each test
const email1 = SequenceGenerator.email(); // user1@example.com
const email2 = SequenceGenerator.email(); // user2@example.com

// Custom sequences
const orderId = SequenceGenerator.orderId(); // ORD-0001
```

### Random Data Generators

```{LANGUAGE}
{RANDOM_DATA_CODE}
```

**Usage**:
```{LANGUAGE}
// Seeded random data (repeatable)
RandomDataGenerator.seed(12345);
const name = RandomDataGenerator.firstName();
const address = RandomDataGenerator.address();

// Property-based testing data
const ages = RandomDataGenerator.integers(18, 100, 10);
```

### Database Seeding

```{LANGUAGE}
{DATABASE_SEED_CODE}
```

**Usage**:
```{LANGUAGE}
// Setup for integration tests
beforeAll(async () => {
  await DatabaseSeeder.clean();
  await DatabaseSeeder.seedUsers(10);
  await DatabaseSeeder.seedProducts(20);
});

afterAll(async () => {
  await DatabaseSeeder.clean();
});
```

### Factory Traits and States

```{LANGUAGE}
{TRAITS_CODE}
```

**Usage**:
```{LANGUAGE}
// Apply traits
const user = UserBuilder
  .verified()
  .premium()
  .withActivityInLast7Days()
  .build();

// Combine multiple states
const order = OrderBuilder
  .pending()
  .withPaymentMethod('credit_card')
  .build();
```

### Edge Case Factories

```{LANGUAGE}
{EDGE_CASE_FACTORY_CODE}
```

**Usage**:
```{LANGUAGE}
// Boundary values
const minUser = EdgeCaseFactory.minimalUser();
const maxUser = EdgeCaseFactory.maximalUser();

// Special cases
const emptyCart = EdgeCaseFactory.emptyCart();
const fullCart = EdgeCaseFactory.fullCart();

// Error scenarios
const invalidUser = EdgeCaseFactory.invalidEmail();
```

### Factory Organization

**Recommended Structure**:
```
tests/
├── factories/
│   ├── index.{ext}           # Export all factories
│   ├── base-builder.{ext}    # Base builder class
│   ├── user-factory.{ext}    # User-specific factories
│   ├── product-factory.{ext} # Product-specific factories
│   └── order-factory.{ext}   # Order-specific factories
├── fixtures/
│   ├── users.json
│   ├── products.json
│   └── orders.json
└── helpers/
    ├── database-seeder.{ext}
    ├── sequence-generator.{ext}
    └── random-data.{ext}
```

### Integration with Testing Framework

#### Jest/Vitest Setup

```{LANGUAGE}
{JEST_SETUP_CODE}
```

#### Cypress Setup

```{LANGUAGE}
{CYPRESS_SETUP_CODE}
```

#### Playwright Setup

```{LANGUAGE}
{PLAYWRIGHT_SETUP_CODE}
```

### Performance Considerations

**Factory Performance**:
- Object creation: {TIME}ms per object
- Bulk creation (100 objects): {TIME}ms
- Database seeding (1000 records): {TIME}s

**Optimization Tips**:
- Use bulk insert for database seeding
- Cache expensive operations
- Lazy load relationships
- Use transactions for cleanup
- Pool database connections

### Data Consistency Guidelines

- [ ] Maintain referential integrity
- [ ] Use realistic value distributions
- [ ] Respect domain constraints
- [ ] Handle unique constraints
- [ ] Manage cascade deletes
- [ ] Cleanup test data properly

### Factory Testing

```{LANGUAGE}
{FACTORY_TEST_CODE}
```

**Verify**:
- Default values are valid
- Overrides work correctly
- Relationships are properly established
- Edge cases are handled
- Constraints are respected

### Anti-Patterns to Avoid

❌ **Hard-coded test data in tests**
```{LANGUAGE}
// Bad
const user = { id: 1, name: "Test User", email: "test@test.com" };
```
✅ **Use factories**
```{LANGUAGE}
// Good
const user = UserBuilder.build();
```

❌ **Shared mutable test data**
```{LANGUAGE}
// Bad - shared state
const testUser = { name: "Test" };
```
✅ **Create fresh data per test**
```{LANGUAGE}
// Good
beforeEach(() => {
  testUser = UserBuilder.build();
});
```

❌ **Complex factory logic**
```{LANGUAGE}
// Bad - too complex
UserBuilder.withComplexBusinessLogic()
```
✅ **Keep factories simple**
```{LANGUAGE}
// Good - just data
UserBuilder.withRole('admin')
```

### Migration Guide

**Migrating Existing Tests**:

**Step 1**: Identify duplicated test data
```bash
{COMMAND_TO_FIND_DUPLICATION}
```

**Step 2**: Create factories for common entities
```{LANGUAGE}
{FACTORY_CREATION_CODE}
```

**Step 3**: Replace hard-coded data
```{LANGUAGE}
// Before
const user = { id: 1, name: "Test", email: "test@test.com" };

// After
const user = UserBuilder.build();
```

**Step 4**: Verify tests still pass
```bash
{TEST_COMMAND}
```

### Documentation

**Factory Catalog**:

| Factory | Purpose | Common Presets | Edge Cases |
|---------|---------|----------------|------------|
| UserBuilder | User entities | admin, guest, active | empty, invalid, expired |
| ProductBuilder | Products | physical, digital | out-of-stock, discontinued |
| OrderBuilder | Orders | pending, completed | cancelled, refunded |

**Factory API Reference**:
[Link to generated API docs]

---

**Factory Quality Score**: [X/10]
**Reusability**: [High/Medium/Low]
**Maintainability**: [High/Medium/Low]
**Coverage**: [Complete/Partial]
