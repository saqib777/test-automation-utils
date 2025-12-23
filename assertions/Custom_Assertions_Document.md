CUSTOM ASSERTIONS — AUTOMATION UTILITIES LIBRARY (EXPLANATION)

Why Custom Assertions exist

Default assertions provided by test frameworks are technically correct but often unhelpful in practice. When a failure occurs, they usually show generic messages that lack context. This forces engineers to dig through logs or rerun tests just to understand what went wrong.

Custom assertions solve this problem by adding clarity, intent, and meaningful failure messages to tests. Instead of just stating that something failed, they explain what was expected, what actually happened, and why the failure matters.

For an SDET, this is not a cosmetic improvement. It directly impacts debugging speed and team productivity.

Problems with using raw assertions everywhere

Using raw assertions inside tests leads to repetitive checks, inconsistent error messages, and poor readability. Assertions end up mixed with test logic, making tests harder to scan and maintain.

When assertions are scattered across the codebase, improving error messages later becomes nearly impossible.

What good custom assertions provide

A well-designed assertion utility should:
- Express intent clearly
- Produce readable and meaningful failure messages
- Reduce repeated assertion logic
- Be reusable across UI and API tests
- Fail fast and fail clearly

Assertions should read like validation statements, not low-level comparisons.

Why assertion logic is centralized

Centralizing assertions ensures consistency across the test suite. When assertion behavior or messaging needs to change, it can be done in one place instead of across hundreds of tests.

This also enforces a common testing language across the team, which improves collaboration and code reviews.

Folder and file placement

The custom assertion helper lives alongside other reusable utilities.

test-automation-utils/
│
├── assertions/
│   └── custom_assertions.py

Design principles followed

Each assertion function is small, focused, and descriptive. The failure messages are explicit and actionable. The utility avoids framework-specific dependencies so it can be used in different contexts with minimal coupling.

The goal is to make tests easier to read and failures easier to understand.

How this improves test readability

With custom assertions, tests read more like specifications. Instead of comparing raw values inline, tests call assertion helpers that clearly describe what is being validated.

This improves maintainability and makes test intent obvious even to someone unfamiliar with the codebase.

Why this demonstrates an SDET mindset

This utility shows that you care about maintainability, clarity, and long-term scalability. It reflects an engineering approach to testing rather than a script-based mindset. Interviewers often see this as a sign of someone who has worked on real, evolving test suites.

