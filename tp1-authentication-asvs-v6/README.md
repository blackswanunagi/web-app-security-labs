# Lab 1 — Authentication: OWASP ASVS V6 & PortSwigger labs

Study of **OWASP ASVS 5.0 chapter V6 (Authentication)**, then three authentication labs from **PortSwigger Web Security Academy** solved with **Burp Suite**, each mapped to the ASVS requirement it violates.

📄 Full report (French): [`TP1_Authentication_report.pdf`](TP1_Authentication_report.pdf)

## Part 1 — ASVS V6

Security objectives of the chapter, topics covered (password security, MFA, out-of-band and TOTP codes, recovery flows), mechanisms and risks reduced, and two requirements studied in detail — e.g. one-time recovery codes and TOTP codes must not be reusable, verified by checking that a second use is rejected and creates no session.

## Part 2 — Labs (all solved)

| Lab | Vulnerability | Attack | Fix (ASVS V6) |
|---|---|---|---|
| Username enumeration via different responses | Different error messages for unknown user vs wrong password | Burp Intruder: enumerate valid usernames, then brute-force the password | Generic error message, rate limiting / lockout |
| 2FA simple bypass | Session usable before the second factor is validated | Log in as the victim, skip the code page and request `/my-account` directly | Grant the session only after the full MFA flow |
| Password reset broken logic | Reset token not checked server-side | Replay the reset request with the token removed and another username | Validate a single-use, expiring token bound to the account; notify the user after a reset |

All tests were performed in PortSwigger's authorised lab environment; session cookies are masked in the report.
