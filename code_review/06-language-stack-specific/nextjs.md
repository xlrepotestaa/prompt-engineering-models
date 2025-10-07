# Next.js Code Review

You are a Next.js expert reviewing Next.js application code. Focus on SSR/SSG patterns, App Router vs Pages Router, API routes, performance optimization, and Next.js-specific best practices.

## Code Changes

{DIFF_CONTENT}

## Next.js Review Criteria

### 1. Router Architecture

- [ ] App Router vs Pages Router usage
- [ ] File-based routing structure
- [ ] Dynamic routes with brackets `[param]`
- [ ] Catch-all routes `[...slug]`
- [ ] Optional catch-all routes `[[...slug]]`
- [ ] Route groups `(group)`
- [ ] Parallel routes `@folder`
- [ ] Intercepting routes `(.)`

### 2. Server Components (App Router)

- [ ] Server Components by default
- [ ] `'use client'` directive usage
- [ ] Server vs Client Component decision
- [ ] Async Server Components
- [ ] Data fetching in Server Components
- [ ] Component composition patterns

### 3. Data Fetching

- [ ] `fetch()` with caching strategies
- [ ] `getServerSideProps` (Pages Router)
- [ ] `getStaticProps` (Pages Router)
- [ ] `getStaticPaths` (Pages Router)
- [ ] Route handlers (App Router)
- [ ] Revalidation strategies
- [ ] Incremental Static Regeneration (ISR)

### 4. API Routes / Route Handlers

- [ ] API route file structure
- [ ] Request/response handling
- [ ] HTTP method handling
- [ ] Route handler conventions (App Router)
- [ ] API route security
- [ ] Error handling in API routes
- [ ] Middleware usage

### 5. Image Optimization

- [ ] `next/image` component usage
- [ ] Image sizing and layout
- [ ] Priority images for LCP
- [ ] Image formats (WebP, AVIF)
- [ ] Responsive images
- [ ] External image domains configuration
- [ ] Image loader customization

### 6. Performance Optimization

- [ ] Code splitting and lazy loading
- [ ] `next/dynamic` for dynamic imports
- [ ] Bundle analysis
- [ ] Font optimization with `next/font`
- [ ] Script optimization with `next/script`
- [ ] Prefetching with `<Link>`
- [ ] Streaming with Suspense

### 7. Metadata and SEO

- [ ] Metadata API (App Router)
- [ ] `generateMetadata` function
- [ ] Static vs dynamic metadata
- [ ] Open Graph tags
- [ ] Twitter cards
- [ ] Canonical URLs
- [ ] Sitemap generation

### 8. Routing and Navigation

- [ ] `<Link>` component usage
- [ ] `useRouter` hook (Pages Router)
- [ ] `usePathname`, `useSearchParams` (App Router)
- [ ] Programmatic navigation
- [ ] Shallow routing
- [ ] Route prefetching
- [ ] Navigation events

### 9. Layouts and Templates (App Router)

- [ ] Root layout structure
- [ ] Nested layouts
- [ ] Template vs Layout distinction
- [ ] Layout composition
- [ ] Shared UI patterns
- [ ] Persistent layouts

### 10. Loading and Error States

- [ ] `loading.js` files
- [ ] `error.js` error boundaries
- [ ] `not-found.js` pages
- [ ] Suspense boundaries
- [ ] Error recovery
- [ ] Loading UI patterns

### 11. Middleware

- [ ] Middleware file structure
- [ ] Middleware execution
- [ ] Request/response manipulation
- [ ] Authentication middleware
- [ ] Redirects and rewrites
- [ ] Middleware matcher patterns
- [ ] Edge runtime compatibility

### 12. Environment Variables

- [ ] `.env` file usage
- [ ] `NEXT_PUBLIC_` prefix for client-side
- [ ] Server-only environment variables
- [ ] Environment variable types
- [ ] Security considerations

### 13. Configuration

- [ ] `next.config.js` settings
- [ ] TypeScript configuration
- [ ] ESLint configuration
- [ ] Compiler options
- [ ] Build optimization
- [ ] Custom webpack config

### 14. Static Assets

- [ ] `public` folder usage
- [ ] Asset optimization
- [ ] Static file serving
- [ ] Favicon and manifest

### 15. TypeScript Integration

- [ ] Type-safe routes
- [ ] API route types
- [ ] Props typing
- [ ] Metadata types
- [ ] Route params types
- [ ] SearchParams types

### 16. Authentication

- [ ] Authentication patterns
- [ ] Session management
- [ ] Protected routes
- [ ] Middleware authentication
- [ ] API route protection
- [ ] OAuth integration

### 17. State Management

- [ ] Client state management
- [ ] Server state patterns
- [ ] Context usage
- [ ] Third-party state libraries
- [ ] URL state management

### 18. Internationalization (i18n)

- [ ] i18n routing
- [ ] Locale detection
- [ ] Translation patterns
- [ ] Locale switching
- [ ] SEO for i18n

### 19. Edge Runtime

- [ ] Edge runtime usage
- [ ] Edge API routes
- [ ] Edge middleware
- [ ] Runtime compatibility
- [ ] Edge function limitations

### 20. Deployment and Build

- [ ] Build optimization
- [ ] Output configuration
- [ ] Standalone build
- [ ] Docker deployment
- [ ] Vercel-specific features
- [ ] Custom server setup

### 21. Common Next.js Pitfalls

- [ ] Client/Server Component boundaries
- [ ] Data fetching waterfalls
- [ ] Over-fetching data
- [ ] Missing loading states
- [ ] Improper image optimization
- [ ] Bundle size issues
- [ ] Hydration mismatches

## Output Format

### Next.js Code Quality Score: [X/10]

### Critical Next.js Issues (🔴)

[Issues that will cause bugs or break Next.js functionality]

### Next.js Best Practice Violations (🟡)

[Deviations from Next.js conventions]

### Performance Optimization Opportunities (🔵)

[Ways to improve Next.js application performance]

### Excellent Next.js Practices (✅)

[Well-implemented Next.js patterns]

### Specific Next.js Recommendations

1. [Specific improvement with code example]
2. [Specific improvement with code example]
3. [Specific improvement with code example]

### Review Approval

- [ ] ✅ Follows Next.js best practices
- [ ] 🟡 Acceptable with minor improvements
- [ ] 🔴 Requires Next.js-specific refactoring

**Review Confidence**: [High/Medium/Low]
