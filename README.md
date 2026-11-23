# Appointify Web Application Security Assessment

A practical security assessment of the Appointify web platform, completed as part of a cybersecurity capstone project.

The work focused on evaluating application security controls, documenting observed weaknesses, and communicating remediation recommendations.

## Assessment Scope

- Authentication and password-reset behaviour
- Session management
- Role-based authorization and access control
- Input validation and injection resistance
- API responses and data exposure
- Business logic checks
- Transport security and HTTP security headers

## Methodology and Tools

Testing included manual application interaction, HTTP request interception and modification, role-based access checks, and review of network and browser responses.

Tools used:
- **Burp Suite:** request interception and application testing
- **Nmap:** service discovery
- **Wireshark:** network traffic inspection
- **Browser Developer Tools:** frontend and API behaviour analysis

## Findings Summary

The assessment identified areas where existing controls worked as expected, alongside weaknesses requiring remediation.

| Area | Observation | Assessment |
|---|---|---|
| Authorization | Tested role restrictions and JWT-protected access blocked the unauthorized actions attempted | Positive control observed in tested cases |
| IDOR checks | Cross-user access attempts were blocked in the tested scenarios | No IDOR confirmed in tested cases |
| Injection and XSS | Tested payloads did not demonstrate successful NoSQL injection or XSS | No exploit confirmed in tested cases |
| Login protection | No effective rate limiting, lockout, or CAPTCHA control was observed during testing | Hardening required |
| MFA | Multi-factor authentication was not available in the tested flow | Improvement recommended |
| Session handling | A session remained valid after the 30-minute observation point | Review session lifetime and invalidation policy |
| Password reset | Password-reset email flow did not work as expected during testing | Functional and security review required |
| Input validation | Phone-number validation accepted weak or insufficiently constrained input | Validation improvement required |
| HTTP headers | Content-Security-Policy and X-Frame-Options were not present in the observed responses | Security-header hardening recommended |
| Data exposure | Responses included implementation fields such as `_id` and `__v` | Review whether these fields are necessary to expose |
| Transport security | TLS 1.3 was observed | Positive configuration observed |

These observations are limited to the endpoints, accounts, test cases, and time of assessment. A failed test does not prove the absence of a vulnerability across the entire application.

## Overall Assessment

The tested application demonstrated working access-control protections in the scenarios exercised. The most important improvement areas were authentication hardening, session policy, password-reset reliability, input validation, and HTTP security headers.

The assessment did not establish that the application was free of vulnerabilities. Further testing and retesting would be required after remediation.

## Deliverables

The repository contains assessment documentation, including technical findings and remediation recommendations. Refer to the report files in the repository for the detailed evidence and testing context.

## What This Project Demonstrates

- Manual web application and API security testing
- Authentication and authorization review
- Request manipulation with Burp Suite
- Evidence-based finding documentation
- Risk communication and remediation planning

## Author

**Adekunle A. Joseph**

- [GitHub](https://github.com/JK-xpinn)
- [LinkedIn](https://www.linkedin.com/in/joseph-adekunle-87600b295)
- [Medium](https://medium.com/@spinnnate7)

## Disclaimer

This repository contains sanitized project documentation for educational and portfolio purposes. Testing was conducted within the project's authorized scope. Sensitive information has been omitted or adjusted where necessary.
