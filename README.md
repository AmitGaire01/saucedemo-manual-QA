# SauceDemo Manual QA Practice Project

Self-directed manual testing project against [SauceDemo](https://www.saucedemo.com/), a public e-commerce demo site built specifically for QA practice.

## What this project covers
- **Test case design** for the Login and Checkout flows (functional, boundary, and negative scenarios)
- **Bug identification and reporting** using SauceDemo's intentionally-seeded buggy accounts (`problem_user`, `visual_user`)
- Standard QA documentation practices: severity/priority ratings, steps to reproduce, expected vs. actual results

## Why SauceDemo
It's a stable, public sandbox designed for testers to practice on, with multiple user accounts that surface real (intentional) bugs — useful for demonstrating both test design skill and bug-hunting ability without needing access to a real company's product.

## Contents
| File | Description |
|------|--------------|
| `test_cases.md` | 26 manual test cases across Login and Checkout modules |
| `bug_reports.md` | 4 documented bugs found via `problem_user` / `visual_user`, written in a standard bug-report format |

## Approach
1. Designed test cases against expected/standard behavior (`standard_user` login)
2. Executed the same test cases against SauceDemo's intentionally buggy accounts
3. Logged any deviation from expected behavior as a formal bug report

## Tools used
- Manual browser testing (Chrome)
- Markdown for documentation
- Git/GitHub for version control and portfolio hosting

## Next steps (planned)
- Automate the Login + Checkout regression suite using Selenium + Python
- Add API-level test coverage for a public REST API using Postman

---
**Author:** Amit Gaire — [GitHub](https://github.com/AmitGaire01) · [LinkedIn](https://linkedin.com/in/amitgaire01)
