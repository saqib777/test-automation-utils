RETRY LOGIC — AUTOMATION UTILITIES LIBRARY (EXPLANATION)

Why Retry Logic exists

Even with proper waits in place, automation tests can still fail due to reasons outside the test’s control. These failures are not functional defects but transient issues such as momentary network delays, slow backend responses, temporary browser glitches, or unstable third-party services.

In real-world test execution, especially in CI pipelines, these transient failures are common. A single such failure can break an entire pipeline and block deployments, even though the application itself is fine.

Retry logic exists to handle these temporary, non-deterministic failures in a controlled and intelligent way.

What retry logic is NOT

Retry logic is not about hiding real bugs. Blindly retrying every failure is dangerous and considered bad engineering practice. If a test fails consistently, retrying it multiple times only masks genuine defects and creates false confidence.

Retry logic should be:
- Limited in number
- Explicit in intent
- Logged clearly
- Used only for known transient failures

This distinction is important and often discussed in SDET interviews.

The correct mental model for retries

A retry should act like a safety net, not a crutch. The test should attempt an operation, and if it fails due to a temporary issue, it should retry the same operation after a short pause. If the failure persists beyond a defined number of attempts, the test must fail clearly.

Retries should always answer these questions:
- How many times will we retry?
- What exception triggered the retry?
- What happens after all retries fail?

Why we centralize retry logic

Scattering retry loops across test code leads to duplication, inconsistency, and unreadable tests. Centralizing retry logic in a utility ensures:
- Consistent retry behavior across the suite
- Clean and readable tests
- Easier maintenance and tuning
- Clear logging and failure reasons

From an SDET perspective, this is a design decision that improves long-term reliability.

Folder and file placement

Retry logic is placed alongside other utilities so it can be reused by UI tests, API tests, and even setup or teardown steps.

test-automation-utils/
│
├── retries/
│   └── retry_helper.py

Design principles followed

The retry utility is designed to be simple, explicit, and safe. It limits the number of retries, introduces a configurable delay between attempts, and raises the original exception if all retries fail. Each retry attempt is logged so failures can be traced easily.

How this improves automation stability

Retry logic reduces noise caused by flaky infrastructure without hiding real issues. It keeps test suites stable in CI environments while still failing fast for genuine defects. This balance is exactly what teams expect from an SDET-owned framework.

Why this demonstrates an SDET mindset

This utility shows that you understand the difference between flaky tests and failing tests. It demonstrates engineering judgment, not just coding ability. Interviewers recognize this as a sign of maturity and production experience.
