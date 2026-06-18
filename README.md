# Cybersecurity Learning Journey

> **Oluwatoni Adebajo** — Software Engineering Student, Babcock University (4.61 GPA)  
> Documenting my transition from secure software development into cybersecurity.  
> Currently preparing for: **ISC2 Certified in Cybersecurity (CC)**

---

##  Table of Contents
- [About This Repo](#about-this-repo)
- [Cisco: Introduction to Cybersecurity](#cisco-introduction-to-cybersecurity)
- [Academic Security Coursework](#academic-security-coursework)
  - [Reverse Engineering & Malware Analysis](#reverse-engineering--malware-analysis-itgy400)
  - [Software Security Engineering](#software-security-engineering-seng204)
  - [Fundamentals of Computer Security](#fundamentals-of-computer-security-cosc222)
  - [Network Security & Software](#network-security--software-seng409)
- [ISC2 CC Exam Preparation](#isc2-cc-exam-preparation)
- [Hands-On Practice](#hands-on-practice)
- [Key Takeaways So Far](#key-takeaways-so-far)

---

## About This Repo

I'm a Software Engineering student with hands-on experience building authenticated, role-based systems. This repo documents everything I've studied in cybersecurity — from formal coursework and certifications to self-directed learning and labs.

My background as a developer shapes how I approach security: I understand how software is *built*, which helps me reason about how it can be *broken*.

---

## Cisco: Introduction to Cybersecurity
**Status: Completed | Certificate: [https://www.credly.com/badges/738a5b5a-9f11-4a82-a01e-f677fd74dec1/public_url](#)** 

Cisco's foundational cybersecurity course covering the modern threat landscape and core defensive concepts.

### What I Learned

**The Threat Landscape**
- Types of cyber threats: malware, ransomware, phishing, social engineering, DDoS attacks
- How threat actors operate — from script kiddies to nation-state actors
- The difference between vulnerabilities, threats, and risks
- Why humans are often the weakest link in any security system

**Data & Device Protection**
- The CIA Triad: **Confidentiality, Integrity, Availability** — the three pillars every security decision must balance
- Encryption basics: how data is protected at rest and in transit
- Authentication methods: passwords, MFA, biometrics, and why layering matters
- The principle of least privilege — users should only access what they need

**Network Defense**
- How firewalls filter traffic and create network boundaries
- Intrusion Detection Systems (IDS) vs Intrusion Prevention Systems (IPS)
- The role of VPNs in securing communications
- Wireless security protocols: WEP (broken), WPA2, WPA3

**Responding to Threats**
- Incident response basics: detect → contain → eradicate → recover
- The importance of logging and monitoring for threat detection
- Why regular backups are a non-negotiable security control

### Key Insight
> Security isn't a product you install — it's a continuous process. A system is only as secure as its weakest component, which is often not technical.

---

## Academic Security Coursework
*Completed as part of B.Sc. Software Engineering at Babcock University*

---

### Reverse Engineering & Malware Analysis (ITGY400)
**Status: Completed**

This was the course that changed how I see software entirely. Looking at programs from the *outside in* — without source code — forces a completely different mental model.

#### Core Concepts Covered

**What is Reverse Engineering?**
- The process of analyzing compiled software to understand its behavior, structure, and intent
- Used in security for: malware analysis, vulnerability research, interoperability, and CTF challenges
- Two primary approaches: **static analysis** (examining code without running it) and **dynamic analysis** (observing behavior at runtime)

**Static Analysis**
- Reading disassembled code (assembly language) to understand program logic
- Identifying suspicious strings, hardcoded credentials, and obfuscated code
- Tools used in the field: IDA Pro, Ghidra (free, NSA-developed), Binary Ninja
- How to identify common code patterns: loops, conditionals, function calls

**Dynamic Analysis**
- Running malware in a controlled sandbox environment to observe behavior
- Monitoring: file system changes, registry modifications, network connections, process spawning
- Why sandboxes matter: you need to contain what you're analyzing
- Tools: Wireshark (network traffic), Process Monitor, Cuckoo Sandbox

**Malware Types & Behaviors**
| Type | What It Does |
|------|-------------|
| Virus | Attaches to legitimate files; spreads when files are shared |
| Worm | Self-replicates across networks without user action |
| Trojan | Disguises itself as legitimate software |
| Ransomware | Encrypts files and demands payment |
| Rootkit | Hides its presence deep in the OS |
| Keylogger | Records keystrokes to steal credentials |
| Spyware | Monitors user activity silently |
| Botnet | Enslaves systems for coordinated attacks (DDoS, spam) |

**Obfuscation Techniques Malware Uses**
- Packing: compressing/encrypting the payload so it's unreadable until runtime
- Code obfuscation: making code intentionally hard to follow
- Anti-debugging tricks: checking if it's being analyzed and behaving differently
- Polymorphism: changing its own code signature to evade antivirus detection

**Defensive Takeaways**
- Understanding *how* malware works is the foundation of building defenses against it
- Behavioral detection is more reliable than signature-based detection for modern threats
- Isolation and sandboxing are critical — never analyze suspicious files on a live system

#### Key Insight
> The same skills used to analyze malware are used to find vulnerabilities in legitimate software. A security engineer who can read disassembly has a significant advantage.

---

### Software Security Engineering (SENG204)
**Status: Completed**

Focused on building security *into* software from the start — not patching it on afterward.

#### Core Concepts Covered

**The Secure Software Development Lifecycle (SSDLC)**
- Why traditional SDLC produces insecure software: security is considered too late
- Integrating security at every phase: requirements → design → implementation → testing → deployment → maintenance
- The cost principle: a vulnerability found in design costs 10x less to fix than one found in production

**Threat Modeling**
- Systematically identifying what could go wrong *before* writing code
- **STRIDE** framework:
  - **S**poofing — pretending to be someone else
  - **T**ampering — modifying data without authorization
  - **R**epudiation — denying an action occurred
  - **I**nformation Disclosure — exposing data to unauthorized parties
  - **D**enial of Service — making a system unavailable
  - **E**levation of Privilege — gaining more access than allowed
- Drawing data flow diagrams to identify trust boundaries
- Rating threats by likelihood and impact (DREAD model)

**Security Requirements Engineering**
- Writing security requirements that are testable and specific
- Difference between functional security requirements ("the system shall encrypt passwords") and non-functional ("the system shall respond to auth requests within 200ms under attack")
- Misuse cases: modeling how an attacker would interact with the system

**Secure Design Principles**
| Principle | What It Means |
|-----------|--------------|
| Least Privilege | Give users/processes only the access they need |
| Defense in Depth | Layer multiple controls so one failure isn't catastrophic |
| Fail Securely | When something breaks, it should default to a secure state |
| Open Design | Security shouldn't depend on secrecy of the design (Kerckhoffs's principle) |
| Separation of Duties | No single person/process controls a critical function entirely |
| Minimize Attack Surface | Expose only what's necessary |

**Common Vulnerabilities (Secure Coding)**
- Injection flaws: SQL injection, command injection — always sanitize and parameterize inputs
- Buffer overflows: writing beyond allocated memory; mitigated by bounds checking
- Insecure deserialization: trusting user-controlled serialized data
- Hardcoded credentials: never store secrets in source code
- Improper error handling: error messages that reveal system internals

**How This Applied to My Internship Work**
At Cynergy Solutions, I applied these principles directly: building RBAC into the Library Management System ensured least privilege; modular design reduced attack surface; thorough input testing addressed injection risks.

---

### Fundamentals of Computer Security (COSC222)
**Status:Completed**

The theoretical foundation — cryptography, access control models, and security protocols.

#### Core Concepts Covered

**Cryptography**
- Symmetric encryption: same key encrypts and decrypts (AES, DES) — fast, used for bulk data
- Asymmetric encryption: public key encrypts, private key decrypts (RSA) — used for key exchange and digital signatures
- Hash functions: one-way transformations (SHA-256, MD5) — used for password storage and integrity checking
- Why MD5 and SHA-1 are broken: collision attacks
- Digital signatures: proving authenticity and non-repudiation
- PKI (Public Key Infrastructure): how certificates and certificate authorities work
- TLS/SSL: how HTTPS actually secures web traffic

**Authentication & Access Control**
- Authentication factors: something you know, have, or are (MFA combines multiple)
- Password security: salting + hashing (why bcrypt beats SHA-256 for passwords)
- Access control models:
  - **DAC** (Discretionary): owner controls access (most OS file systems)
  - **MAC** (Mandatory): system enforces policy based on labels (military systems)
  - **RBAC** (Role-Based): access tied to roles, not individuals (what I built at Cynergy)
  - **ABAC** (Attribute-Based): access based on attributes of user, resource, environment

**Security Protocols**
- How Diffie-Hellman key exchange works (two parties agree on a key without ever transmitting it)
- Kerberos: network authentication protocol used in enterprise environments
- OAuth and session token management

**Key Insight**
> Cryptography is only as strong as its implementation. A mathematically perfect cipher with a hardcoded key, or without proper IV/salt management, is still vulnerable.

---

### Network Security & Software (SENG409)
**Status:Completed**

How networks are attacked and defended — from the packet level up.

#### Core Concepts Covered

**Network Fundamentals for Security**
- OSI model from a security perspective: which attacks happen at which layer
- TCP/IP and how protocols can be exploited (SYN floods, IP spoofing)
- DNS security: DNS poisoning, DNSSEC
- ARP spoofing and man-in-the-middle positioning

**Attack Types**
- **Reconnaissance**: passive (OSINT, Shodan) vs active (port scanning with Nmap)
- **Network scanning**: discovering open ports, services, and OS fingerprinting
- **Sniffing**: capturing unencrypted traffic on the same network
- **DDoS**: volumetric, protocol, and application-layer attacks
- **Man-in-the-Middle (MITM)**: intercepting and possibly modifying communications

**Defense Mechanisms**
- Firewalls: stateless (packet filtering) vs stateful (tracks connection state) vs application-layer (WAF)
- Network segmentation and DMZ architecture
- IDS vs IPS: detection vs active prevention
- VPNs: tunneling protocols (IPSec, OpenVPN, WireGuard)
- Network Access Control (NAC)

**Wireless Security**
- WEP: broken — RC4 key reuse makes it crackable in minutes
- WPA2: CCMP/AES-based, still widely used
- WPA3: mandatory forward secrecy, protects past sessions if key is compromised
- Evil twin attacks and rogue access points

**Secure Communications**
- Certificate pinning: hardcoding expected certificate to prevent MITM on mobile apps
- HSTS: forcing browsers to use HTTPS only
- Secure email: PGP, S/MIME, SPF/DKIM/DMARC to prevent spoofing

---

## ISC2 CC Exam Preparation
**Status:In Progress | Target Exam Date: June2026**

The ISC2 Certified in Cybersecurity (CC) is an entry-level certification covering five domains.

### Exam Domains & My Progress

| Domain | Topic | Status |
|--------|-------|--------|
| Domain 1 | Security Principles |Completed |
| Domain 2 | Business Continuity, Disaster Recovery & Incident Response |Completed |
| Domain 3 | Access Controls Concepts | In Progress |
| Domain 4 | Network Security |  Not Started |
| Domain 5 | Security Operations |  Not Started |

### Domain 1: Security Principles — Study Notes

**The CIA Triad (in depth)**
- **Confidentiality**: preventing unauthorized disclosure. Controls: encryption, access control, classification
- **Integrity**: ensuring data hasn't been altered. Controls: hashing, digital signatures, input validation
- **Availability**: ensuring authorized access when needed. Controls: redundancy, backups, DDoS protection
- Non-repudiation: a fourth principle — you cannot deny an action you took (digital signatures provide this)

**Risk Management**
- Risk = Threat × Vulnerability × Impact
- Risk responses: **Accept** (tolerate it), **Avoid** (eliminate the activity), **Mitigate** (reduce likelihood/impact), **Transfer** (insurance, outsourcing)
- Qualitative vs quantitative risk assessment
- Residual risk: the risk that remains after controls are applied

**Privacy vs Security**
- Security protects data from unauthorized access
- Privacy protects personal information from misuse — even by authorized parties
- Key regulations: GDPR (Europe), NDPR (Nigeria), HIPAA (US healthcare)

### Domain 2: Business Continuity, Disaster Recovery & Incident Response — Study Notes
 
**Business Continuity (BC)**
- Business continuity planning ensures critical business functions keep running during and after a disruptive event (natural disaster, cyberattack, system failure, pandemic, etc.)
- A **Business Continuity Plan (BCP)** documents how an organization will continue operating during an incident
- **Business Impact Analysis (BIA)**: identifies which business functions are most critical and what the impact of their loss would be over time
- Key BIA metrics:
  - **RTO (Recovery Time Objective)**: the maximum acceptable time a system can be down before causing unacceptable harm
  - **RPO (Recovery Point Objective)**: the maximum acceptable amount of data loss, measured in time (e.g., "we can lose up to 1 hour of data")
  - **MTD (Maximum Tolerable Downtime)**: the absolute limit of how long a function can be unavailable before the business suffers severe/irrecoverable damage
**Disaster Recovery (DR)**
- DR is a *subset* of business continuity — specifically focused on restoring IT systems and data after a disruptive event
- A **Disaster Recovery Plan (DRP)** is the technical playbook: how to restore servers, applications, and data
- Backup strategies:
  - **Full backup**: complete copy of all data — slow to create, fast to restore
  - **Incremental backup**: only changes since the last backup — fast to create, slower to restore (must apply all increments in order)
  - **Differential backup**: changes since the last *full* backup — a middle ground
- **3-2-1 backup rule**: keep 3 copies of data, on 2 different media types, with 1 copy stored offsite
- DR site types:
  - **Hot site**: fully operational duplicate environment, ready to take over almost instantly (expensive)
  - **Warm site**: partially configured, needs some setup before becoming operational
  - **Cold site**: basic infrastructure only (power, space) — requires significant time to become operational (cheapest)
**Incident Response (IR)**
- An **incident** is any event that violates security policy or threatens the confidentiality, integrity, or availability of a system
- The Incident Response Lifecycle (commonly modeled in 6 phases):
  1. **Preparation** — having policies, tools, and trained personnel ready *before* an incident occurs
  2. **Detection & Analysis** — identifying that an incident has occurred and understanding its scope
  3. **Containment** — isolating affected systems to stop the incident from spreading
  4. **Eradication** — removing the root cause (malware, unauthorized access, vulnerability)
  5. **Recovery** — restoring systems to normal operation and verifying they're clean
  6. **Lessons Learned (Post-Incident Review)** — documenting what happened and improving defenses for next time
- **Incident Response Team (IRT)**: a designated cross-functional team responsible for executing the IR plan
- **Chain of custody**: maintaining a documented trail of how evidence was collected, handled, and stored — critical if the incident leads to legal action
- Difference between an **event** (anything observable on a system) and an **incident** (an event that has a negative impact on confidentiality, integrity, or availability)
**Why This Matters Together**
- BC, DR, and IR are deeply connected: an incident (e.g., ransomware) triggers incident response, which may trigger disaster recovery (restoring from backups), all in service of business continuity (keeping the organization running)
- A common testing approach is the **tabletop exercise**: walking through a simulated incident scenario as a team to validate that plans actually work before a real crisis happens
**Key Insight**
> Prevention will eventually fail — every organization will face an incident eventually. What separates organizations that survive from those that don't is whether they prepared a plan *before* they needed it.
 
---
 
 
- DAC, MAC, RBAC, ABAC — see notes in COSC222 section above
- Physical access controls: locks, badges, biometrics, mantrap
- Logical access controls: passwords, tokens, certificates
- Account management lifecycle: provisioning → review → de-provisioning

 ---
### Domain 3: Access Controls — Study Notes
*(Strong foundation from COSC222 and internship experience)*
- DAC, MAC, RBAC, ABAC — see notes in COSC222 section above
- Physical access controls: locks, badges, biometrics, mantrap
- Logical access controls: passwords, tokens, certificates
- Account management lifecycle: provisioning → review → de-provisioning

---

## Hands-On Practice

### TryHackMe
**Profile:** [tryhackme.com/p/oluwatoniadebajo](#)

| Room | Status | Topic |
|------|--------|-------|
| Offensive Security Intro | Completed | Attacker mindset, penetration testing fundamentals |
| Defensive Security Intro | Completed | Blue team fundamentals, SOC operations, monitoring |
 
*Continuing to build hands-on lab experience as time and resources allow, alongside ongoing certification study.*
---

## Key Takeaways So Far

1. **Security is a mindset before it's a skill.** The most important shift is learning to think adversarially — asking "how could this be abused?" before asking "how does this work?"

2. **Being a developer is a security advantage.** Understanding codebases, authentication flows, and data structures from the inside makes vulnerabilities more intuitive to identify.

3. **Defense in depth beats single controls.** No single control is enough. Layers create resilience.

4. **The human layer is always the weakest.** Social engineering succeeds where technical controls don't. Security awareness matters as much as technical controls.

5. **Cryptography is only as strong as its implementation.** Understanding *why* we use bcrypt instead of MD5 for passwords matters more than memorizing algorithm names.

---

*Last updated: June 2026*
