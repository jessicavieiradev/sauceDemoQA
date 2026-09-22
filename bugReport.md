### BUG-01: Display defect and text overflow (padding) on invalid login error message

| Field | Value |
| :--- | :--- |
| **Test Case** | LT03-R3, LT04-R4, LT09-R3 |
| **Description** | When attempting to log in with invalid credentials (invalid username/password, valid username/incorrect password, or uppercase username), the error message is displayed, but shows a visual UI flaw: the text is clipped at the top and bottom (text overflow) and the internal spacing (padding) of the red container is misaligned. |
| **Preconditions** | The user is on the login page (https://www.saucedemo.com) |
| **Steps to Reproduce** | **Scenario A (LT03-R3):**<br>1. Enter `usuario_invalido` in the Username field.<br>2. Enter `senha_invalida` in the Password field.<br>3. Click the "Login" button.<br><br>**Scenario B (LT04-R4):**<br>1. Enter `standard_user` in the Username field.<br>2. Enter `senha_invalida` in the Password field.<br>3. Click the "Login" button.<br><br>**Scenario C (LT09-R3):**<br>1. Enter `STANDARD_USER` in the Username field.<br>2. Enter `secret_sauce` in the Password field.<br>3. Click the "Login" button. |
| **Expected Result** | Login is blocked and the error message `"Epic sadface: Username and password do not match any user in this service"` must be displayed fully legible, centered, and with proper margins/padding. |
| **Actual Result** | Login is correctly blocked, but the error message presents a UI layout defect: the text is clipped at the top and bottom (text overflow) and the red container has misaligned padding across all 3 scenarios. |
| **Environment** | Arch Linux, Firefox |
| **Severity** | Low |
| **Priority** | Medium |
| **Status** | Open |
| **Reported by** | Jessica Vieira |
| **Evidence** | <img width="881" height="652" alt="invalid username, invalid password" src="https://github.com/user-attachments/assets/f2b1924e-a611-427e-bd30-5c9d027e5e3d" /> <img width="905" height="656" alt="valid username, invalid password" src="https://github.com/user-attachments/assets/d930c238-6351-4bfb-92f3-29a7e6a5a7d2" /> <img width="894" height="652" alt="uppercase username, valid password" src="https://github.com/user-attachments/assets/4a3d0207-a3e4-4e25-9ac2-ffa184940d0a" />
