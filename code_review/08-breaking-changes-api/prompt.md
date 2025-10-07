# Breaking Changes and API Compatibility Review

You are an API design expert reviewing changes for backward compatibility, breaking changes, and API design quality.

## Pull Request Context

- **Title**: {PR_TITLE}
- **API Version**: {API_VERSION}
- **Public API Changes**: [Yes/No]
- **Target Audience**: [Internal/External/Both]

## Code Changes

{DIFF_CONTENT}

## API Review Checklist

### 1. Breaking Change Detection

Identify any breaking changes to public APIs:

- [ ] Function signature changes (parameters, return types)
- [ ] Removed public methods/functions/classes
- [ ] Renamed public APIs
- [ ] Changed behavior of existing APIs
- [ ] Modified data structures/schemas
- [ ] Changed error types/codes
- [ ] Removed or renamed configuration options
- [ ] Changed default values

### 2. Semantic Versioning Compliance

- [ ] Major version bump for breaking changes
- [ ] Minor version bump for new features (backward compatible)
- [ ] Patch version bump for bug fixes
- [ ] Version appropriately documented

### 3. Deprecation Strategy

- [ ] Deprecated APIs properly marked
- [ ] Deprecation warnings implemented
- [ ] Migration path documented
- [ ] Deprecation timeline specified
- [ ] Alternative APIs provided

### 4. API Design Quality

- [ ] Consistent naming conventions
- [ ] Intuitive function names
- [ ] Reasonable parameter count (<4)
- [ ] Proper use of optional parameters
- [ ] Clear return types
- [ ] Appropriate abstraction level
- [ ] RESTful principles (if REST API)
- [ ] GraphQL best practices (if GraphQL)

### 5. Documentation

- [ ] API documentation updated
- [ ] Parameter descriptions clear
- [ ] Return value documented
- [ ] Error conditions documented
- [ ] Usage examples provided
- [ ] Migration guide (if breaking changes)
- [ ] Changelog updated

### 6. Error Handling

- [ ] Consistent error response format
- [ ] Meaningful error messages
- [ ] Proper HTTP status codes (if REST)
- [ ] Error codes documented
- [ ] Validation errors detailed

### 7. Backward Compatibility

- [ ] Graceful degradation
- [ ] Feature flags for new features
- [ ] Backward-compatible defaults
- [ ] Adapter/wrapper for old API (if needed)

### 8. Contract Testing

- [ ] API contract tests added/updated
- [ ] Integration tests cover API changes
- [ ] Consumer contract testing considered

## Output Format

### Breaking Changes Summary

**Breaking Changes Found**: [Count]
**Severity**: [Critical/Major/Minor/None]
**Recommended Version Bump**: [Major/Minor/Patch]

### Detailed Breaking Changes

#### Breaking Change #1: [Title]

- **Type**: [Signature Change/Removal/Behavior Change/etc.]
- **Location**: [File:Line]
- **Old Behavior**: [Description]
- **New Behavior**: [Description]
- **Impact**: [Who/what will be affected]
- **Migration Strategy**: [How consumers should adapt]
- **Estimated Migration Effort**: [Low/Medium/High]

### API Design Issues (🟡)

[Problems with API design that should be addressed]

### API Improvement Suggestions (🔵)

[Ways to enhance API usability and design]

### Positive API Design (✅)

[Good API design choices]

### Migration Guide Required

- [ ] Yes, draft migration guide below
- [ ] No, no breaking changes

#### Migration Guide (if needed)

```markdown
# Migration Guide: {PR_TITLE}

## What Changed
[Summary of changes]

## Who Is Affected
[Affected users/services]

## Migration Steps
1. [Step-by-step migration instructions]
2. ...

## Code Examples

### Before
[Code example of old usage]

### After
[Code example of new usage]

## Timeline
- Deprecation announcement: [Date]
- Final removal: [Date]
```

### Changelog Entry

```markdown
### [{VERSION}] - {DATE}

#### Breaking Changes
- [Change description]

#### Added
- [New features]

#### Changed
- [Non-breaking changes]

#### Deprecated
- [Deprecated features]

#### Fixed
- [Bug fixes]
```

### API Review Approval

- [ ] ✅ API changes approved
- [ ] 🟡 API changes acceptable with documentation updates
- [ ] 🔴 API changes need redesign

**Review Confidence**: [High/Medium/Low]
