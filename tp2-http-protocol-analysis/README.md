# Lab 2 — HTTP protocol analysis (curl & Wireshark)

HTTP exchanges with `gaia.cs.umass.edu` captured and analysed with **Wireshark** (filter `http`) and reproduced with **curl**, based on the Kurose–Ross Wireshark HTTP lab.

📄 Full report (French): [`TP2_HTTP_analysis_report.pdf`](TP2_HTTP_analysis_report.pdf)

| Task | What was analysed |
|---|---|
| 1. Basic GET / response | Request line, HTTP version, status `200 OK`, `Server`, `Last-Modified`, `ETag`, `Content-Length`, `Content-Type`; HEAD vs GET (headers only vs body) |
| 2. Conditional GET | First request without `If-Modified-Since` (body downloaded), second request with `If-Modified-Since` → **`304 Not Modified`**, no body: how browser caching saves bandwidth |
| 3. Wireshark trace | Observing and answering questions on a captured HTTP exchange |
| 4. Embedded objects | An HTML page with images triggers one extra GET per embedded object |

```bash
curl.exe -v -c cookies.txt -b cookies.txt http://gaia.cs.umass.edu/wireshark-labs/<page>.html
curl.exe -v -H "If-Modified-Since: <Last-Modified value>" http://gaia.cs.umass.edu/wireshark-labs/<page>.html
```

**Why it matters for security:** reading raw HTTP (methods, headers, status codes, cookies, caching) is the basis of web testing with Burp Suite and of analysing web traffic and logs in a SOC.

The reference traces are the official ones from the [Kurose–Ross Wireshark labs](https://gaia.cs.umass.edu/kurose_ross/wireshark.php).
