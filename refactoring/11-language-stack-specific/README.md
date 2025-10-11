# Language & Stack-Specific Refactoring Prompts

This directory contains specialized refactoring prompts tailored to specific programming languages, frameworks, and technology stacks. Each prompt addresses language-specific code smells, idioms, and best practices for refactoring.

## 📁 Structure

```text
11-language-stack-specific/
├── README.md                          # This file
├── python-refactoring.md              # Python-specific refactoring
├── javascript-refactoring.md          # JavaScript/TypeScript refactoring
├── java-refactoring.md                # Java refactoring
├── csharp-refactoring.md              # C# refactoring
├── go-refactoring.md                  # Go refactoring
├── rust-refactoring.md                # Rust refactoring
├── ruby-refactoring.md                # Ruby refactoring
├── php-refactoring.md                 # PHP refactoring
├── react-refactoring.md               # React-specific refactoring
├── angular-refactoring.md             # Angular-specific refactoring
├── vue-refactoring.md                 # Vue-specific refactoring
├── spring-boot-refactoring.md         # Spring Boot refactoring
├── django-refactoring.md              # Django refactoring
└── dotnet-refactoring.md              # .NET refactoring
```

## 🎯 Purpose

Language-specific refactoring prompts help you:

- **Adopt Language Idioms**: Use language-specific patterns and conventions
- **Modernize Code**: Update to latest language versions and features
- **Framework Best Practices**: Apply framework-specific refactoring patterns
- **Performance Optimization**: Language-specific performance improvements
- **Type Safety**: Improve type systems where applicable
- **Error Handling**: Language-appropriate error handling patterns

## 🚀 Coming Soon

Language-specific refactoring prompts will be added to cover:

### Core Languages
- **Python**: PEP 8 compliance, type hints, dataclasses, asyncio patterns
- **JavaScript/TypeScript**: ES6+ features, TypeScript migration, async/await
- **Java**: Modern Java features (8-21), streams, optionals, records
- **C#**: LINQ, async/await, nullable reference types, records
- **Go**: Goroutines, channels, error handling patterns
- **Rust**: Ownership, borrowing, lifetimes, traits
- **Ruby**: Ruby 3 features, Rails patterns
- **PHP**: PHP 8+ features, PSR standards

### Frameworks
- **React**: Hooks migration, performance optimization, modern patterns
- **Angular**: RxJS patterns, dependency injection, best practices
- **Vue**: Composition API, reactivity, performance
- **Spring Boot**: Dependency injection, REST patterns, JPA optimization
- **Django**: ORM optimization, async views, middleware patterns
- **.NET**: Minimal APIs, EF Core, async patterns

## 📋 Refactoring Categories by Language

Each language-specific prompt will cover:

1. **Code Smells**: Language-specific anti-patterns
2. **Modernization**: Updating to newer language versions
3. **Idioms**: Using language-appropriate patterns
4. **Performance**: Language-specific optimizations
5. **Type Safety**: Strong typing where applicable
6. **Error Handling**: Language-appropriate patterns
7. **Testing**: Language-specific test patterns
8. **Build & Tooling**: Modern build tools and practices

## 💡 Usage Pattern

1. **Choose Language Prompt**: Select based on your technology stack
2. **Run General Refactoring**: Apply general prompts first (code smells, SOLID, etc.)
3. **Apply Language-Specific**: Use language prompt for idioms and best practices
4. **Combine with Framework**: If applicable, use framework-specific guidance
5. **Validate**: Test thoroughly after language-specific refactoring

## 🔗 Related Prompts

For comprehensive refactoring, combine with:

- [Code Smells Detection](../01-code-smells-detection/prompt.md)
- [SOLID Principles](../02-solid-principles/prompt.md)
- [Design Patterns](../03-design-patterns/prompt.md)
- [Performance Refactoring](../05-performance-refactoring/prompt.md)
- [Modernization](../09-modernization/prompt.md)

## 📊 Priority Framework

When refactoring with language-specific prompts:

**High Priority**:
- Security vulnerabilities specific to language/framework
- Deprecated language features being removed
- Critical performance issues
- Type safety improvements (if applicable)

**Medium Priority**:
- Modern syntax adoption
- Idiomatic pattern application
- Framework best practices
- Code organization

**Low Priority**:
- Syntactic sugar
- Style preferences
- Minor optimizations

## 🎓 Learning Resources

Each language-specific prompt will reference:
- Official language style guides
- Framework documentation
- Community best practices
- Migration guides for version updates

---

**Note**: Language-specific prompts are being developed and will be added incrementally. Check back for updates or contribute your own!
