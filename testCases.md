# Test Cases - Login Feature
**Project:** SauceDemo Login Testing \
**Author:** Jessica Vieira \
**Date:** September 22, 2026 \
**Reference Document:** Test Plan - Login Feature (v1.2)

## Conventions

* **ID:** LT (Login Test) + sequential number + Decision Table rule from the plan (when applicable). E.g., `LT01-R1`.
* **Priority:** Low, Medium, High, or Critical.
* **Status:** Not Run, Passed, or Failed.

**General Preconditions (apply to all cases):** Browser open at https://www.saucedemo.com, login screen loaded with empty fields, environment as described in section 10 of the test plan. Test data: section 11 of the test plan.

## Test Cases


| ID | Summary | Priority | Steps | Expected Result | Actual Result | Status | Bug / Issue | Observations |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| **LT01-R1** | Login with valid credentials (Smoke Test) | Critical | 1. Enter `standard_user` in the Username field.<br>2. Enter `secret_sauce` in the Password field.<br>3. Click Login. | Redirects to `/inventory.html` and displays the Products page ("Products"), with no error message. | Redirected to `/inventory.html` and displayed the Products page ("Products") without an error message. | Passed | | |
| **LT02-R2** | Login with locked-out user | High | 1. Enter `locked_out_user` in the Username field.<br>2. Enter `secret_sauce` in the Password field.<br>3. Click Login. | Access is denied, the user remains on the login screen, and the message `"Epic sadface: Sorry, this user has been locked out."` is displayed. | Access was denied, the user remained on the login screen, and the expected error message was displayed. | Passed | | |
| **LT03-R3** | Login with non-existent user and filled password | High | 1. Enter `usuario_invalido` in the Username field.<br>2. Enter `senha_invalida` in the Password field.<br>3. Click Login. | Access is denied, the user remains on the login screen, and the message `"Epic sadface: Username and password do not match any user in this service."` is displayed. | Access was denied, the user remained on the login screen, and the expected error message was displayed. | Passed | BUG-01 | The error message container has a UI defect: text is clipped at the top and bottom (text overflow), and the red container has misaligned padding. |
| **LT04-R4** | Login with valid user and incorrect password | High | 1. Enter `standard_user` in the Username field.<br>2. Enter `senha_invalida` in the Password field.<br>3. Click Login. | Access is denied, the user remains on the login screen, and the message `"Epic sadface: Username and password do not match any user in this service."` is displayed. | Access was denied, the user remained on the login screen, and the expected error message was displayed. | Passed | BUG-01 | The error message container has a UI defect: text is clipped at the top and bottom (text overflow), and the red container has misaligned padding. |
| **LT05-R5** | Login with empty user and filled password | High | 1. Leave the Username field empty.<br>2. Enter `secret_sauce` in the Password field.<br>3. Click Login. | Access is denied, and the message `"Epic sadface: Username is required."` is displayed. | Access was denied, and the expected error message was displayed. | Passed | | |
| **LT06-R6** | Login with filled user and empty password | High | 1. Enter `standard_user` in the Username field.<br>2. Leave the Password field empty.<br>3. Click Login. | Access is denied, and the message `"Epic sadface: Password is required."` is displayed. | Access was denied, and the expected error message was displayed. | Passed | | |
| **LT07-R7** | Login with empty user and empty password | High | 1. Leave the Username and Password fields empty.<br>2. Click Login. | Access is denied, and the message `"Epic sadface: Username is required."` is displayed. | Access was denied, and the expected error message was displayed. | Passed | | |
| **LT08** | Password field masking | Medium | 1. Click the Password field.<br>2. Enter `secret_sauce`.<br>3. Observe how the characters are displayed. | Password characters are masked (dots or asterisks) and are not visible in plain text. | Password characters were masked and were not visible in plain text. | Passed | | |
| **LT09-R3** | Login with uppercase username | Medium | 1. Enter `STANDARD_USER` in the Username field.<br>2. Enter `secret_sauce` in the Password field.<br>3. Click Login. | Access is denied, the user remains on the login screen, and the message `"Epic sadface: Username and password do not match any user in this service."` is displayed. | Access was denied, the user remained on the login screen, and the expected error message was displayed. | Passed | BUG-01 | The error message container has a UI defect: text is clipped at the top and bottom (text overflow), and the red container has misaligned padding. |
| **LT10** | Dismiss error message | Low | 1. Click Login with empty fields to trigger the error message.<br>2. Click the X icon next to the error message. | The error message is dismissed, and the user remains on the login screen. | The error message was dismissed, and the user remained on the login screen. | Passed | | |

## Traceability

### Scope Items x Test Cases
| Scope Item (section 3.1 of the test plan) | Test Cases |
| :--- | :--- |
| Login with valid credentials | LT01-R1 |
| Login with locked-out user | LT02-R2 |
| Login with invalid username and/or password | LT03-R3, LT04-R4, LT09-R3 |
| Login with empty fields | LT05-R5, LT06-R6, LT07-R7 |
| Validation of error messages | LT02-R2 to LT07-R7, LT09-R3, LT10 |
| Redirection to /inventory.html | LT01-R1 |
| Password masking | LT08 |

### Decision Table Rules x Test Cases
| Rule | Test Case |
| :--- | :--- |
| R1 | LT01-R1 |
| R2 | LT02-R2 |
| R3 | LT03-R3, LT09-R3 |
| R4 | LT04-R4 |
| R5 | LT05-R5 |
| R6 | LT06-R6 |
| R7 | LT07-R7 |

## Notes

* Error messages follow the observed behavior of SauceDemo; verify exact strings during execution as the system lacks formal specifications.
* Suggested execution order: LT01-R1 (Smoke Test) first. If it fails, execution of the full suite is suspended (criterion 9.3 of the test plan).
