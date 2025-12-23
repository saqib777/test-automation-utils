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
