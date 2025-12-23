# Test Automation Utilities Library

## Overview

This repository contains a collection of reusable utilities designed to support UI and API automation frameworks. The goal of this library is to solve common automation problems in a clean, consistent, and scalable way, without polluting test code with low-level implementation details.

This is **not a test framework**.  
It is a shared utility layer that can be plugged into any automation framework built using Selenium, Playwright, or API testing tools.

The utilities in this repository reflect real-world automation challenges and demonstrate an SDET-style engineering mindset.

---

## Why this repository exists

In many automation projects, test code slowly becomes cluttered with:
- hard waits
- retry loops
- print statements
- repeated assertion logic
- hardcoded test data
- scattered screenshot handling

Over time, this makes test suites flaky, slow, and hard to maintain.

This repository centralizes those concerns into well-defined utilities so that:
- tests remain readable
- failures are easier to debug
- behavior is consistent across the suite
- changes can be made in one place

---

## Repository Structure

```
test-automation-utils/
│
├── waits/
│ └── wait_helpers.py
│
├── retries/
│ └── retry_helper.py
│
├── data/
│ └── test_data_generator.py
│
├── screenshots/
│ └── screenshot_helper.py
│
├── assertions/
│ └── custom_assertions.py
│
├── logging/
│ └── logger_helper.py
│
└── README.md

```


Each folder represents a specific automation concern and contains a focused, reusable utility.

---

## Utilities Included

### 1. Wait Helpers

Provides explicit wait wrappers for common UI conditions such as:
- element presence
- element visibility
- element clickability
- text presence
- URL validation

This utility removes the need for hard waits and direct usage of Selenium wait internals inside tests.

---

### 2. Retry Logic

Handles transient failures caused by:
- network instability
- temporary browser issues
- slow backend responses

Retries are controlled, limited, and explicit, ensuring real bugs are not hidden while reducing test flakiness.

---

### 3. Test Data Generator

Generates dynamic and reusable test data such as:
- random users
- emails and phone numbers
- boundary values
- invalid data for negative testing

This eliminates hardcoded data and enables safe parallel execution.

---

### 4. Screenshot Helper

Captures screenshots with:
- automatic directory creation
- timestamped filenames
- consistent naming conventions

Designed to be used during failures, hooks, or debugging steps.

---

### 5. Custom Assertions

Provides readable, intent-driven assertions with meaningful failure messages.
These assertions improve test clarity and reduce noisy debugging output.

---

### 6. Logging Helper

Creates a centralized logging setup with:
- log levels (INFO, WARNING, ERROR)
- timestamps
- file and console output

This is especially useful for CI environments where logs are the primary debugging tool.

---

## How to use this repository

This repository is intended to be imported into an automation framework.

Example usage pattern:
- Add this repo as a dependency or submodule
- Import required utilities into your tests or framework layer
- Keep test code focused on behavior, not infrastructure

Tests should describe **what** is being validated, not **how** supporting logic works.

---

## Design philosophy

This library follows a few simple principles:
- clarity over cleverness
- reuse over duplication
- explicit behavior over hidden magic
- maintainability over shortcuts

Every utility exists because it solves a real automation problem.

---

## Intended audience

This repository is designed for:
- SDETs
- Automation engineers
- Test engineers moving toward engineering-heavy roles
- Anyone building scalable automation frameworks

---

## Status

This repository is actively evolving. Utilities are added incrementally, with a focus on correctness, clarity, and real-world applicability.

---

## License

This project is intended for learning, portfolio demonstration, and internal automation use.

