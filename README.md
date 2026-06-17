# API Security Risk Analysis

A read-only API security risk assessment of two public test APIs  **JSONPlaceholder** and **ReqRes** produced as **Cyber Security Task 3 (2026)** for **Future Interns**.

The goal is to think like a security consultant: identify common API security risks, assess authentication and access control, explain the risks in plain business language, and suggest clear remediation steps. No exploitation was performed  only risk identification.

---

## Scope & Ethics

**Allowed and performed**
- Testing public / demo APIs
- Read-only requests (GET)
- Documentation-based analysis
- Inspection of headers, tokens and responses

**Not allowed (never performed)**
- Exploitation or bypass attempts
- Flooding / denial-of-service testing
- Attacking private or production APIs

All testing was strictly ethical and legal.

---

## APIs Tested

| API | Base URL | Authentication |
|-----|----------|----------------|
| JSONPlaceholder | https://jsonplaceholder.typicode.com | None (open) |
| ReqRes | https://reqres.in | API key required |

---

## Tools Used

- **Postman** — sending requests and inspecting responses and headers
- **Firefox DevTools** — reading documentation and observing traffic
- **Official API documentation** (JSONPlaceholder, ReqRes)
- **Microsoft Word** — writing the final report

---

## Methodology

1. Select the test APIs (JSONPlaceholder and ReqRes)
2. Read the documentation of each API
3. Test the endpoints with Postman
4. Inspect authentication requirements, headers and response data
5. Identify security risks
6. Classify the severity of each risk (Low / Medium / High)
7. Propose remediation steps
8. Document all findings in a professional report

---

## Key Findings (summary)

| No. | Risk | API | Severity |
|-----|------|-----|----------|
| 1 | Open / unauthenticated endpoint | JSONPlaceholder | High |
| 2 | Excessive data exposure (email, phone, address, GPS) | JSONPlaceholder | High |
| 3 | Broken Object Level Authorization (BOLA / IDOR) | JSONPlaceholder | High |
| 4 | Permissive CORS configuration | JSONPlaceholder | Medium |
| 5 | Missing security headers (HSTS, X-Frame-Options, CSP) | JSONPlaceholder | Low |
| 6 | Technical information disclosure (X-Powered-By) | JSONPlaceholder | Low |

**Positive findings:** rate limiting active (`x-ratelimit-limit: 1000`), MIME-sniffing protection (`x-content-type-options: nosniff`), and authentication correctly enforced by ReqRes (401 without a valid key).

Full analysis, business impact and remediation are in the report under `report/`.


---

## How to Reproduce

1. Open Postman.
2. Send a `GET` request to `https://jsonplaceholder.typicode.com/users` and inspect the response body and headers.
3. Repeat with `/users/1`, `/users/2`, `/users/9999` and `/users/abc` to observe object access, BOLA and input handling.
4. Send a `GET` request to `https://reqres.in/api/users` without an API key to observe the `401 Unauthorized` response.

---

## References

- OWASP API Security Top 10  official OWASP project
- API Security Checklist (shieldfy)
- JSONPlaceholder and ReqRes documentation

---

## Author

Prepared by: **Assia EL MOURTADAH** , Future Interns — Cyber Security Task 3 (2026)
