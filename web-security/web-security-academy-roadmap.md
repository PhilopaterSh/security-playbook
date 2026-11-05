# Web Security Academy Master Roadmap

# Web Security Academy Master Roadmap

## Overview
A structured 17-week training curriculum covering **272 labs across 31 topics** in the PortSwigger Web Security Academy. Every topic is mapped to relevant chapters in four seminal industry books and two modern operational benchmarks:
- **WAHH:** The_Web_Application_Hackers_Handbook_-_Finding_and_Exploiting_Security_Flaws_2nd_Edition_by_Dafydd_Stuttard_Marcus_Pinto.pdf by Dafydd Stuttard & Marcus Pinto
- **OTG v4:** OWASP_Testing_Guide_v4.pdf by OWASP Foundation
- **WH101:** web-hacking-101.pdf by Peter Yaworski
- **BBB:** Bug_Bounty_Bootcamp.pdf by Vickie Li
- **DS2025:** Top Most Common Web Application Vulnerabilities, DeepStrike 2025 Industry Benchmark (Top 20 Web Vulnerabilities, breach statistics, and severity ranking)
- **PTC2025:** Web Application Penetration Testing Checklist, Phased tactical audit and penetration testing verification checklist
- **Procedure reference:** Cybersecurity Commands & Payloads Cheatsheet, reusable, scoped methods and tools linked from checklist cases
- **Field workflow:** Web Application Penetration Testing Field Guide, guided phase-by-phase assessment flow for applying the checklist and procedures during an authorized test
- **Engagement record:** Web Application Engagement Record Template, compact, per-assessment scope/evidence/status record; never use the learning roadmap or master checklist as a client-status ledger

---

## The Evidence-Based Study Protocol (7 Phases)
Upgraded 2026-11-03 from the original 4-step cycle using cognitive-science evidence: Dunlosky et al. 2013 ([PSI review](https://journals.sagepub.com/doi/abs/10.1177/1529100612453266)) — practice testing and distributed practice are the only high-utility techniques, while rereading is low-utility; the pretesting effect (Richland, Kornell & Kao — failed pre-attempts enhance later learning); the worked-example / expertise-reversal effects (Kalyuga et al.; [Nievelstein et al. 2013](https://www.sciencedirect.com/science/article/abs/pii/S0361476X12000677)); and interleaving over blocking (Rohrer — better retention and transfer despite feeling harder). For every topic, the study cycle follows this exact sequence:

0. **Pre-Attempt (P0):** Spend at most 10 minutes genuinely attempting one lab for the topic BEFORE studying it. Failure is expected and useful — the errorful generation activates prior knowledge and sharpens corrective learning.
1. **Theory & Deep Study (D):** Read the concepts from PortSwigger, WAHH, OTG v4, BBB, WH101, and cross-reference modern attack surfaces and breach impact in **DS2025** (Top Most Common Web Application Vulnerabilities). Books are consulted as references during retrieval and note-building, never reread passively.
2. **Worked-Pattern Study (W):** For each NEW technique class, study one fully worked solution pattern before attempting independent labs (worked-example effect for novices), then fade guidance and attempt alone as the class becomes familiar (expertise reversal).
3. **Atomic Vault Note Documentation:** Create/update the corresponding atomic note in the Vault following Technical Note Structure, ensuring real-world remediation and CVSS severity metrics are documented.
4. **Independent Labs, Interleaved (I):** Solve the topic's PortSwigger Academy labs independently with documented PoCs. Within each week, interleave lab types from at least two earlier topics instead of grinding a single block — higher error rate during practice is expected and does not mean learning failed.
5. **Field Verification & Review (R):** Verify attack vectors against the **PTC2025** checklist (Web Application Penetration Testing Checklist), run an interactive lock-in quiz, and complete the weekly synthesis to lock down intuition.
6. **Spaced Retrieval Re-Drill (S):** Every lock-in quiz question and failed lab enters a re-drill queue at expanding intervals (~1 week → ~3 weeks → before each phase synthesis). An item clears only at 100% on its re-drill — the same discipline that carried the HCIA sprint to a first-sitting pass.

**Operational tracker:** WSA Study Tracker — owns the per-node score log, the re-drill queue, and the agreed session cadence for this protocol.

**Traceability rule:** Roadmap checkboxes track learning and lab completion. During an authorized assessment, record WSTG and supplemental test dispositions only in that assessment's Web Application Engagement Record Template. The checklist owns test scope and case anchors; the Cheatsheet owns reusable procedures. A completed training lab is practice evidence, not an engagement test result.

---

## Phase Breakdown

### Week 0: Foundations, Methodology & Setup (4 Days)
- [x] **Day 1 (Study):** Web App Security Fundamentals & Core Defenses
  - **Books:** WAHH Ch. 1 & 2 | WH101 Ch. 1 & 19 | BBB Ch. 1 & 2
  - **Note:** Web Application Security Fundamentals
- [ ] **Day 2 (Study):** HTTP Protocol Mechanics & Burp Suite Proxying
  - **Books:** WAHH Ch. 3 | BBB Ch. 3 & 4
  - **Notes:** HTTP Protocol, Burp Suite
- [ ] **Day 3 (Study):** Application Mapping, Reconnaissance & Client-Side Control Bypasses
  - **Books:** WAHH Ch. 4 & 5 | BBB Ch. 5
  - **Note:** Web Reconnaissance Methodology
- [ ] **Day 4 (Review):** Week 0 Synthesis & Setup Validation

---

### Phase 1: Server-Side Topics (Weeks 1-6 / 115 Labs)

#### Week 1: SQL Injection (18 Labs)
- [ ] **Day 5 (Study):** SQL Injection Theory & Error/UNION-based Fundamentals
  - **Books:** WAHH Ch. 9 | WH101 Ch. 9 | BBB Ch. 11
  - **Note:** SQL Injection
- [ ] **Day 6 (Practice):** SQLi Labs 1-5 (Retrieving Hidden Data, Subverting Logic, UNION Attacks)
- [ ] **Day 7 (Practice):** SQLi Labs 6-10 (Examining Database Types, Blind SQLi with Conditional Responses)
- [ ] **Day 8 (Practice):** SQLi Labs 11-14 (Blind SQLi with Conditional Errors & Time Delays)
- [ ] **Day 9 (Finish Solving):** SQLi Labs 15-18 (Blind SQLi with Out-of-Band OAST Interactions)
- [ ] **Day 10 (Review):** Week 1 SQLi Review & Cheat Sheet Synthesis

#### Week 2: Authentication (14 Labs) & Path Traversal (6 Labs)
- [ ] **Day 11 (Study):** Authentication Flaws, 2FA Bypasses & Password Reset Vulnerabilities
  - **Books:** WAHH Ch. 6 & 7
  - **Note:** Authentication Vulnerabilities
  - **Modern authentication supplement:** Passkey/WebAuthn registration, origin/RP ID binding, credential lifecycle, recovery, and fallback behavior, Web Application Penetration Testing Checklist#^supp-webauthn-01 · Cybersecurity Commands & Payloads Cheatsheet#WebAuthn and Passkey Security Review
- [ ] **Day 12 (Practice):** Authentication Labs 1-5 (Brute-force, Username Enumeration, 2FA Bypasses)
- [ ] **Day 13 (Practice):** Authentication Labs 6-10 (Cookie-based Auth, Password Reset Logic Flaws)
- [ ] **Day 14 (Finish Solving):** Authentication Labs 11-14 (OAuth/SAML Auth Flaws, Offline Hash Cracking)
  - **Supplemental practice (outside the PortSwigger lab count):** In an approved sandbox or dedicated test application, trace passkey enrollment, sign-in, credential removal, account recovery, and fallback using tester-owned accounts; compare observations with the linked WebAuthn checklist and procedure.
- [ ] **Day 15 (Study):** Path Traversal & Arbitrary File Access
  - **Books:** WAHH Ch. 10
  - **Note:** Path traversal
- [ ] **Day 16 (Practice):** Path Traversal Labs 1-3 (Simple Traversal, Absolute Path Bypass, Traversal Sequences Stripped)
- [ ] **Day 17 (Finish Solving):** Path Traversal Labs 4-6 (Superfluous URL-decode, Null Byte Injection)
- [ ] **Day 18 (Review):** Week 2 Authentication & Traversal Review

#### Week 3: Access Control (13 Labs), Command Injection (5 Labs), Info Disclosure (5 Labs)
- [ ] **Day 19 (Study):** Access Control Flaws, Vertical/Horizontal Privilege Escalation & IDOR
  - **Books:** WAHH Ch. 8 | WH101 Ch. 16 | BBB Ch. 10
  - **Note:** Broken Access Control & IDOR
- [ ] **Day 20 (Practice):** Access Control Labs 1-5 (Unprotected Admin Functionality, Insecure Direct Object References)
- [ ] **Day 21 (Practice):** Access Control Labs 6-9 (Multi-step Process Flaws, Referer-based Access Control)
- [ ] **Day 22 (Finish Solving):** Access Control Labs 10-13 (URL-matching Bypasses, Method-based Access Controls)
- [ ] **Day 23 (Study):** OS Command Injection Mechanics
  - **Books:** WAHH Ch. 10 | WH101 Ch. 12 | BBB Ch. 18
  - **Note:** Remote Code Execution (RCE)#1. OS Command Injection
- [ ] **Day 24 (Finish Solving):** Command Injection Labs 1-5 (Simple, Blind with Time Delays, Blind with Output Redirection & OOB)
- [ ] **Day 25 (Study):** Information Disclosure & Leakage Vectors
  - **Books:** WAHH Ch. 15 | BBB Ch. 21
  - **Note:** Information disclosure
- [ ] **Day 26 (Finish Solving):** Information Disclosure Labs 1-5 (Error Messages, Debug Pages, Source Code Exposure)
- [ ] **Day 27 (Review):** Week 3 Access Control & Injection Review

#### Week 4: Business Logic (11 Labs), File Upload (7 Labs), Race Conditions (6 Labs)
- [ ] **Day 28 (Study):** Business Logic Flaws & Flawed Assumptions
  - **Books:** WAHH Ch. 11 | WH101 Ch. 18 | BBB Ch. 17
  - **Note:** Business Logic Vulnerabilities
- [ ] **Day 29 (Practice):** Business Logic Labs 1-4 (Excessive Trust in Client Controls, High-level Logic Flaws)
- [ ] **Day 30 (Practice):** Business Logic Labs 5-8 (Low-level Flaws, Inconsistent Handling of Exceptional Input)
- [ ] **Day 31 (Finish Solving):** Business Logic Labs 9-11 (Domain-specific Logic Flaws, Authentication Logic Bypasses)
- [ ] **Day 32 (Study):** File Upload Vulnerabilities & Execution Paths
  - **Books:** WAHH Ch. 10 | WH101 Ch. 12 | BBB Ch. 18
  - **Note:** File upload
- [ ] **Day 33 (Practice):** File Upload Labs 1-4 (Remote Code Execution via Web Shell, Content-Type Bypass, Path Traversal Execution)
- [ ] **Day 34 (Finish Solving):** File Upload Labs 5-7 (Blacklist Bypass via .htaccess, Obfuscated Extensions, Polyglots)
- [ ] **Day 35 (Study):** Race Conditions & Multi-Threaded State Vulnerabilities
  - **Books:** WH101 Ch. 15 | BBB Ch. 12
  - **Note:** Time-of-Check to Time-of-Use (TOCTOU)
- [ ] **Day 36 (Practice):** Race Condition Labs 1-3 (Limit Overrun, Single-packet Attacks, Bypassing Rate Limits)
- [ ] **Day 37 (Finish Solving):** Race Condition Labs 4-6 (Multi-endpoint Race Conditions, Hidden Multi-step State Machines)
- [ ] **Day 38 (Review):** Week 4 Logic, Uploads & Race Conditions Review

#### Week 5: SSRF (7 Labs), XXE (9 Labs), NoSQL Injection (4 Labs)
- [ ] **Day 39 (Study):** Server-Side Request Forgery (SSRF) Mechanics & Cloud Metadata Attacks
  - **Books:** WAHH Ch. 10 | WH101 Ch. 10 | BBB Ch. 13
  - **Note:** Server-side request forgery (SSRF)
- [ ] **Day 40 (Practice):** SSRF Labs 1-4 (Basic SSRF against Localhost, Backend Systems, Whitelist/Blacklist Bypasses)
- [ ] **Day 41 (Finish Solving):** SSRF Labs 5-7 (Blind SSRF with Out-of-Band Detection, Shellshock Exploitation via SSRF)
- [ ] **Day 42 (Study):** XML External Entity (XXE) Injection
  - **Books:** WAHH Ch. 10 | WH101 Ch. 11 | BBB Ch. 15
  - **Note:** XML External Entity (XXE)
- [ ] **Day 43 (Practice):** XXE Labs 1-5 (File Retrieval via XXE, SSRF via XXE, Blind XXE via Out-of-Band)
- [ ] **Day 44 (Finish Solving):** XXE Labs 6-9 (Blind XXE with Error Messages, Repurposing Local DTDs, XInclude Attacks)
- [ ] **Day 45 (Study):** NoSQL Injection & Syntax Manipulation
  - **Books:** WAHH Ch. 9 | BBB Ch. 11
  - **Note:** [PortSwigger NoSQL injection](https://portswigger.net/web-security/nosql-injection) | Cybersecurity Commands & Payloads Cheatsheet#4.7.5.6: Testing for NoSQL Injection
- [ ] **Day 46 (Finish Solving):** NoSQLi Labs 1-4 (MongoDB Syntax Injection, Authentication Bypass, Data Extraction)
- [ ] **Day 47 (Review):** Week 5 SSRF, XXE & NoSQLi Review

#### Week 6: API Testing (5 Labs) & Web Cache Deception (5 Labs)
- [ ] **Day 48 (Study):** API Reconnaissance, Hidden Endpoints & Mass Assignment
  - **Books:** WAHH Ch. 3 | BBB Ch. 24
  - **Note:** [PortSwigger API testing](https://portswigger.net/web-security/api-testing) | Cybersecurity Commands & Payloads Cheatsheet#API Object Authorization and Mass Assignment
- [ ] **Day 49 (Finish Solving):** API Testing Labs 1-5 (API Documentation Discovery, Parameter Tampering, Mass Assignment)
- [ ] **Day 50 (Study):** Web Cache Deception Vulnerabilities
  - **Reference:** Academic Paper *Cached and Confused*
  - **Note:** [PortSwigger Web cache deception](https://portswigger.net/web-security/web-cache-deception)
- [ ] **Day 51 (Finish Solving):** Web Cache Deception Labs 1-5 (Path Confusion, Delimiter Misconfigurations, Static Extension Exploits)
- [ ] **Day 52 (Review):** Week 6 API & Cache Deception Review + Phase 1 Consolidation

---

### Phase 2: Client-Side Topics (Weeks 7-10 / 60 Labs)

#### Week 7: XSS: Part 1: Reflected & Stored Fundamentals (15 Labs)
- [ ] **Day 53 (Study):** Cross-Site Scripting (XSS) Foundations & Contexts
  - **Books:** WAHH Ch. 12 | WH101 Ch. 7 | BBB Ch. 6
  - **Note:** Cross-site scripting (XSS)
- [ ] **Day 54 (Practice):** XSS Labs 1-5 (Reflected XSS, Stored XSS, HTML Context Injection)
- [ ] **Day 55 (Practice):** XSS Labs 6-10 (Attribute Context Injection, JavaScript Context String Escapes)
- [ ] **Day 56 (Finish Solving):** XSS Labs 11-15 (Anchor Href Context, Event Handlers, Tag Whitelist Bypasses)
- [ ] **Day 57 (Review):** Week 7 Basic XSS Review

#### Week 8: XSS: Part 2: Advanced Sinks, DOM Invader & Filter Bypasses (15 Labs)
- [ ] **Day 58 (Study):** Advanced DOM XSS, DOM Invader Tooling & CSP Bypasses
  - **Books:** WAHH Ch. 12 | BBB Ch. 6
  - **Note:** Cross-site scripting (XSS) | [PortSwigger DOM-based XSS](https://portswigger.net/web-security/cross-site-scripting/dom-based)
- [ ] **Day 59 (Practice):** Advanced XSS Labs 16-20 (DOM XSS in document.write, innerHTML, jQuery Sinks)
- [ ] **Day 60 (Practice):** Advanced XSS Labs 21-25 (DOM XSS in AngularJS, Web Messages, SVG Payloads)
- [ ] **Day 61 (Finish Solving):** Advanced XSS Labs 26-30 (Reflected XSS with Custom Tags, CSP Bypasses, Cookie Stealing via XSS)
- [ ] **Day 62 (Review):** Week 8 Advanced XSS Review

#### Week 9: CSRF (12 Labs) & Clickjacking (5 Labs)
- [ ] **Day 63 (Study):** Cross-Site Request Forgery (CSRF) & Token Defense Flaws
  - **Books:** WAHH Ch. 13 | WH101 Ch. 4 | BBB Ch. 9
  - **Note:** Cross-Site Request Forgery (CSRF)
- [ ] **Day 64 (Practice):** CSRF Labs 1-4 (No Defenses, Validation Dependent on Request Method, Token Validation Depending on Token Presence)
- [ ] **Day 65 (Practice):** CSRF Labs 5-8 (CSRF Token Tied to Non-Session Cookie, Cookie Duplication Bypass, SameSite Cookie Bypasses)
- [ ] **Day 66 (Finish Solving):** CSRF Labs 9-12 (SameSite Lax Bypass via Method Override, Referer Header Validation Bypasses)
- [ ] **Day 67 (Study):** Clickjacking & UI Redressing Attacks
  - **Books:** WAHH Ch. 13 | BBB Ch. 8
  - **Note:** Clickjacking
- [ ] **Day 68 (Finish Solving):** Clickjacking Labs 1-5 (Basic Clickjacking, CSRF Protection Bypass, Prefilled Form Data, Frame Busting Bypasses)
- [ ] **Day 69 (Review):** Week 9 CSRF & Clickjacking Review

#### Week 10: CORS (3 Labs), DOM-Based Flaws (7 Labs), WebSockets (3 Labs)
- [ ] **Day 70 (Study):** Cross-Origin Resource Sharing (CORS) Misconfigurations
  - **Books:** WAHH Ch. 13 | BBB Ch. 19
  - **Note:** CORS Misconfiguration
- [ ] **Day 71 (Finish Solving):** CORS Labs 1-3 (Arbitrary Origin Trust, Null Origin Trust, Trusted Insecure Subdomains)
- [ ] **Day 72 (Study):** General DOM-based Vulnerabilities (Open Redirection, Cookie Manipulation, Web Message Sinks)
  - **Note:** [PortSwigger DOM-based vulnerabilities](https://portswigger.net/web-security/dom-based)
- [ ] **Day 73 (Practice):** DOM Labs 1-4 (DOM Open Redirection, DOM Cookie Manipulation, DOM Clobbering)
- [ ] **Day 74 (Finish Solving):** DOM Labs 5-7 (DOM Clobbering Enabling XSS, Bypassing HTML Sanitizers)
- [ ] **Day 75 (Study):** WebSockets Protocol & Vulnerabilities
  - **Books:** WAHH Ch. 3
  - **Note:** Cybersecurity Commands & Payloads Cheatsheet#WSTG-CLNT-10: Test WebSockets
- [ ] **Day 76 (Finish Solving):** WebSockets Labs 1-3 (Manipulating WebSocket Messages, Cross-Site WebSocket Hijacking - CSWSH)
- [ ] **Day 77 (Review):** Week 10 Client-Side Review + Phase 2 Consolidation

---

### Phase 3: Advanced Topics (Weeks 11-17 / 97 Labs)

#### Week 11: Insecure Deserialization (10 Labs)
- [ ] **Day 78 (Study):** Object Serialization & Insecure Deserialization Internals
  - **Books:** BBB Ch. 14
  - **Note:** Insecure Deserialization
- [ ] **Day 79 (Practice):** Deserialization Labs 1-5 (Modifying Serialized Objects, PHP Object Injection, Arbitrary Object Injection)
- [ ] **Day 80 (Finish Solving):** Deserialization Labs 6-10 (Java Deserialization with Apache Commons Collections, Custom Gadget Chains, PHAR Deserialization)
- [ ] **Day 81 (Review):** Week 11 Deserialization Review

#### Week 12: JWT Attacks (8 Labs), GraphQL (5 Labs), Essential Skills (2 Labs)
- [ ] **Day 82 (Study):** JSON Web Token (JWT) Architecture & Cryptographic Flaws
  - **Books:** BBB Ch. 20
  - **Note:** JWT Vulnerabilities
- [ ] **Day 83 (Practice):** JWT Labs 1-4 (Unverified Signature, Flawed Signature Verification, Weak Signing Keys, Header Parameter Injections - jku/kid)
- [ ] **Day 84 (Finish Solving):** JWT Labs 5-8 (Algorithm Confusion HMAC vs RSA, Cross-Service Key Confusion)
- [ ] **Day 85 (Study):** GraphQL API Architectures & Introspection
  - **Books:** BBB Ch. 24
  - **Note:** [PortSwigger GraphQL API vulnerabilities](https://portswigger.net/web-security/graphql) · Web Application Penetration Testing Checklist#^supp-graphql-01 · Cybersecurity Commands & Payloads Cheatsheet#GraphQL API Security Review
- [ ] **Day 86 (Finish Solving):** GraphQL Labs 1-5 (Introspection Querying, Direct Object Access, Bypassing Rate Limits via Aliases, CSRF over GraphQL)
  - **Field mapping:** Relate lab findings to intended introspection policy, object/field authorization, and safe query-cost controls; do not treat enabled introspection alone as a vulnerability or run resource-exhaustion tests against production.
- [ ] **Day 87 (Finish Solving):** Essential Skills Labs 1-2 (Multi-Step Vulnerability Chaining & Practical Exploitation)
- [ ] **Day 88 (Review):** Week 12 JWT & GraphQL Review

#### Week 13: OAuth 2.0 (6 Labs) & Server-Side Template Injection (7 Labs)
- [ ] **Day 89 (Study):** OAuth 2.0 Grant Types & Authentication Flaws
  - **Books:** WH101 Ch. 17 | BBB Ch. 20
  - **Note:** OAuth 2.0 Vulnerabilities
- [ ] **Day 90 (Practice):** OAuth Labs 1-3 (Authentication Bypass via Implicit Flow, Flawed CSRF Protection, Account Linking Bypasses)
- [ ] **Day 91 (Finish Solving):** OAuth Labs 4-6 (Stealing OAuth Tokens via Redirect URI Manipulation, Open Redirection Chaining)
- [ ] **Day 92 (Study):** Server-Side Template Injection (SSTI) Engines (Jinja2, Twig, Freemarker)
  - **Books:** WH101 Ch. 8 | BBB Ch. 16
  - **Note:** Remote Code Execution (RCE)#2. Server-Side Template Injection (SSTI)
- [ ] **Day 93 (Practice):** SSTI Labs 1-4 (Basic SSTI, Code Execution via Template Engine Discovery, Sandboxed Template Engines)
- [ ] **Day 94 (Finish Solving):** SSTI Labs 5-7 (Server-side Template Injection in Unknown Contexts, SSTI via Information Disclosure)
- [ ] **Day 95 (Review):** Week 13 OAuth & SSTI Review

#### Week 14: Web Cache Poisoning (13 Labs)
- [ ] **Day 96 (Study):** Web Caching Architecture, Cache Keys & Unkeyed Inputs
  - **Note:** [PortSwigger Web cache poisoning](https://portswigger.net/web-security/web-cache-poisoning)
- [ ] **Day 97 (Practice):** Cache Poisoning Labs 1-5 (Unkeyed Headers, Unkeyed Port, Parameter Cloaking)
- [ ] **Day 98 (Practice):** Cache Poisoning Labs 6-9 (Fat GET Requests, Multiple Headers, Normalized Cache Keys)
- [ ] **Day 99 (Finish Solving):** Cache Poisoning Labs 10-13 (DOM XSS via Cache Poisoning, Cache Key Injection, Internal Cache Poisoning)
- [ ] **Day 100 (Review):** Week 14 Cache Poisoning Review

#### Week 15: HTTP Host Header Attacks (7 Labs) & Web LLM Attacks (7 Labs)
- [ ] **Day 101 (Study):** HTTP Host Header Routing, Virtual Hosts & Password Reset Poisoning
  - **Books:** WAHH Ch. 3 | BBB Ch. 3
  - **Note:** [PortSwigger HTTP Host header attacks](https://portswigger.net/web-security/host-header) | Cybersecurity Commands & Payloads Cheatsheet#WSTG-INPV-17: Test for Host Header Injection
- [ ] **Day 102 (Finish Solving):** Host Header Labs 1-7 (Password Reset Poisoning, Web Cache Poisoning via Host Header, SSRF via Flawed Host Header Parsing)
- [ ] **Day 103 (Study):** Web Large Language Model (LLM) Attacks & Indirect Prompt Injections
  - **Note:** [PortSwigger Web LLM attacks](https://portswigger.net/web-security/llm-attacks) · Web Application Penetration Testing Checklist#^supp-llm-01 · Cybersecurity Commands & Payloads Cheatsheet#LLM-Integrated Feature Security Review
- [ ] **Day 104 (Finish Solving):** Web LLM Labs 1-7 (Direct Prompt Injection, Indirect Prompt Injection, Exploiting Insecure Output Handling, Excessive Agency)
  - **Field mapping:** Use OWASP GenAI 2025 terminology: LLM01 Prompt Injection, LLM05 Improper Output Handling, and LLM06 Excessive Agency. Keep lab exploits inside their provided sandbox; use synthetic data and inert actions for authorized application reviews.
- [ ] **Day 105 (Review):** Week 15 Host Header & LLM Attacks Review

#### Week 16: HTTP Request Smuggling (22 Labs: The Deepest Protocol Exploit)
- [ ] **Day 106 (Study 1):** HTTP/1.1 Parsing Discrepancies (Content-Length vs Transfer-Encoding)
  - **Books:** WAHH Ch. 3
  - **Note:** HTTP Request Smuggling
- [ ] **Day 107 (Study 2):** Advanced Request Smuggling (HTTP/2 Desync, Request Tunneling, H2.CL & H2.TE)
- [ ] **Day 108 (Practice):** Request Smuggling Labs 1-5 (Basic CL.TE, Basic TE.CL, Obfuscating TE Header)
- [ ] **Day 109 (Practice):** Request Smuggling Labs 6-10 (Smuggling to Bypass Front-end Security Controls, Revealing Front-end Request Rewriting)
- [ ] **Day 110 (Practice):** Request Smuggling Labs 11-15 (Capturing Other Users' Requests, Exploiting XSS via Smuggling)
- [ ] **Day 111 (Practice):** Request Smuggling Labs 16-19 (HTTP/2 Request Smuggling, H2.CL, H2.TE, Request Splitting via CRLF)
- [ ] **Day 112 (Finish Solving):** Request Smuggling Labs 20-22 (HTTP/2 Request Tunneling, Response Queue Poisoning)
- [ ] **Day 113 (Review):** Week 16 Request Smuggling Master Synthesis

#### Week 17: Prototype Pollution (10 Labs) & BSCP Certification Readiness
- [ ] **Day 114 (Study):** Prototype Pollution Mechanics (Client-Side & Server-Side NodeJS)
  - **Note:** [PortSwigger Prototype pollution](https://portswigger.net/web-security/prototype-pollution)
- [ ] **Day 115 (Practice):** Prototype Pollution Labs 1-5 (DOM XSS via Client-Side Prototype Pollution, Flawed Sanitization Bypasses)
- [ ] **Day 116 (Finish Solving):** Prototype Pollution Labs 6-10 (Server-Side Prototype Pollution, Remote Code Execution via Child Process Manipulation)
- [ ] **Day 117 (Practice Exam):** Burp Suite Certified Practitioner (BSCP) Mystery Lab Challenge
- [ ] **Day 118 (Practice Exam):** Official Practice Exam Simulation
- [ ] **Day 119 (Final Review):** Full Roadmap Completion & Certification Readiness Sign-Off

---

## Related Notes

- Web Security MOC
- Vulnerabilities MOC
- Top Most Common Web Application Vulnerabilities
- Web Application Penetration Testing Checklist
- Web Application Engagement Record Template
- Cybersecurity Commands & Payloads Cheatsheet
- Web Application Security Fundamentals
- Burp Suite

## Resources

Sources and references are stored in this note's `source` / `references` properties.
