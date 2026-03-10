# Day-73-100-Days-challenge-in-cybersecurity
# DVWA Lab: Brute Force Analysis (Low vs. Medium)

## 📋 Overview
An analysis of Brute Force vulnerabilities within the Damn Vulnerable Web Application (DVWA), contrasting simple server-side delays with robust multi-layered defense strategies.

## 🔍 Key Findings

### 1. Low Security (The "Open Door")
- **Vulnerability:** Zero server-side validation or request throttling.
- **Impact:** High-speed automated attacks (Hydra/Burp Suite) can attempt thousands of credentials per minute.
- **The Lesson:** Without logic to distinguish between the 1st and 1,000,000th request, the server is inherently compromised.

### 2. Medium Security (The "Speed Bump")
- **Mechanism:** Implementation of a `sleep(2)` delay upon failed login attempts.
- **Flaw:** While it prevents "machine-gun" style attacks, it does not address the underlying vulnerability. 
- **The Math:** - Password List: 100 entries
  - Delay: 2 seconds per attempt
  - **Total Added Time:** ~3 minutes 20 seconds.
- **Conclusion:** Delay only changes the *Time-to-Compromise*, it does not prevent it.

## 🛡️ The Blueprint for Real Protection: Defense in Depth
To secure a login portal, a layered approach is required:

| Measure | Purpose |
| :--- | :--- |
| **Rate Limiting** | Blocks requests per IP/User after a threshold. |
| **Account Lockout** | Freezes account after 3-5 failed attempts. |
| **CAPTCHA** | Ensures the user is human, breaking automation. |
| **2FA / MFA** | Adds a secondary "possession" factor. |
| **Strong Passwords** | Increases entropy to make brute-forcing computationally unfeasible. |

## 🖼️ Infographics
*(Insert your generated images here using `![Description](image-link)`)*
