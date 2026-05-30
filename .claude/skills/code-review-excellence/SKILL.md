---
name: code-review-excellence
description: |
  Provides comprehensive code review guidance for React 19, Vue 3, Angular 17+, Svelte 5, Rust, TypeScript, Java, Python, Django, Go, C#/.NET, Kotlin, NestJS, C/C++, and more.
  Helps catch bugs, improve code quality, and give constructive feedback.
  Use when: reviewing pull requests, conducting PR reviews, code review, reviewing code changes,
  establishing review standards, mentoring developers, architecture reviews, security audits,
  checking code quality, finding bugs, giving feedback on code.
user-invocable: true
allowed-tools:
  - Read
  - Grep
  - Glob
  - Bash
  - WebFetch
---

# Code Review Excellence

Transform code reviews from gatekeeping to knowledge sharing through constructive feedback, systematic analysis, and collaborative improvement.

## When to Use This Skill

- Reviewing pull requests and code changes
- Establishing code review standards for teams
- Mentoring junior developers through reviews
- Conducting architecture reviews
- Maintaining code quality standards

## Core Principles

### The Review Mindset

**Goals of Code Review:**
- Catch bugs and edge cases
- Ensure code maintainability
- Share knowledge across team
- Enforce coding standards
- Improve design and architecture

**Not the Goals:**
- Show off knowledge
- Nitpick formatting (use linters)
- Block progress unnecessarily
- Rewrite to your preference

### Effective Feedback

Good feedback is specific, actionable, educational (not judgmental), focused on the code (not the person), balanced (praise good work too), and prioritized (critical vs nice-to-have).

```
❌ Bad: "This is wrong."
✅ Good: "This could cause a race condition when multiple users access simultaneously. Consider using a mutex here."

❌ Bad: "Why didn't you use X pattern?"
✅ Good: "Have you considered the Repository pattern? It would make this easier to test."

❌ Bad: "Rename this variable."
✅ Good: "[nit] Consider `userCount` instead of `uc` for clarity. Not blocking."
```

### What to Review

- Logic correctness and edge cases
- Security vulnerabilities
- Performance implications
- Test coverage and quality
- Error handling
- API design and naming
- Architectural fit

**What Not to Review Manually:** code formatting, import organization, linting violations, simple typos — use automated tools for these.

## Review Process

### Phase 1: Context Gathering (2-3 min)

1. Read PR description and linked issue
2. Check PR size (>400 lines? Ask to split)
3. Review CI/CD status (tests passing?)
4. Understand the business requirement
5. Note relevant architectural decisions

### Phase 2: High-Level Review (5-10 min)

1. **Architecture & Design** — Does the solution fit the problem? SOLID principles, coupling/cohesion, anti-patterns
2. **Performance** — Algorithm complexity, N+1 queries, memory usage
3. **File Organization** — New files in the right places?
4. **Testing Strategy** — Edge cases covered?

### Phase 3: Line-by-Line Review (10-20 min)

For each file check:
- **Logic & Correctness** — Edge cases, off-by-one, null checks, race conditions
- **Security** — Input validation, injection risks, XSS, sensitive data
- **Performance** — N+1 queries, unnecessary loops, memory leaks
- **Maintainability** — Clear names, single responsibility
- **Reuse** — Search for existing utilities before accepting new code; check adjacent files and shared modules

### Phase 4: Summary & Decision (2-3 min)

1. Summarize key concerns
2. Highlight what you liked
3. Make a clear decision:
   - ✅ Approve
   - 💬 Comment (minor suggestions)
   - 🔄 Request Changes (must address)
4. Offer to pair if complex

## Severity Labels

- 🔴 `[blocking]` — Must fix before merge
- 🟡 `[important]` — Should fix, discuss if you disagree
- 🟢 `[nit]` — Nice to have, not blocking
- 💡 `[suggestion]` — Alternative approach to consider
- 📚 `[learning]` — Educational comment, no action needed
- 🎉 `[praise]` — Good work, keep it up!

## Review Techniques

### Ask Questions, Don't Command

```
❌ "This will fail if the list is empty."
✅ "What happens if `items` is an empty array?"

❌ "You need error handling here."
✅ "How should this behave if the API call fails?"
```

### Suggest, Don't Command

```
❌ "You must change this to use async/await"
✅ "Suggestion: async/await might make this more readable. What do you think?"

❌ "Extract this into a function"
✅ "This logic appears in 3 places. Would it make sense to extract it?"
```

## Language-Specific Key Concerns

| Language/Framework | Key Topics |
|-------------------|------------|
| **React 19** | Hooks rules, useEffect deps, Server Components, Suspense, Actions |
| **Vue 3** | Composition API, reactivity, Props/Emits, Composables |
| **Angular 17+** | Signals, Standalone components, RxJS, Zoneless change detection |
| **Rust** | Ownership/borrowing, Unsafe blocks, async cancel-safety |
| **TypeScript** | Type safety, `any` usage, async/await, immutability |
| **Python** | Mutable defaults, exception handling, class attributes |
| **Go** | Error handling, goroutine/channel, context propagation |
| **Java** | Java 17/21 features, Spring Boot 3, virtual threads |
| **C#/.NET** | async/await patterns, EF Core N+1, LINQ |
| **Kotlin** | Coroutines, Flow, null safety, Jetpack Compose |
| **NestJS** | DI, layered architecture, DTO validation, Guards/Interceptors |

## Common Anti-Patterns to Catch

- **Parameter sprawl** — function with 5+ params; suggest object/config
- **Leaky abstractions** — implementation details bleeding through interfaces
- **Nested conditionals** — deeply nested if/else; suggest early returns
- **Stringly-typed code** — magic strings instead of enums/constants
- **TOCTOU** — check-then-act race conditions
- **No-op updates** — setting state to the same value unnecessarily
- **Redundant state** — derived state stored instead of computed
