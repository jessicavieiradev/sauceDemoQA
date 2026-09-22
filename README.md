# Software Testing & QA - SauceDemo

> **Software Quality Assurance (QA) Portfolio Project**  
> This repository contains the complete documentation for the manual testing cycle of the **Login** functionality on the [SauceDemo](https://www.saucedemo.com) application.

---

## Author

* **Name:** Jessica Vieira
* **Role:** QA Analyst / Test Analyst
* **GitHub:** [@jessicavieiradev](https://github.com/jessicavieiradev)

---

## Project Overview

The objective of this project is to demonstrate the practical application of fundamental **Quality Assurance (QA)** and **Software Testing** concepts, covering everything from strategic planning to execution, traceability, and formal defect reporting.

The application tested was **SauceDemo**, a dummy e-commerce site widely used in the QA community to simulate real-world functional and user interface (UI) testing scenarios.

---

## Project Deliverables

The project is structured into **3 main documents**, covering the entire testing lifecycle:

| Document | Description | Access Link |
| :--- | :--- | :--- |
| **1. Test Plan** | Strategic planning, scope, environment, entry/exit criteria, risks, and Decision Table. | [View Test Plan](https://github.com/jessicavieiradev/sauceDemoQA/blob/main/testPlan.md) |
| **2. Test Cases & Execution** | Test suite featuring traceability, step-by-step instructions, expected vs. actual results, and coverage matrix. | [View Execution](https://github.com/jessicavieiradev/sauceDemoQA/blob/main/testCases.md) |
| **3. Bug Report** | Detailed technical documentation of the visual defect (UI/Overflow) identified during execution. | [View Bug Report](https://github.com/jessicavieiradev/sauceDemoQA/blob/main/bugReport.md) |

---

## Methodologies & Applied Techniques

* **Test Design Techniques (Black-Box):**
  * **Decision Table:** Mapping of 7 business rules to ensure complete coverage of input combinations (valid, locked-out, invalid, and empty credentials).
  * **Equivalence Partitioning:** Dividing inputs into valid, invalid, and state classes to prevent redundant testing.
* **Test Types & Levels:**
  * **Smoke Test (Suspension Criteria):** Critical validation of the happy path (`standard_user`) prior to running the full test suite.
  * **Functional Testing:** Validation of business rules, mandatory error messages, and access restriction.
  * **UI/UX Testing:** Validation of password masking and visual display of elements on screen.
* **Documentation & Traceability:**
  * Traceability Matrix covering Scope Items and Decision Table Rules.
  * Standardized Bug Reporting (`BUG-01`) featuring severity, priority, steps to reproduce, and supporting evidence.

---

## Defect Found (Highlight)

During test suite execution, a layout/UI bug common to multiple invalid credential scenarios was identified:

* **Bug ID:** `BUG-01`
* **Type:** UI / Layout (Text Overflow & Misaligned Padding)
* **Severity:** Low | **Priority:** Medium
* **Summary:** The error message `"Epic sadface: Username and password do not match any user in this service"` is triggered correctly by the business rule, but displays with text clipping on the top/bottom margins and misalignment inside the red container.

---

## Tools Used

* Markdown (Documentation)
* Git & GitHub (Version control and portfolio hosting)
* Firefox for Arch Linux
