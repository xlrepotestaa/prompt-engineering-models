# Language-Specific Code Review Prompts

This directory contains specialized code review prompts for different programming languages and frameworks. Each prompt is tailored to specific language versions, frameworks, and architectural patterns.

## Available Prompts

### Python-Specific Review
See [python-review.md](./python-review.md) for Python-specific best practices, idioms, and common pitfalls.

### JavaScript/TypeScript - Core

#### Generic (Frontend/General)
- **[javascript-vanilla-generic.md](javascript-vanilla-generic.md)** - Vanilla JavaScript for general/frontend use
- **[javascript-es6-generic.md](javascript-es6-generic.md)** - Modern JavaScript (ES6+) for general/frontend use
- **[typescript-generic.md](typescript-generic.md)** - TypeScript for general/frontend use

#### Backend/Node.js
- **[javascript-vanilla-backend.md](javascript-vanilla-backend.md)** - Vanilla JavaScript for backend/Node.js
- **[javascript-es6-backend.md](javascript-es6-backend.md)** - Modern JavaScript (ES6+) for backend/Node.js
- **[typescript-backend.md](typescript-backend.md)** - TypeScript for backend/Node.js

### React
- **[react-modern-javascript.md](react-modern-javascript.md)** - React Functional Components with Hooks (JavaScript)
- **[react-modern-typescript.md](react-modern-typescript.md)** - React Functional Components with Hooks (TypeScript)
- **[react-legacy-javascript.md](react-legacy-javascript.md)** - React Class Components (JavaScript)
- **[react-legacy-typescript.md](react-legacy-typescript.md)** - React Class Components (TypeScript)

### Angular
- **[angular-javascript.md](angular-javascript.md)** - AngularJS (1.x) with JavaScript
- **[angular-typescript.md](angular-typescript.md)** - Angular (2+) with TypeScript

### Vue
- **[vue2-javascript.md](vue2-javascript.md)** - Vue 2 with JavaScript (Options API)
- **[vue2-typescript.md](vue2-typescript.md)** - Vue 2 with TypeScript
- **[vue3-javascript.md](vue3-javascript.md)** - Vue 3 with JavaScript (Composition API)
- **[vue3-typescript.md](vue3-typescript.md)** - Vue 3 with TypeScript (Composition API)

### Svelte
- **[svelte-javascript.md](svelte-javascript.md)** - Svelte with JavaScript
- **[svelte-typescript.md](svelte-typescript.md)** - Svelte with TypeScript

### Meta-Frameworks
- **[nextjs.md](nextjs.md)** - Next.js (App Router & Pages Router, SSR/SSG)
- **[nuxtjs.md](nuxtjs.md)** - Nuxt.js (Nuxt 3 with Composition API)

### Backend Frameworks
- **[nestjs.md](nestjs.md)** - NestJS (Node.js enterprise framework)
- **[expressjs.md](expressjs.md)** - Express.js (Node.js web framework)

### API & GraphQL
- **[graphql.md](graphql.md)** - GraphQL Schema, Resolvers, and API Design

### Testing
- **[testing-jest-vitest-cypress.md](testing-jest-vitest-cypress.md)** - Testing with Jest, Vitest, and Cypress

### Mobile Development
- **[react-native.md](react-native.md)** - React Native mobile applications

## Choosing the Right Prompt

### For JavaScript/TypeScript Projects

**Consider these factors:**
1. **Language**: JavaScript or TypeScript?
2. **Environment**: Frontend/Generic or Backend/Node.js?
3. **Framework**: React, Angular, Vue, or none?
4. **Framework Version**: Vue 2 vs 3, AngularJS vs Angular
5. **Architecture Pattern**: Class-based or Functional/Hooks (React), Options or Composition API (Vue)

### Quick Selection Guide

| Project Type | Language | Prompt File |
|--------------|----------|-------------|
| Vanilla Frontend | JS | `javascript-vanilla-generic.md` |
| Modern Frontend (ES6+) | JS | `javascript-es6-generic.md` |
| Generic/Frontend | TS | `typescript-generic.md` |
| Node.js Backend | JS (legacy) | `javascript-vanilla-backend.md` |
| Node.js Backend | JS (modern) | `javascript-es6-backend.md` |
| Node.js Backend | TS | `typescript-backend.md` |
| React Hooks | JS | `react-modern-javascript.md` |
| React Hooks | TS | `react-modern-typescript.md` |
| React Classes | JS | `react-legacy-javascript.md` |
| React Classes | TS | `react-legacy-typescript.md` |
| AngularJS (1.x) | JS | `angular-javascript.md` |
| Angular (2+) | TS | `angular-typescript.md` |
| Vue 2 | JS | `vue2-javascript.md` |
| Vue 2 | TS | `vue2-typescript.md` |
| Vue 3 | JS | `vue3-javascript.md` |
| Vue 3 | TS | `vue3-typescript.md` |
| Svelte | JS | `svelte-javascript.md` |
| Svelte | TS | `svelte-typescript.md` |
| Next.js | JS/TS | `nextjs.md` |
| Nuxt.js | JS/TS | `nuxtjs.md` |
| NestJS | TS | `nestjs.md` |
| Express.js | JS/TS | `expressjs.md` |
| GraphQL | JS/TS | `graphql.md` |
| Testing (Jest/Vitest/Cypress) | JS/TS | `testing-jest-vitest-cypress.md` |
| React Native | JS/TS | `react-native.md` |

## Usage

1. **Select the appropriate prompt** based on your project characteristics
2. **Replace `{DIFF_CONTENT}`** with your actual code changes
3. **Provide the prompt** to your AI code review tool

## Common Features Across All Prompts

Each specialized prompt includes:

- **Detailed Review Criteria** - Framework/language-specific checklist
- **Code Quality Score** - Quantitative assessment (X/10)
- **Categorized Issues**:
  - 🔴 Critical Issues (must fix)
  - 🟡 Best Practice Violations (should fix)
  - 🔵 Optimization Opportunities (nice to have)
  - ✅ Excellent Practices (worth highlighting)
- **Specific Recommendations** - Actionable improvements
- **Review Approval Status** - Overall assessment

## When to Use

Use language-specific reviews when:
- The PR is primarily in one language/framework
- You want to enforce language-specific best practices
- You need to check for framework-specific issues
- You want to ensure modern features are used appropriately
- You need to assess type safety (TypeScript variants)
