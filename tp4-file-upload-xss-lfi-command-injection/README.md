# Lab 4 — File upload, XSS, LFI & OS command injection

Four web attack scenarios against **DVWA** (security level *low*) on **Metasploitable 2**, from **Kali Linux** with **Metasploit**, each followed by a vulnerability sheet (C/I/A impact, server-side fixes) and regression tests.

👥 Joint lab — **Hiba El Hjouji** & **Ikram Ezziouani**
📄 Full report (French): [`TP4_Web_Attacks_report.pdf`](TP4_Web_Attacks_report.pdf) · Screenshots: [`figures/`](figures/)

| # | Vulnerability | What we did | Server-side fix |
|---|---|---|---|
| 1 | **Unrestricted file upload** | Generated a PHP Meterpreter payload with `msfvenom`, uploaded it, triggered it from the browser → Meterpreter session | Check real MIME type, store uploads outside the web root, random names, no script execution in the upload folder |
| 2.1 | **Reflected XSS** | `<script>alert(document.cookie)</script>` exposed `PHPSESSID`; injected a fake login form exfiltrating credentials to a netcat listener | Output encoding (`htmlspecialchars`), Content Security Policy, `HttpOnly` cookies |
| 2.2 | **Stored XSS** | Same payload stored in the guestbook, re-executed for every visitor without re-injection | Same as above, plus sanitising stored content |
| 3 | **Local File Inclusion** | `?page=../../../../../etc/passwd` returned the system account list | Whitelist of includable files, disable `allow_url_include` / `allow_url_fopen`, reject `../` |
| 4 | **OS command injection** | `IP && ls -la`, then Metasploit `web_delivery` → Meterpreter as `www-data` | Strict IP validation, no shell commands built from user input, least-privilege service account |

**Common root cause:** the server trusts client input — file type, displayed text, file path or command argument — without validating it.

Each fix comes with validation and regression tests (T1–T7 in the report): the attack must now fail, and the legitimate feature (image upload, ping…) must still work.

> All attacks were performed in an isolated lab (Kali Linux, Metasploitable 2/DVWA) — never against real systems.
