# Bug Bounty Learning Resources

> [!info] Navigation
> NTI Bug Bounty Course Notes | NTI Bug Bounty Session Links | Bug BountyPrograms

# Bug Bounty Learning Resources

A curated list of resources, tools, and notes for bug bounty hunting.

## 1. General Learning & Methodology

- **OWASP WSTG (Web Security Testing Guide)**
  - [Main Page](https://owasp.org/www-project-web-security-testing-guide/stable/)
  - [Web Application Security Testing Guide](https://owasp.org/www-project-web-security-testing-guide/stable/4-Web_Application_Security_Testing/)
  - !Attachments/AI Security/Pasted image 20250913121651.png

- **MITRE ATT&CK**
  - [Homepage](https://attack.mitre.org/)
  - !Attachments/AI Security/Pasted image 20250913122359.png

- **NahamSec's Recon Methodology**
  > When it comes down to recon, it is usually divided into two main pillars. The first one being `asset discovery` and the second one being `content discovery`. The goal of asset discovery is to find as many assets that we can hack on (domains, subdomains, IP addresses). Content discovery is where you look for content to hack on (Google Dorking, brute forcing files/directories, scraping JS files, crawling).

### AI-assisted research cascade

Use LLM Agent Architecture and Feedback Standard#Research Cascade Protocol for Security Agents when a verified, in-scope behavior suggests related behavior or additional implications worth checking. Keep generated hypotheses separate from evidence and review authorization before testing. In PortSwigger's usage, a discovery can seed conceptually related discoveries, including on other targets; this differs from bug chaining. The follow-up model evaluation is explicitly exploratory and does not establish intentional model sabotage or a universal performance rule. Independent pentest-agent studies support adjacent ideas such as state retention, explicit task planning, feedback, and verification, but do not test this named method or our prompt: [EMNLP 2025 study](https://aclanthology.org/2025.emnlp-main.802/) · [IJCAI 2026 study](https://www.ijcai.org/proceedings/2026/725). See the full evidence assessment and limitations in the canonical protocol.

## 2. Learning Platforms & Communities

### Official Researcher Training, Program Rules, and Reporting Guidance

Use these sources for different purposes; none of their general training material grants permission to test a live target.

#### Safe practice and learning

- [Hacker101](https://www.hackerone.com/hackers/hacker101), free web-security lessons and the [Hacker101 CTF](https://ctf.hacker101.com/about), which is explicitly designed as a safe learning environment. Use its CTF for hands-on practice before applying techniques to authorized programs.
- [Bugcrowd University](https://www.bugcrowd.com/bugcrowd-university/), Bugcrowd's researcher education hub. Its content and availability may change; use it as supplementary training alongside the structured Web Security Academy Master Roadmap.
- [Google Bug Hunter University](https://bughunters.google.com/learn), Google's learning material on vulnerability reporting, attack scenarios, tool-output verification, and examples of findings that do not qualify under Google's program. Treat its acceptance and scope guidance as Google-program-specific.

#### Program rules and reporting quality

- [HackerOne Quality Reports](https://docs.hackerone.com/en/articles/8475116-quality-reports), a report-writing reference for clear reproduction steps, impact, and supporting evidence. [HackerOne Safe Harbor guidance](https://docs.hackerone.com/en/articles/8494502-safe-harbor-overview-faq) also explains that safe harbor does not expand the program's explicitly defined assets.
- [Bugcrowd: Reporting a Bug](https://docs.bugcrowd.com/researchers/reporting-managing-submissions/reporting-a-bug/), current submission fields and report-quality guidance, including target, vulnerability details, reproduction, and demonstrated impact.
- [Intigriti: How to Write and Submit a Good Report](https://kb.intigriti.com/en/articles/5379086-how-to-write-and-submit-a-good-report) and [Triage Standards](https://kb.intigriti.com/en/articles/10335710-intigriti-triage-standards), report reproduction and impact guidance plus an example of platform-specific scope and severity handling. Always check the selected program's current brief for its own rules.
- [disclose.io Vulnerability Disclosure Policy](https://disclose.io/framework/terms/vdp/), vendor-neutral VDP policy wording to help understand common policy elements such as scope, safe harbor, data minimization, and reporting channels. It is a policy model, not authorization to test any system.

> [!IMPORTANT]
> Before any live testing, read the target's current program brief and confirm the exact asset and technique are permitted. Platform training, public reports, safe-harbor examples, and scope-assistant warnings are references; they do not override the program's policy or independently authorize testing. See the Web Application Penetration Testing Field Guide for the live-engagement gate and test sequence.

### Notion
- [NTI Boot camp](https://cold-pyramid-f00.notion.site/NTI-Boot-camp-2436a7a7d31380e8981bc14fcf9c0a08?authuser=0)
- [POCs (Proof of Concepts)](https://www.notion.so/POC-1bd6a7a7d3138018a752e762825052ca)
- [Business Logic Vulnerabilities](https://www.notion.so/Business-Logic-Vulnerabilities-25ac1516b2bb806b99f2cd2e422af2a7)
- [Android Pentesting Notes (A0xTrojan)](https://www.notion.so/Android-Pentesting-A0xTrojan-17b90050c67180d8a453fb4dfb6cfd2c?authuser=0)

### YouTube Channels & Videos
- **Daoud Youssef**
  - [Channel Link](https://www.youtube.com/@daoudyoussef7999/videos)
  - [How to approach a bug bounty program](https://youtu.be/LgnT7Hsh4lE)
  - [How To Fail In Bug Bounty](https://youtu.be/RGS8jP3s4p4)
  - [Recon Mega Course Introduction](https://youtu.be/k57PNXnpzRI?list=PL4S940IsHJYXCmx361_ft5LwOgpLLYRlR)
  - [How to search for CVE POC for outdated Tech](https://youtu.be/t4KE-p2eCbY)
- **NahamSec**
  - [Channel Link](https://www.youtube.com/@NahamSec)
  - [Free Recon Course and Methodology](https://youtu.be/evyxNUzl-HA)
  - [JS Files Bug Bounty 1](https://youtu.be/fQoxjBwQZUA?si=A1AnQz_GvG6vQ5XV)
  - [JS Files Bug Bounty 2](https://youtu.be/FWPXWBh4EFw?si=HU3lSJMyvi-SBVh8)
- **Orwa Atyat**
  - [Channel Link](https://www.youtube.com/@orwaatyat2958?authuser=0)
- **Specific Topics**
  - [Puny-Code, 0-Click Account Takeover](https://youtu.be/4CCghc7eUgI)
  - [Art of VirusTotal Hacking](https://www.youtube.com/watch?v=Xosa-1o-01M&authuser=0)
  - [Finding Admin Panels & Leaked credentials with GitHub Dorks](https://www.youtube.com/watch?v=3sfe8U-f_zk&authuser=0)
  - [Information Disclosure Part 1](https://www.youtube.com/watch?v=zfpOg3P7gpo&authuser=0)
  - [Information Disclosure Part 2](https://www.youtube.com/watch?v=F5q5oimkJ9k&authuser=0)
  - [Tips & Tricks for Information Disclosure](https://www.youtube.com/watch?v=ODhLUi24DxQ&authuser=0)

### Articles & Writeups
- **Medium / Freedium / GitBook**
  - [Bug Bounty Insights: 10 Key Findings (ZeroClick Account Takeover)](https://medium.com/@maakthon/bug-bounty-insights-10-key-findings-zeroclick-account-takeover-part-5-a6acb3dce5e7?authuser=0)
  - [How to Discover EXIF Metadata Leaks from Images](https://freedium.cfd/https://medium.com/h7w/how-to-discover-exif-metadata-leaks-from-images-easy-p4-p3-bugs-44cf6b1cb875?authuser=0)
  - [How I Escalated Simple HTML Injection to SSRF via PDF Rendering](https://ahmed-tarek.gitbook.io/security-notes/pentesting/write-ups/how-i-escalated-simple-html-injection-to-ssrf-via-pdf-rendering)
  - [10 Google Dorks for Sensitive Data](https://freedium.cfd/https://infosecwriteups.com/10-google-dorks-for-sensitive-data-9454b09edc12)
- **HackerOne Reports**
  - [H1 Report 446238](https://hackerone.com/reports/446238?authuser=0)
  - [H1 Report 3099978](https://hackerone.com/reports/3099978?authuser=0)

### Forums & Socials
- [Bug Bounty Forum](https://bugbountyforum.com/)
- [Telegram: Daily Bounty Writeups](https://t.me/dailybountywriteup?authuser=0)
- [LinkedIn Post Example](https://www.linkedin.com/posts/abdelrahman-tamer-6a932924a_cybersecurity-cyber-share-activity-7238217097640636416-M31i?utm_source=social_share_send&utm_medium=member_desktop_web&rcm=ACoAAD2g5qEBCi2mx4g5MOSmzmul3ThyB9VkAZI&authuser=0)

### Mind Maps
- [Xmind Web Applications Map](https://xmind.app/mindmap/web-applications/rueGCH/?from=gallery&authuser=0)

## 3. Core Concepts & Vulnerabilities

### Punycode & IDN Homograph Attacks
- **Resource**: [The Most Underrated 0-Click Account Takeover Using Punycode](https://freedium.cfd/https://infosecwriteups.com/the-most-underrated-0-click-account-takeover-using-punycode-idn-attacks-c0afdb74a3dc?utm_source=chatgpt.com)
- **Tool**: [Punycode converter](https://www.punycoder.com/)
- **Attack Vectors**:
    - `FORGOT PASSWORD SECTION`
    - `OAUTH PROVIDER EMAIL TRUST`
    - `OAUTH PROVIDER REDIRECT URL`
- **Related Technique: Gmail Trick**
    - Gmail ignores dots `.` and plus signs `+` in email addresses.
    - e.g., `test.email@gmail.com`, `testemail@gmail.com`, and `test+1@gmail.com` all go to the same inbox.
    - > Ø¯Ù‡ Ù…Ø´ PunycodeØŒ Ù„ÙƒÙ†Ù‡ ÙŠÙÙŠØ¯Ùƒ ÙÙŠ **Ø§Ø®ØªØ¨Ø§Ø± ÙƒÙŠÙ Ø§Ù„ØªØ·Ø¨ÙŠÙ‚Ø§Øª ØªØªØ¹Ø§Ù…Ù„ Ù…Ø¹ ØªØ¹Ø¯Ø¯ Ø£Ø´ÙƒØ§Ù„ Ù†ÙØ³ Ø§Ù„Ø¥ÙŠÙ…ÙŠÙ„**.

### HTTP Request Smuggling
- [PortSwigger Academy](https://portswigger.net/web-security/request-smuggling)

### Cross-Site Scripting (XSS)
- [OWASP XSS Page](https://owasp.org/www-community/attacks/xss/)
- [HTML5 Security Cheatsheet (H5SC)](https://html5sec.org/), searchable collection of HTML5-related browser/XSS vectors; useful for generating test ideas around markup parsing and browser behavior. Treat individual entries and browser-compatibility labels as leads that may be dated: verify behavior in a current browser and use the authorized test scope. See the [Cure53 H5SC source repository](https://github.com/cure53/H5SC) and Cross-site scripting (XSS).
  - [H5SC InnerHTML Test-Tool](https://html5sec.org/innerhtml/), interactive browser-side demonstration with `document.write(innerHTML)` and `style.cssText` actions. Use it for sink and parsing concepts; it does not test a separate target or establish a vulnerability there. See Cross-site scripting (XSS)#3. DOM-Based XSS (Special / Client-Side).
- **XSS Challenges:**
  - [Google's XSS Challenge (Easier)](https://xss-game.appspot.com/)
  - [prompt.ml (Harder)](http://prompt.ml/0), availability was not confirmed during the 2026-10-08 link review (request timed out); use the [PortSwigger Web Security Academy XSS labs](https://portswigger.net/web-security/cross-site-scripting) as the maintained practice path if it remains unavailable.
  - [More Challenges (Google Search)](https://www.google.com/search?q=XSS+Challenges&*&ie=utf-8&oe=utf-8)

### Android Pentesting
- **Courses**
    - [Android Development for Beginners - Part 1](https://www.youtube.com/watch?v=fis26HvvDII)
    - [Android Development for Beginners - Part 2](https://www.youtube.com/watch?v=RcSHAkpwXAQ)
- **Resources**
    - [Sallam's GitBook on Android AppSec](https://sallam.gitbook.io/sec-88/android-appsec?authuser=0)
    - [YouTube Playlist](https://www.youtube.com/watch?v=hf5mOFtdsz0&list=PL4S940IsHJYWhhYOpBk6Y-U9nTQq2omae)
    - [Video Link](https://youtu.be/QwwLSyRzNwo?si=_WPVvlfNI1fS6cV2)

## 4. Tools

### Tool Aggregators & Installers
- **Project Discovery Tools Manager (pdtm)**
  - [GitHub Link](https://github.com/projectdiscovery/pdtm)

### Reconnaissance & Discovery
- **Subdomain Enumeration**
  - `subfinder`
  - `assetfinder`
  - `findomain`
  - `massdns`
  - `altdns`
  - `dnscan`
  - `Knockpy`
  - `Sublist3r`
- **Content Discovery**
  - `Waymore`
  - `katana`
  - `SecretFinder`
- **General Recon**
  - `theHarvester`
  - `enumall`
- **GitHub Secret Scanners**
  - `Gitrob`
  - `git-all-secrets`
  - `TruffleHog`
  - `git-secrets`
  - `repo-supervisor`

### Exploiting & Scanning
- **XSS Scanners**
  - `XSS-Radar`
  - `XSSHunter`
  - `domxssscanner`
  - `XSSer`
  - `BruteXSS`
  - `XSStrike`

### Manual HTTP Traffic Capture for Web Assessments

Use an intercepting proxy to observe the requests and responses produced by ordinary, authorized application use. Keep automated scanning separate from this initial mapping pass.

| Tool | Fit for this workflow | Persistence and sharing |
|---|---|---|
| [OWASP ZAP](https://www.zaproxy.org/) | Recommended free starting point when you need a durable capture. The History tab lists requests and displays the matching request and response; you can filter the history and add notes or tags. | Save the session at the start of the work; ZAP updates its session database as you work. Select relevant entries and use **Save Messages** to export requests and responses to a text file. |
| [Burp Suite](https://portswigger.net/burp) | Strong option if you already use it. Proxy HTTP history records traffic even when interception is off and supports filtering, annotations, and request/response inspection. | Burp Community's temporary project is memory-only and is lost when Burp closes. A disk-backed project is a Professional feature. Before closing Community, manually preserve the specific messages you need; do not treat its open history as durable storage. |
| [HTTP Toolkit](https://httptoolkit.com/) | Convenient browser/client interception and readable HTTP inspection; it can also capture traffic from many command-line and application clients. | Documentation lists HAR export for individual exchanges and filtered sets as a Pro feature. Check the current edition limits before making it your only evidence archive. |

**Suggested capture routine:** create a dedicated browser profile, configure only the chosen proxy, and browse the authorized application normally with interception paused. Set/filter the target scope so third-party traffic does not dominate the history. Save the session, then export only the requests relevant to one workflow (for example, login or a read-only page view). Name each capture by sequence and action, such as `01-login-baseline.txt` or `02-profile-view.txt`.

> [!WARNING]
> Request/response captures can contain passwords, session cookies, bearer tokens, personal data, and private application content. Keep the untouched capture in your controlled local storage. Before sharing a sample for analysis, redact `Cookie`, `Set-Cookie`, `Authorization`, CSRF tokens, passwords, personal information, and sensitive response values while preserving the method, path, relevant parameter names, status, and behavior needed to reason about it. Do not upload a full project or raw HAR unless it has been reviewed and sanitized.

For each workflow, provide: **action performed**, **user role**, **request method and path**, **redacted request**, **status and relevant redacted response**, and **what you expected versus observed**. This lets the traffic be mapped to the relevant test category and checklist case without assuming that a request alone proves a vulnerability.

## 5. Online Resources & Search Engines

### Hacking Search Engines
- [Recon-Engine](https://ahmed-0-3del.github.io/Recon-Engine/)
- [Hunter.how](https://hunter.how/)
- [FOFA.info](https://en.fofa.info/)
- [ZoomEye](https://www.zoomeye.ai/)
- [Censys](https://search.censys.io/)
- [Shodan](https://www.shodan.io/)
- [Quake](https://quake.360.net/quake/#/index)
- [BeVigil (Mobile Apps)](https://bevigil.com/)
- [FullHunt](https://fullhunt.io/), use the current search interface and query only assets authorized by the applicable program; the former saved URL contained a target-specific query (`mgm.mo`) and should not be reused as a general starting point.

### Dorking & Cheatsheets
- **Google Dorks**
  - [TakSec Cheatsheet](https://taksec.github.io/google-dorks-bug-bounty/?authuser=0)
  - [VeryLazyTech Cheatsheet](https://verylazytech.github.io/index.html)
  - [GitHub Repo: TakSec/google-dorks-bug-bounty](https://github.com/TakSec/google-dorks-bug-bounty/)
- **GitHub Dorks**
  - [Der Benji Cheatsheet](https://benjitrapp.github.io/memories/2022-09-04-github-dorks/)
  - [mr-koanti Cheatsheet](https://mr-koanti.github.io/github.html?authuser=0#)
  - **Tips & Notes:**
    - > First step: don't forget to filter by recently updated code.
    - `path:/wp-config.php` -> Finds WordPress credentials.
    - **Keywords**: `org:`, `language:PHP`, `Passwords`, `Pss`, `Pwd`, `PW`, `Token`, `Secret`, `Privet`
    - **Reporting Leaked Internal Data**:
      - > Write *internal data leaked via github*. You must mention this data is internal so you can't test it.
      - > 1. Use lowercase filters.
      - > 2. Check the date of the repository.
      - > 3. Verify the user works for the company.
      - > 4. Don't add `.com` to searches.
      - > 5. Use negative filters: `NOT net.com NOT about.test`
- **Shodan Dorks**
  - [mr-koanti Cheatsheet](https://mr-koanti.github.io/shodan)
  - `Ssl.cert.subject.CN:`

### Vulnerability & Threat Intel
- [VirusTotal](https://www.virustotal.com/)
- [OTX AlienVault](https://otx.alienvault.com/)
- [Exploit-DB](https://www.exploit-db.com/)
- [HuntDB (Real-Time Intel)](https://huntdb.com/)
- [ThreatCrowd](https://ci-www.threatcrowd.org/), legacy link retained for reference; current availability and data freshness were not confirmed in this review. Do not rely on it as a primary source.
- [ThreatBook](https://i.threatbook.io/research)
- [NVD](https://nvd.nist.gov/vuln-metrics/cvss#)
- [CVExploits](https://cvexploits.io/)

### Other Useful Websites
- [Wayback Machine](https://web.archive.org/)
- [SecurityTrails](https://securitytrails.com/)
- [urlscan.io](https://urlscan.io/)
- [Robtex](https://www.robtex.com/)
- [RapidDNS](https://rapiddns.io/)
- [Intelx.io](https://intelx.io/tools?tab=domain)
- [Netcraft](https://searchdns.netcraft.com/)
- [CVSS Calculator](https://www.first.org/cvss/calculator/3-0?authuser=0)

### Browser Extensions
- [Apollo.io](https://chromewebstore.google.com/detail/apolloio-free-b2b-phone-n/alhgpfoeiimagjlnfekdhkjlkiomcapa?authuser=0)
- [Findsomething](https://addons.mozilla.org/en-US/firefox/addon/findsomething/?authuser=0)

## 6. Key Technologies

### Large Language Models (LLMs)
- [LM Studio](https://lmstudio.ai/)
- [Ollama](https://ollama.com/)
- **Gemini CLI**
  - [Codelab](https://codelabs.developers.google.com/gemini-cli-hands-on?hl=ar#0)
  - **Windows Install:**
    ```powershell
    Set-ExecutionPolicy Bypass -Scope Process -Force
    iex ((New-Object System.Net.WebClient).DownloadString('https://community.chocolatey.org/install.ps1'))
    choco install nodejs --version=22.19.0 -y
    npm install -g @google/gemini-cli
    gemini
    ```

### AI Frameworks
- **LangChain**
  - [Tutorials](https://langchain-ai.github.io/langgraph/tutorials/workflows/#building-blocks-the-augmented-llm)
- **Crew AI**
  - [Homepage](https://www.crewai.com/open-source)

## 7. Recommended Reading
- *Web Hacking 101* by Peter Yaworski

## 8. Bug Bounty Platforms

This is a directory, not an authorization list. Platform registration does not grant permission to test any asset. For every live test, use the target's current program brief to confirm the exact asset, allowed methods, exclusions, and reporting route. Availability and researcher eligibility can change; check the official page before applying.

| Service | What it is | Official starting point | Access / eligibility note |
|---|---|---|---|
| HackerOne | Researcher platform hosting bug bounty programs, VDPs, and other engagements. | [For hackers](https://www.hackerone.com/hackers) · [Public vs. private programs](https://docs.hackerone.com/en/articles/8365270-private-vs-public-programs) | Create an account; public programs are available to the community, while private programs require an invitation. Program terms still govern each test. |
| Bugcrowd | Researcher platform and learning resources. | [Researcher onboarding](https://docs.bugcrowd.com/researchers/onboarding/becoming-a-researcher/) | Anyone can create an account; access to a particular program and its scope is controlled by that program. |
| Intigriti | Researcher platform for bug bounty and vulnerability disclosure programs. | [Researcher account registration](https://login.intigriti.com/account/register) · [Report guidance](https://kb.intigriti.com/en/articles/5379086-how-to-write-and-submit-a-good-report) | Account registration does not establish eligibility for every program; read the program brief and its participation requirements. |
| Zerocopter | Managed security platform offering CVD, recon, pentesting, and bug bounty services. | [Platform overview](https://www.zerocopter.com/products/platform) · [Terms](https://www.zerocopter.com/terms-and-conditions/) | Its terms describe researchers selected for certain services. Do not assume open self-service program access; confirm participation with Zerocopter and the specific customer program. |
| Synack Red Team (SRT) | Vetted security-researcher community and paid security-testing engagements. | [SRT](https://www.synack.com/red-team/) · [Synack security](https://www.synack.com/security/) | Application and vetting are required. Synack states that SRT is not a bug bounty program; classify it as a vetted engagement route, not a public/private bounty marketplace. |
| Cobalt Core | Vetted freelance pentesting community delivering scoped customer engagements. | [Become a pentester](https://www.cobalt.io/life/become-a-pentester) | Application, technical assessment, interview, and verification apply. Payment is for engagement effort rather than an open per-bug bounty model. |
| Google Bug Hunters | Google's vendor-run vulnerability reward and disclosure programs, with program-specific policies. | [Google Bug Hunter University](https://bughunters.google.com/learn) · [Program portal](https://bughunters.google.com/) | Follow the policy for the specific Google product/program; training content is not itself a test authorization. |

### Legacy or unverified directory entries

The following names appeared in an older third-party platform list. Their current researcher onboarding and program availability were not verified from current official documentation during this review. Retain them as leads only; verify before relying on them.

- Bountyfactory, [legacy directory entry](https://bugbountyforum.com/getting-started/platforms/)
- BugBountyHQ, [legacy directory entry](https://bugbountyforum.com/getting-started/platforms/)

The linked forum page is an older, undated community directory and still labels Synack as a private bug bounty and Cobalt as public/private. Those labels are not reliable current classifications; see the official service descriptions above.

> [!WARNING]
> A public account, public program listing, or platform-wide safe-harbor statement is not a blanket license. Do not probe assets until the exact target policy explicitly includes them and permits the planned technique.

## 9. Beginner Prerequisites

> Source: [How to start in bug bounty](https://youtu.be/FAU7r80Y8Os)

Before hunting, ensure you have foundational knowledge in the following areas:

### Frontend Technologies
- **HTML basics** â€” useful for attacks like XSS (freeCodeCamp / Elzeroweb)
- **JavaScript basics** â€” essential for XSS, CSRF, CORS, CSWSH
  - Key concepts: data types, variables, conditions, loops, arrays, functions, objects, OOP basics, events, built-in functions, window properties, arrow functions
- **PHP basics** â€” for server-side attack understanding
  - Key concepts: data types, conditions, loops, functions, OOP basics, database operations, file operations, cookies, sessions, headers

### Networking & Infrastructure
- **Network basics**: IP, TCP/UDP, packets, DNS, subdomain types, record types (A, AAAA, CNAME, PTR, SOA)
- **Linux basics**: file commands (`mkdir`, `ls`, `cp`, `mv`, `cat`, `touch`, `find`, `cd`), string tools (`grep`, `head`, `tail`, `awk`, `sed`), user privileges

### Hacking Fundamentals
- HTTP request/response cycle, response codes (2xx / 3xx / 4xx / 5xx)
- Intercept proxies (Burp Suite), fuzzing, directory brute-force, firewall, encryption, payloads, exploits, MITM, virus types

### Vulnerability Learning Workflow
1. Read about *why* the vulnerability happens
2. Understand *where and how* to find it
3. Solve labs (PortSwigger, HackTheBox, Root-Me)
4. Read write-ups and HackerOne reports
5. Take canonical notes -> Web Application Penetration Testing Checklist
6. Before live work, use Web Application Penetration Testing Field Guide to establish authorization and move through the assessment; track WSTG coverage in the Checklist and use the target's own program brief as the permission boundary.

### Optional Skills
- Scripting: Python, Ruby, or Bash
- JS frameworks: React, Angular, Vue, Next.js

---


## 10. Research and Penetration Testing Standards

### How to weigh these sources

| Source class | Best use | Limitation |
|---|---|---|
| Current target program brief and Rules of Engagement | Decide what exact asset, account, technique, rate, evidence handling, and reporting route are permitted for this engagement. | Applies to that program and can change; re-check it before resuming testing. |
| Platform documentation | Learn that platform's report fields, triage process, severity model, and program controls. | It is platform guidance, not independent evidence and not a substitute for another platform's or target's policy. |
| OWASP / NIST / government disclosure guidance | Use OWASP WSTG for web-test cases; use NIST SP 800-115 - Security Testing and Assessment for general planning, execution, evidence-handling, and reporting context; use NIST SP 800-216 for federal disclosure-program lifecycle guidance. The Web Application Penetration Testing Checklist and Web Application Penetration Testing Field Guide provide this vault's web-specific workflow. | NIST SP 800-115 is a 2008 general guide, not current web-test coverage or tool documentation. None of these sources authorizes testing a particular target; follow its current written scope and Rules of Engagement. |
| Peer-reviewed empirical studies | Learn what sampled hunters, maintainers, and program operators reported about scope clarity, report review, communication, and program design. | Results describe specific samples and settings; they do not establish universal rules or technical test procedures. |
| Preprints, blogs, forums, and individual writeups | Generate questions, hypotheses, and optional practice ideas. | Treat as lower-confidence until corroborated; they do not override policy, standards, or reproducible evidence. |

> [!IMPORTANT]
> The previous official platform resources are useful operational references, but they are not all “research findings.” Platform guidance states what that platform recommends or requires. Use the empirical studies below for evidence about observed ecosystem patterns, with each study's sample and setting in mind. For a live engagement, the current target policy remains the permission boundary.

### Empirical studies on Bug Bounty and disclosure programs

- [Bug Hunters' Perspectives on the Challenges and Benefits of the Bug Bounty Ecosystem, USENIX Security 2023](https://www.usenix.org/conference/usenixsecurity23/presentation/akgul), combines a free-listing survey (`n=56`), a factor-rating survey (`n=159`), and interviews (`n=24`). Participants identified rewards and learning as important benefits, scope as the strongest program differentiator, and communication problems as a major challenge. **Practical use:** when comparing programs for learning, inspect scope clarity and communication expectations as well as reward tables. These are reported participant perspectives, not a guarantee of success on any program.
- [Why Some Bug-bounty Vulnerability Reports are Invalid?, ESEM 2021](https://doi.org/10.1145/3475716.3484193), empirical analysis of disclosed invalid HackerOne reports and program policies; the paper identifies out-of-scope reports as a leading invalid category in its dataset. **Practical use:** make asset/issue applicability and program-policy checks explicit before testing and again before submission. Its data is platform- and sample-specific.
- [Coordinated Vulnerability Disclosure Programme Effectiveness: Issues and Recommendations, Computers & Security, 2022](https://ora.ox.ac.uk/objects/uuid:58b63628-8a00-4958-8d1f-8c880bfc8d91), qualitative evidence from 39 survey responses and eight follow-up interviews with program operators; respondents described low-quality reports as a resource burden and reports as inputs to security-process improvement. **Practical use:** validate the behavior and impact, make evidence reproducible, and write reports that reduce avoidable triage work. The relatively small qualitative sample should not be treated as a universal rate estimate.
- [A Deep Dive Into How Open-Source Project Maintainers Review and Resolve Bug Bounty Reports, IEEE S&P 2025](https://jgarcia.ics.uci.edu/wp-content/uploads/sp2025_deepdive.pdf), studies maintainers who used the Huntr platform, using surveys (`n=51` and `n=90`) and interviews (`n=17`). It documents both benefits and review burdens in open-source projects. **Limitation:** the OSS/Huntr setting may differ from commercial web programs on HackerOne, Bugcrowd, or Intigriti.
- [From Reviewers' Lens: Understanding Bug Bounty Report Invalid Reasons with LLMs, arXiv preprint, 2025](https://arxiv.org/abs/2511.18608), analyzes 9,942 publicly disclosed HackerOne reports, including 1,400 marked invalid, and tests automated validity classification. The taxonomy work focuses on Information Disclosure and the paper is a preprint. **Use as emerging research only:** it is not a general rubric for deciding whether every vulnerability class is valid, and an AI verdict must never replace reproduction, scope review, or human judgment.

### Bug Bounty and Penetration Testing: Different Operating Models

These terms overlap in the security techniques used, but they describe different ways of commissioning and organizing security work. The distinction below is a synthesis of official testing guidance, program documentation, and the limits of the available empirical studies; it is not a claim that every engagement follows one universal contract.

| Dimension | Scoped penetration test | Bug bounty / vulnerability reward program |
|---|---|---|
| Work arrangement | A client and tester agree an assessment objective, target scope, timeframe, constraints, and rules of engagement before testing. | An organization publishes or provides program rules and eligible assets to a researcher community; researchers independently choose what to investigate within those rules. |
| Coverage expectation | The engagement is planned against stated objectives and agreed coverage. A checklist helps record what was and was not tested; it cannot prove that every possible flaw was found. | There is no guaranteed complete test of every listed asset or test case. Participation and findings vary by researcher, program, and time. |
| Time and coordination | Usually planned and bounded as an engagement, with coordination, contacts, and reporting milestones defined in the rules of engagement. | Often ongoing or campaign-based, with submissions reviewed as they arrive; researcher participation is distributed rather than managed as one fixed assessment team. |
| Primary output | An assessment report that communicates scope, methods, evidence, risk, limitations, and remediation priorities; retesting may be agreed separately. | Individual vulnerability reports submitted under the program's policy; reward, recognition, handling, and disclosure depend on that program's terms. A bounty program is not automatically a comprehensive assessment report. |
| What defines permission | Written authorization and the engagement's rules of engagement. | The specific program policy and its scope, exclusions, constraints, and reporting rules. A platform account alone grants no authority. |

OWASP describes WSTG as a testing framework with detailed techniques, not a rigid universal checklist; it also notes that no finite list can cover every possible issue. NIST SP 800-115 describes a planned assessment process including planning, execution, and post-testing/reporting activities; the publication dates to 2008, so use it as a foundational process reference and pair it with current engagement requirements and current technical guidance. PTES also presents a phased penetration-testing model, from pre-engagement through reporting.

Empirical bug bounty research supports treating the models as complementary rather than interchangeable: a Chromium/Firefox case study found differences between vulnerabilities discovered by external hunters, internal teams, and threat actors, and concluded that bounty programs can complement internal expertise. This is evidence from two browser projects, not a universal head-to-head study proving that pentesting or bug bounty is always more effective. A mixed-methods hunter study (`n=56`, `n=159`, and `n=24`) examined researcher experience and program factors, not a controlled comparison against commissioned penetration tests.

> [!TIP]
> For a learner whose goal is penetration testing, practice the **complete engagement workflow**: define authorization and scope, plan coverage, enumerate and test methodically, validate evidence safely, document limitations, write prioritized remediation guidance, and close out or retest when agreed. Use Web Application Penetration Testing Field Guide for execution, Web Application Penetration Testing Checklist as the test-case coverage register, and the target's Rules of Engagement as the live boundary. Bug bounty reports and labs remain useful supplemental practice, but they do not replace full-scope planning and reporting exercises.

### Standards and disclosure guidance

- [NIST SP 800-216](https://csrc.nist.gov/pubs/sp/800/216/final), federal vulnerability-disclosure framework covering receipt, assessment, tracking, and communication of reports. It helps explain the organization-side lifecycle; it is not itself permission for external testing.
- [OWASP Vulnerability Disclosure Cheat Sheet](https://cheatsheetseries.owasp.org/cheatsheets/Vulnerability_Disclosure_Cheat_Sheet.html), general disclosure guidance for researchers and organizations, including scope, reproduction evidence, privacy, and communication considerations. Treat it as guidance, not target-specific authorization.
- [DOJ Vulnerability Disclosure Policy](https://www.justice.gov/jmd/vulnerability-disclosure-policy) and [disclose.io's VDP model](https://disclose.io/framework/terms/vdp/), examples for understanding how policies express authorized assets, allowed/prohibited activity, and reporting channels. Each applies to its stated context; neither authorizes work on unrelated targets.

- [Google Bug Hunters, Learn](https://bughunters.google.com/learn)
- [hakluke, How to start (or come back to) bug bounties in 2026](https://hakluke.com/how-to-start-or-come-back-to-bug-bounties-in-2026)
- [PTES, Penetration Testing Execution Standard](http://www.pentest-standard.org/index.php/Main_Page)
- [PTES Technical Guidelines](http://www.pentest-standard.org/index.php/PTES_Technical_Guidelines)
- NIST SP 800-115 - Security Testing and Assessment, legacy 2008 process reference; see its linked official NIST record and PDF for the original.
## Related Notes
- NTI Bug Bounty Course Notes
- NTI Bug Bounty Session Links
- Bug BountyPrograms
- Hacker Methodology
- Web Application Penetration Testing Checklist
- Web Application Penetration Testing Field Guide

## Resources
Sources and references are stored in this note's `source` / `references` properties.
