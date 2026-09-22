# Test Plan - Login Feature
**Project:** SauceDemo Login Testing \
**Author:** Jessica Vieira \
**Date:** September 21, 2026

## 1. Objective
Ensure the effectiveness of the authentication mechanism by validating that system access is granted exclusively upon entering valid credentials. Additionally, verify that the system properly handles invalid or incorrect input data, displaying the appropriate error messages and preventing unauthorized access.

## 2. Revision History
| Version | Date | Description | Author |
| :--- | :--- | :--- | :--- |
| 1.0 | 09/21/2026 | Test plan creation | Jessica Vieira |
| 1.1 | 09/21/2026 | Added Decision Table, Estimates, Test Items, Suspension/Resumption Criteria, Test Data, References, and Glossary | Jessica Vieira |
| 1.2 | 09/22/2026 | Added Assumptions section and removed items from Out of Scope that were non-existent features in SauceDemo | Jessica Vieira |

## 3. Scope
### 3.1 In Scope
* Login with valid credentials
* Login with locked-out user
* Login with invalid username and/or password
* Login with empty username and/or password fields
* Error message validation on the login screen
* Redirection to the products page (/inventory.html) after a valid login
* Password masking

### 3.2 Out of Scope
* Security testing (SQL Injection, XSS, etc.)
* Performance and load testing
* Cross-browser and cross-OS testing
* Validation of post-login anomalous behaviors associated with special Sauce Demo profiles (`problem_user`, `performance_glitch_user`, `error_user`, and `visual_user`), as the authentication process for these users follows the standard flow.

## 4. Assumptions
* SauceDemo does not feature a password recovery flow ("Forgot Password"), making this scenario inapplicable to the test scope.
* SauceDemo does not implement dynamic account locking after multiple incorrect attempts; the user `locked_out_user` is provided pre-locked by the application. Therefore, this behavior is not applicable.
* SauceDemo does not feature "Remember Me", user registration, or social media login options on the authentication screen.

## 5. Test Items
| Item | Description |
| :--- | :--- |
| Login Screen | SauceDemo landing page (https://www.saucedemo.com), web version |
| Input Fields | Username and Password |
| Error Messages | Messages displayed upon authentication failures |
| Redirection | Access to `/inventory.html` following a valid login |

## 6. Team
As this test plan is part of a personal portfolio project designed to demonstrate software testing skills, Jessica Vieira is the sole contributor.

## 7. Risks and Mitigations
| Identified Risk | Impact | Mitigation Strategy |
| :--- | :--- | :--- |
| Inaccessibility of the public Sauce Demo environment during execution. | High | Verify URL stability (https://www.saucedemo.com/) prior to starting the test session. |
| Redirection failure for valid user (`standard_user`). | Critical | Prioritize running the success scenario first via the Smoke Test. |

## 8. Test Strategy
The validation approach is based exclusively on **manual black-box testing**, focusing on verifying functional authentication requirements and system behavior when handling user input.

### 8.1 Strategy Summary

| Test Level | Test Type | Test Techniques | Execution Mode |
| :--- | :--- | :--- | :--- |
| System Testing, UI Testing | Smoke Test, Functional, Black-Box | Equivalence Partitioning, Decision Table | Manual |

### 8.2 Execution Approach

1. **Smoke Test:**
   * Before executing the full test suite, a single critical scenario will be run manually: a successful login with `standard_user`.
   * **Goal:** Ensure stability and accessibility of the Sauce Demo environment. If this scenario fails, execution of the complete test suite will be suspended.

2. **Functional Testing & Business Rules:**
   * Guided by pre-defined Test Cases to validate access flows, locked-out users, invalid credentials, and required field validations.

3. **Applied Techniques:**
   * **Equivalence Partitioning:** Dividing input data into valid (success), invalid (incorrect credentials), and state (locked-out user) classes to avoid redundant testing.
   * **Decision Table:** Mapping combinations of inputs (username and password) to expected outcomes.

| Rule | Username | Password | Expected Outcome |
| :--- | :--- | :--- | :--- |
| R1 | Valid | Valid | Redirects to /inventory.html |
| R2 | Locked out | Valid | Error: user locked out |
| R3 | Non-existent | Filled | Error: username and password do not match |
| R4 | Valid | Invalid | Error: username and password do not match |
| R5 | Empty | Filled | Error: username is required |
| R6 | Filled | Empty | Error: password is required |
| R7 | Empty | Empty | Error: username is required |

## 9. Criteria
### 9.1 Entry Criteria
* Test cases defined and reviewed
* Test environment ready

### 9.2 Exit Criteria
* All test cases executed
* All identified defects documented
* Test evidence recorded for all failed test cases

### 9.3 Suspension Criteria
* Smoke Test failure (login with `standard_user`)
* Unavailability of the SauceDemo website

### 9.4 Resumption Criteria
* Successful re-execution of the Smoke Test
* Test environment stability restored

## 10. Test Environment
| Component | Details |
| :--- | :--- |
| **Application URL** | https://www.saucedemo.com |
| **Browser** | Mozilla Firefox 156.0 (64-bit) for Arch Linux |
| **Operating System** | Arch Linux |
| **Network** | Home Wi-Fi |
| **Device** | Desktop |
| **Test Tools** | GitHub, Markdown |

## 11. Test Data
| Profile | Username | Password |
| :--- | :--- | :--- |
| Valid | standard_user | secret_sauce |
| Locked out | locked_out_user | secret_sauce |
| Invalid | usuario_invalido | senha_invalida |
| Empty | (blank) | (blank) |

## 12. Estimates
| Activity | Estimated Effort |
| :--- | :--- |
| Test case creation | 2h |
| Smoke Test execution | 10 min |
| Full suite execution | 1h |
| Defect logging and evidence capture | 1h |
| **Total** | **~4h10m** |

**Timeline:** 09/21/2026 to 09/23/2026

## 13. Deliverables
* Test Plan
* Test Cases
* Bug Report
* Test Evidence

## 14. References
* SauceDemo: https://www.saucedemo.com
* ISO/IEC/IEEE 29119-3: Software and systems engineering — Software testing — Test documentation

## 15. Glossary
| Term | Definition |
| :--- | :--- |
| Smoke Test | A rapid test suite to verify that critical features are functional before running the full suite |
| Black-box | A testing technique that validates software behavior without inspecting its internal code |
| Equivalence Partitioning | A technique that groups inputs into classes expected to exhibit similar behavior |
| Decision Table | A structured technique used to map input combinations against expected output behaviors |
