# Web Application Security Labs

Hands-on web application security labs from the course *Sécurité des applications et des services* (IT Security engineering cycle, FST Guéliz, Prof. Yassine Sadqi). Each lab follows the same method: **exploit in an authorised lab → explain the root cause → propose a server-side fix → define validation and regression tests.**

| Lab | Topic | Tools |
|---|---|---|
| [Lab 1](tp1-authentication-asvs-v6/) | Authentication: OWASP ASVS V6, username enumeration, 2FA bypass, broken password reset | Burp Suite, PortSwigger Web Security Academy |
| [Lab 2](tp2-http-protocol-analysis/) | HTTP protocol analysis: headers, conditional GET / `304`, embedded objects | Wireshark, curl |
| [Lab 3](tp3-broken-access-control/) | Broken access control: IDOR (horizontal) and unprotected admin panel (vertical) | Burp Suite, PortSwigger Web Security Academy |
| [Lab 4](tp4-file-upload-xss-lfi-command-injection/) | Unrestricted file upload, reflected & stored XSS, LFI, OS command injection | Kali Linux, Metasploit, msfvenom, DVWA / Metasploitable 2 |

> ⚠️ All exploitation was performed only in intentionally vulnerable, authorised lab environments. Never test these techniques on systems you are not allowed to test.

**Author:** Hiba El Hjouji — Cybersecurity engineering student, FST Guéliz (Université Cadi Ayyad).
