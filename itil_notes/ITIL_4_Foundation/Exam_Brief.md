# ITIL 4 Foundation — What the Cert Actually Is

> Everything you need to know before you book the exam, plus the mark
> distribution so you know where the points actually are.
> Facts verified against the official AXELOS/PeopleCert candidate syllabus
> (EN_ITIL4_FND_2019_CandidateSyll_v1.4) and the PeopleCert product page.

---

## 1. The Exam Format

| Item | Detail |
|---|---|
| **Questions** | 40, each worth 1 mark |
| **Pass mark** | **26 of 40 (65%)** |
| **Duration** | **60 minutes** (75 min if your exam language isn't your native/working language) |
| **Pacing** | ~90 seconds per question |
| **Book** | **Closed book** — no notes, no phone, no ITIL publication |
| **Negative marking** | **None** — attempt every question |
| **Prerequisites** | **None** — anyone can sit it |
| **Delivery** | PeopleCert test centre or online proctored |
| **Framework owner** | AXELOS |
| **Exam body** | PeopleCert (under licence from AXELOS) |
| **Languages** | 13 — English, Chinese, Dutch, French, German, Hungarian, Italian, Japanese, Polish, Portuguese (Brazil), Spanish, Thai |
| **Certificate validity** | 3-year renewal cycle, keep current with **60 CPD points** or by passing a higher ITIL module |
| **Cost** | ~£300–450 / $363–445, varies by region and provider |

**Two things people get wrong:**

1. "Closed book" means closed book. The ITIL 4 Foundation publication is the
   study material and is *not* allowed in the exam.
2. No negative marking means a guess is free. **Never leave a question blank.**

---

## 2. Question Types

This matters because the question *style* changes how you read it. Foundation
uses four styles, all multiple choice:

### Standard (classic) — most common

```text
Which practice has a purpose that includes managing risks to
confidentiality, integrity and availability?

  A. Information security management
  B. Continual improvement
  C. Monitoring and event management
  D. Service level management
```

Four options, one correct.

### List — pick TWO of four

```text
Which TWO statements about service asset and configuration
management are CORRECT?

  1. It does Q
  2. It does P
  3. It does R
  4. It does S

  A. 1 and 2
  B. 2 and 3
  C. 3 and 4
  D. 1 and 4
```

**Read carefully:** the options are *pairs of statements*, not statements. So
you must first identify the 2 true statements, then find the option pairing
them. Note the syllabus's own example for list questions is
"Which statement ... is CORRECT?" while the published form is "Which TWO
statements ... are CORRECT?" — always trust the stem in front of you.

### Missing word

```text
Identify the missing word(s) in the following sentence.

A [?] defines requirements for services and takes responsibility for
outcomes from service consumption.

  A. Role Q
  B. Role P
  C. Role R
  D. Role S
```

### Negative — used only as an exception

```text
Which is NOT a defined area of value?

  A. Q   B. P   C. R   D. S
```

The syllabus is explicit: negative questions appear **only** where part of the
learning outcome is knowing that something should *not* be done or should
*not* occur. So they are rare — but when you see `NOT`, `EXCEPT`, or `is least
likely`, slow down and invert each option before deciding.

**List questions are never negative.** Good to know — it narrows the reading.

---

## 3. Bloom's Level — What They Actually Ask

Foundation is tested at **Bloom's levels 1 and 2 only**:

| Level | Means | Verb in the syllabus | Example |
|---|---|---|---|
| **BL1** | Recall / recognise | "Recall", "Define" | State the definition of a known error |
| **BL2** | Understand / comprehend | "Describe", "Explain" | Explain how change enablement fits the SVC |

```text
 ❌ NOT tested at Foundation: "apply", "analyse", "evaluate"
    Those appear at the higher-level (Specialist/MP) modules.

 ✅ Tested: can you RECALL it and can you DESCRIBE it in your own words.
```

**Practical consequence:** you do *not* need real-world implementation
experience to pass. You need accurate definitions and clear conceptual
relationships. The verb in each syllabus row tells you the expected depth.

---

## 4. The Syllabus and Where the Marks Are

Seven learning outcomes, 40 marks total. This table is the single most useful
thing in this file:

| LO | Learning outcome | Marks | % | Notes |
|---|---|---|---|---|
| **1** | Key concepts of service management | **5** | 12.5% | 1.1 (2) + 1.2 (2) + 1.3 (1) |
| **2** | Guiding principles and how they aid adoption | **6** | 15% | 2.1 (1) + 2.2 (5) |
| **3** | The four dimensions of service management | **2** | 5% | |
| **4** | Purpose and components of the SVS | **1** | 2.5% | |
| **5** | SVC activities and how they interconnect | **2** | 5% | 5.1 (1) + 5.2 (1) |
| **6** | Purpose + key terms of 15 practices | **7** | 17.5% | 6.1 (5) + 6.2 (2) |
| **7** | **7 ITIL practices in detail** | **17** | **42.5%** | all of it |
| | **TOTAL** | **40** | 100% | |

### The uncomfortable truth

```text
LO4  Service Value System            =  1 mark  ( 2.5%)
LO5  Service Value Chain             =  2 marks ( 5.0%)
                        ─────────────────────────────
   SVS + SVC together                 =  3 marks ( 7.5%)

LO7  Seven practices in detail        = 17 marks (42.5%)
```

**The SVS and the Service Value Chain — the conceptual heart of ITIL 4, and
the most intellectually interesting part — are worth 3 of 40 marks.**

So if you're studying this cert to *understand* service management, study the
SVS and SVC properly; they're the framework that makes the rest coherent.
But if you're studying it to *pass*, your time is not best spent there. The
marks are overwhelmingly in the seven detailed practices.

```text
 Marks by area, out of 40:

 LO7  practices in detail    ██████████████████████████████████  17
 LO6  practice purposes+terms ██████████████                     7
 LO2  guiding principles      ████████████                       6
 LO1  key concepts           ██████████                         5
 LO3  four dimensions        ████                               2
 LO5  service value chain    ████                               2
 LO4  service value system   ██                                 1
```

Study strategy: **LO7 + LO6 = 24 of 40 marks = 60% of the exam** from roughly
ten practices. That's where the returns are.

---

## 5. LO1 — Key Concepts of Service Management (5 marks)

```text
1.1  Recall the definition of (BL1) — 2 marks
     a) Service
     b) Utility
     c) Warranty
     d) Customer
     e) User
     f) Service management
     g) Sponsor

1.2  Describe the key concepts of creating value with services (BL2) — 2 marks
     a) Cost
     b) Value
     c) Organization
     d) Outcome
     e) Output
     f) Risk
     g) Utility
     h) Warranty

1.3  Describe the key concepts of service relationships (BL2) — 1 mark
     a) Service offering
     b) Service relationship management
     c) Service provision
     d) Service consumption
```

Note the split: **2 marks are pure definition recall (BL1)** and **3 marks
require description (BL2)**. Learn the definitions, then be able to explain
how the concepts relate. Full content: `Key_Concepts.md`.

### Common distractor pairings in LO1

```text
CUSTOMER  vs  USER
  Customer = person who BUYS and uses products/services
  User     = person who USES products/services
  → Can be different people, or the same person

SPONSOR    vs  CUSTOMER
  Sponsor  = authorises, funds, sets priority for change
  Customer = consumes the service
  → Sponsor pays, user complains

OUTCOME   vs  OUTPUT
  Output   = the deliverable produced (a service)
  Outcome  = the EFFECT for a specific stakeholder
  → The output is what you deliver; the outcome is what happens to them

UTILITY   vs  WARRANTY
  Utility   = does it satisfy a need (fitness for purpose)
  Warranty  = does it keep doing so as promised (assurance)
```

---

## 6. LO2 — Guiding Principles (6 marks)

```text
2.1  Describe the nature, use and interaction of the guiding
     principles (BL2) — 1 mark

2.2  Explain the use of the guiding principles (BL2) — 5 marks
     a) Focus on value
     b) Start where you are
     c) Progress iteratively with feedback
     d) Collaborate and promote visibility
     e) Think and work holistically
     f) Keep it simple and practical
     g) Optimize and automate
```

**2.2 is worth 5 marks** — one mark each for explaining the use of a named
principle. Expect scenario questions: "which principle does this describe?"

Full content: `Guiding_Principles.md`

---

## 7. LO6 — 15 Practices and 7 Key Terms (7 marks)

```text
6.1  Recall the purpose of these 15 practices (BL1) — 5 marks
     a) Information security management      j) Change enablement
     b) Relationship management             k) Incident management
     c) Supplier management                 l) Problem management
     d) IT asset management                 m) Service request management
     e) Monitoring and event management     n) Service desk
     f) Release management                  o) Service level management
     g) Service configuration management
     h) Deployment management
     i) Continual improvement

6.2  Recall definitions of these terms (BL1) — 2 marks
     a) IT asset            d) Change
     b) Event               e) Incident
     c) Configuration item  f) Problem
                            g) Known error
```

### The 15 practices are not random

**10 of the 15 are general management practices** (a–j in the list above).
Only **5 are service management practices** (k–o):

```text
GENERAL MANAGEMENT PRACTICES (10 of 15)
  information security · relationship · supplier · IT asset
  monitoring and event · release · service configuration
  deployment · continual improvement · change enablement

SERVICE MANAGEMENT PRACTICES (5 of 15)
  incident · problem · service request · service desk · service level
```

That's a classic exam question: given a purpose, identify the practice — and
the traps are usually service-management-sounding purposes assigned to
general-management practices.

### LO6.2 — the seven terms, with the 2019 revised definitions

```text
IT asset            a configuration item that has a financial value
Event               any occurrence or change in state of an object or system
Configuration item  a component having a defined function, an agreed
                    specification, and a place in a supported model
Change              any alteration to a current or future state of an
                    object or system
Incident            an unplanned interruption to a service, or a reduction
                    in the quality of a service
Problem             the underlying cause of one or more incidents
Known error         a problem for which the underlying cause and/or a
                    workaround is known, but it has not yet been fully
                    resolved
```

⚠️ ITIL 4 revised the **problem** and **known error** definitions in a 2019
errata. If your study material is pre-2019 it will say "the cause of one or
more incidents" without "underlying". The distinction that matters:

```text
INCIDENT   = the interruption            (symptom, what users feel)
PROBLEM    = the underlying cause        (why it keeps happening)
KNOWN ERROR= cause/woraround KNOWN, not yet fully resolved
```

Full content: `Practices.md`

---

## 8. LO7 — Seven Practices in Detail (17 marks)

By far the biggest block. All of it is **BL2 "explain in detail, excluding how
they fit within the service value chain"** — so you need the substance, and
you *don't* need to recite SVC placement.

```text
a) Continual improvement
     including the continual improvement model (fig 4.3)
b) Change enablement
c) Incident management
d) Problem management
e) Service request management
f) Service desk
g) Service level management (5.2.15 – 5.2.15.1)
```

Note the wording: **"excluding how they fit within the service value chain."**
That's the syllabus telling you not to waste marks on SVC mapping for these
seven. It also means overlap with `Service_Value_Chain.md` is deliberate, not
duplicated.

Full content: `Practices.md`

---

## 9. What's In and Out of Scope

```text
 ✅ IN SCOPE at Foundation
    • Key concepts, value, utility, warranty, stakeholders
    • 7 guiding principles
    • 4 dimensions
    • SVS and its 5 components
    • 6 SVC activities
    • Purpose of 15 named practices
    • 7 key terms
    • 7 practices explained in detail
    • Continual improvement model

 ❌ NOT AT Foundation (these are higher-level modules)
    • Detailed practice procedures, roles, activities, tools
    • Implementing practices at scale
    • Organizational change in depth
    • Metrics design beyond basic SLM
    • Software development / DevOps tooling practice
      (covered in the Practitioner and MP modules)
```

---

## 10. What the Cert Gets You

Be honest-eyed about this, because it's a Foundation-level credential.

```text
WHAT IT IS
  • An entry-level IT service management qualification
  • Proof you know ITIL 4's vocabulary and structure
  • The prerequisite for all ITIL 4 higher-level modules
  • Widely recognised across 185+ countries
  • Commonly requested for ITSM, service desk and IT ops roles

 WHAT IT ISN'T
  • Not proof you can run an ITSM function
  • Not a management qualification
  • Not a substitute for practitioner experience

 TYPICAL ROLES it supports
  • Service desk / IT support analyst
  • IT operations coordinator
  • Change/release coordinator
  • Junior IT project or service delivery analyst
```

### The ITIL 4 pathway

```text
             ITIL 4 FOUNDATION
              (no prerequisites)
                      │
        ┌─────────────┴─────────────┐
        ▼                           ▼
  PRACTITIONER                 MANAGING
  (2 modules)                  PROFESSIONAL
  • Incident & Problem         (4 modules)
    Management                 • Create, Deliver & Support
  • Change Enablement          • Plan, Implement & Control
                              • Service Request Mgmt
  + optional                    • Service Design & Testing
  • Service Design             + optional
  • Sustainability             • Sustainability
  • Sustainability: Digital    • Enabling Technologies
    & Core Practices
  • Enabling Technologies
  • Drive & Enable             = ITIL MASTER
```

### Career note — the 3-year CPD cycle

Your certificate must be renewed every 3 years by accumulating **60 CPD points**
(or by passing a higher module). That means the credential is a maintenance
commitment, not a one-off. Plan CPDs from the day you pass, and get your
first 3 years organised.

---

## 11. Important 2026 Context — ITIL 5

This affects how you plan your studying, so read it before you book.

```text
 TIMELINE
 ────────
 12 Feb 2026   ITIL (Version 5) officially released
                 • New modules: ITIL Product, ITIL Service, ITIL Experience,
                   ITIL Transformation
                 • Focus shifts from operational thinking to digital product
                   and service lifecycle management
                 • Stronger customer-experience and AI/digital emphasis
                 • More clearly enterprise-wide, not just IT
 2026 →         Phased rollout. ITIL 4 remains available for those continuing
                their ITIL 4 journey
 31 Dec 2027    Current plan: ALL ITIL 4 modules sunset
```

**What this means for you:**

1. **ITIL 4 Foundation is still valid and still sitting** — and ITIL 4 remains
   the mature, widely-demanded version in the job market right now.
2. **The 3-year CPD cycle is a factor.** With sunset on 31 Dec 2027, an ITIL 4
   renewal lands uncomfortably close to the sunset. Do the CPDs, but plan for
   a Foundation Bridge (Version 5) later.
3. **There's a cheap path if you already hold ITIL 4 Foundation:**
   the **ITIL Foundation Bridge (Version 5)** is a one-day course + short exam
   covering only the changes introduced at Foundation level, leading straight
   to ITIL Foundation (Version 5) certification. No need to repeat covered
   content.
4. Bridge is for anyone holding an ITIL 4 qualification (except Cloud and
   Sustainability). Bridge itself is also scheduled to retire 31 Dec 2027.

**Verdict:** Study ITIL 4 if you want the current, in-demand version and the
option to bridge cheaply later. The SVS/SVC knowledge transfers — ITIL 5 builds
on ITIL 4 rather than discarding it.

---

## 12. Exam-Day Tactics

```text
 TIME
 60 min / 40 questions = 90 seconds each
 Don't spend 3 minutes on one item. Flag it, move on, return.

 NO NEGATIVE MARKING
 A blank = certain zero. A guess = a real chance. Always answer.

 NEGATIVE STEMS
 "Which is NOT..." → invert each option before deciding
 "Which is LEAST likely..." → ask which one is MOST likely, then
                             eliminate the other three

 LIST QUESTIONS
 Identify the true statements FIRST, then find the option that pairs them.
 The options are pairs, not statements — a very common misread.

 PRACTICE PURPOSE QUESTIONS
 Learn the 15 practice purposes as precise phrasings. They're recall (BL1)
 so the wording matters.

 SCENARIO QUESTIONS
 Foundational scenarios are usually one-hop. Find the practice or activity
 whose purpose matches the stated problem. Don't overthink multi-step
 reasoning — that would be higher-level material.
```

---

## Key Takeaway

> **40 questions, 60 minutes, closed book, 26 of 40 to pass, no negative
> marking, no prerequisites, Bloom's levels 1–2 only. And 17 of the 40 marks
> sit in seven practices — so study the SVS and SVC for understanding, but
> study the practices to pass.**

```text
 Exam map
 ────────
 5 marks  key concepts
 6 marks  guiding principles
 2 marks  four dimensions
 1 mark   service value system
 2 marks  service value chain
 7 marks  15 practices + 7 terms
17 marks  SEVEN PRACTICES IN DETAIL   ← the biggest prize
────────
40 marks
```
