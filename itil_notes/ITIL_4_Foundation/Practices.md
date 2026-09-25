# ITIL 4 Practices

> Covers **LO6 (7 marks)** and **LO7 (17 marks)** = **24 of 40 marks, 60% of
> the exam.** This is the highest-value file in the folder.

---

## What a Practice Is

> A practice is a set of organizational resources designed for performing work
> or accomplishing an objective.

```text
ITIL v3: PROCESS  =  a defined sequence of steps, with defined inputs,
                     outputs, roles and controls
ITIL 4: PRACTICE  =  resources + capability, scaled to fit the context,
                     with NO defined start or end
```

Consequences of the v3 → v4 shift:

| v3 process | v4 practice |
|---|---|
| Followed as written | Adapted to context |
| Had a defined start and end | No defined start or end |
| One way of doing it | Practices vary by organization |
| Enforced | Enabled and supported |
| Process owner accountable for compliance | Everyone contributes |

You do not "implement a practice" once and finish. You implement it *to an
appropriate level for your organization* and then improve it continually.

### The 34 practices, in 3 categories

```text
 34 practices
 ───────────
  14  General management practices
  17  Service management practices
   3  Technical management practices
 ───────────
  34
```

---

## LO6.1 — Purpose of 15 Practices (BL1 — 5 marks)

Learn these purposes as precise phrasings. These are recall, so wording
matters. Only 15 of the 34 are named on the syllabus.

### The 15 — and their categories

```text
GENERAL MANAGEMENT PRACTICES (10 of the 15)
────────────────────────────────────────────
  information security management
  relationship management
  supplier management
  IT asset management
  monitoring and event management
  release management
  service configuration management
  deployment management
  continual improvement
  change enablement

SERVICE MANAGEMENT PRACTICES (5 of the 15)
────────────────────────────────────────────
  incident management
  problem management
  service request management
  service desk
  service level management
```

⚠️ **10 general vs 5 service.** This is a reliable distractor generator: exam
questions sound service-y but the correct answer is a general practice, and
vice versa. Expect to be tested on the *category* as much as the purpose.

### The 15 purposes

| # | Practice | Category | Purpose |
|---|---|---|---|
| 1 | **Information security management** | General | Manage risks to the confidentiality, integrity and availability of information and services |
| 2 | **Relationship management** | General | Identify, establish and maintain relationships with stakeholders so the organization can maximise the benefits of each relationship |
| 3 | **Supplier management** | General | Ensure the organization's suppliers and their performance are managed appropriately to support the seamless, quality provision of products and services |
| 4 | **IT asset management** | General | Manage the lifecycle and the financial value of IT assets throughout their lifecycle |
| 5 | **Monitoring and event management** | General | Collect and process operational data to support the organization's services, covering event monitoring, performance monitoring, and the analysis of operational data |
| 6 | **Release management** | General | Plan, schedule, build, test and deploy software and hardware changes to production to minimise business disruption |
| 7 | **Service configuration management** | General | Define and control the services, assets, and the configuration items and relationships between them, so the delivered service is understood and traceable |
| 8 | **Deployment management** | Technical | Make new or changed components available appropriately, with the least possible disruption to the customer's business activities |
| 9 | **Continual improvement** | General | Identify and implement changes that are continually improving and enhancing the organization's products and services, practices, and the SVS itself |
| 10 | **Change enablement** | General | Maximise the success of IT changes by assessing and prioritising them, and then scheduling them into implementation and release windows |
| 11 | **Incident management** | Service | Minimise the negative impact by reducing the rate and impact of incidents through a combination of activities to restore normal service as quickly as possible |
| 12 | **Problem management** | Service | Reduce the long-term negative impact of incidents by identifying and eliminating the underlying causes of incidents, or mitigating the effects of recurring incidents where elimination is not possible |
| 13 | **Service request management** | Service | Provide a means for stakeholders to request and get approved service, product or service component enhancements |
| 14 | **Service desk** | Service | Provide a means for service users to find help, and for service support personnel to resolve, and fulfil a variety of user and consumer requests, questions and issues; also acts as a focal point for the organisation's communication |
| 15 | **Service level management** | Service | Define, agree, deliver and support the levels of service required, and monitor them against agreed targets |

### Purpose-recall traps

```text
 ❌ CONFUSING RELEASE vs DEPLOYMENT
   release    = building and moving changes into PRODUCTION
                (the software/hardware change journey)
   deployment = making components available in the right PLACE
                and TIME to users, with least disruption

 ❌ CONFUSING INCIDENT vs PROBLEM
   incident   = restore service as FAST as possible (speed)
   problem    = stop it happening again (prevention, root cause)

 ❌ CONFUSING CHANGE ENABLEMENT vs RELEASE
   change enablement = ASSESS and AUTHORISE changes (decide, schedule)
   release management = BUILD, TEST and DEPLOY (execute)

 ❌ CONFUSING SUPPLIER vs RELATIONSHIP MANAGEMENT
   supplier      = incoming, third-party providers of goods/services
   relationship  = stakeholders more broadly, both directions

 ❌ CONFUSING SERVICE REQUEST vs INCIDENT
   request  = something NEW or a pre-agreed service
   incident = something BROKE
```

---

## LO6.2 — Seven Key Terms (BL1 — 2 marks)

```text
IT asset            A configuration item that has a financial value

Event               Any occurrence or change in state of an object or
                    system. Events can be planned or unplanned.
                    → alerts, changes of state, notifications
                      (some events are informational only)

Configuration item  A component having a defined function, an agreed
   (CI)             specification, and a place in a supported model

Change              Any alteration to a current or future state of an
                    object or system

Incident            An unplanned interruption to a service, or a reduction
                    in the quality of a service

Problem             The underlying cause of one or more incidents

Known error         A problem for which the underlying cause and/or a
                    workaround is known, but it has not yet been fully
                    resolved
```

### Definitions that are commonly out of date

ITIL 4 revised the problem definitions in a **2019 errata**. Pre-2019 study
material is wrong on these two:

```text
 ❌ OLD (pre-2019)          ✅ CURRENT (ITIL 4)
 Problem: "The cause of      Problem: "The underlying cause of
 one or more incidents"       one or more incidents"

 Known error: "A problem     Known error: "A problem for which the
 for which a workaround is   underlying cause and/or a workaround
 known"                      is known, but it has not yet been
                             fully resolved"
```

Why it matters: the current wording makes explicit that you can know the
**cause** *or* a **workaround** — and that a known error is by definition
**not yet fully resolved**. A problem that is fully resolved is no longer a
known error.

### The chain that connects all seven terms

```text
   EVENT                    (something happened — a notification, an alert)
      │
      ▼
   INCIDENT                 (service was interrupted or degraded)
      │                     unplanned
      ▼
   PROBLEM                  (the underlying cause)
      │
      ├── cause known, workaround known, NOT yet fully resolved
      ▼
   KNOWN ERROR
      │
      ▼
   CHANGE                   (a change fixes the cause or adds the workaround)

   ── around the whole thing ──
   CONFIGURATION ITEM        (the component affected; tracked by service
      │                      configuration management)
      ▼
   IT ASSET                 (a CI with financial value)
```

```text
 Symptom chain
 ─────────────
 INCIDENT    = the symptom users feel       → restore fast
 PROBLEM     = why it keeps happening       → eliminate cause
 KNOWN ERROR = we know the cause, not yet fixed → document, plan a fix
 CHANGE      = the actual fix               → enable, authorise, deploy
```

This chain is the most commonly examined relationship in the whole syllabus.
Incident → Problem → Known error → Change is a single conceptual story.

---

## LO7 — Seven Practices in Detail (BL2 — 17 marks)

The biggest block on the exam. All BL2 "explain in detail", and note the
syllabus explicitly says **"excluding how they fit within the service value
chain"** — so don't burn marks on SVC mapping here.

### 1. Service desk (5.2.14)

The **single point of contact (SPOC)** between users and the service provider.

```text
 PURPOSE
   Provide a means for service users to find help, and for service support
   personnel to resolve and fulfil a variety of user and consumer requests,
   questions and issues. Also acts as a focal point for the organisation's
   communication.

 KEY CHARACTERISTICS
   ├── single point of contact for users
   ├── channels: phone, email, chat, self-service portal, walk-up
   ├── handles: incidents, service requests, and questions
   ├── visible, well-communicated, business-aligned
   └── increasingly: self-service + automation as first line

 WHY IT MATTERS (anatomy of a ticket)
   Incidents ──────────────▶ service desk (log, categorise, prioritise)
   Service requests ───────▶ service desk (fulfil, often via fulfilment)
   Questions ──────────────▶ service desk (answer, self-serve)

 ESCALATION
   unresolved → escalate up the agreed path, by the agreed criteria
   (e.g. time breached, impact increased)
```

```text
 ⚠️ The most confused relationship on the syllabus:

 SERVICE REQUEST  ──▶  handled by   ──▶  SERVICE REQUEST MANAGEMENT
 SERVICE DESK                        (the practice that manages
                                       the request lifecycle)

 INCIDENT       ──▶  handled by   ──▶  INCIDENT MANAGEMENT
 SERVICE DESK                        (the practice that manages
                                       the incident lifecycle)

 The service desk is the FRONT DOOR — the point of contact.
 Request and incident management are the PRACTICES doing the work.
 You can have one without the other; you rarely want one without both.
```

### 2. Incident management (5.2.5)

> **Restore normal service as quickly as possible**, reducing rate and impact.

```text
 CORE PRINCIPLE
   Restore normal service as quickly as possible and with minimum impact
   → SPEED and IMPACT REDUCTION are the objectives

 INCIDENT MANAGEMENT IS (usually)
   ├── REACTIVE      (deal with what happened)
   └── NORMALLY     NOT a root cause fix
                      → that's problem management

 WHAT IT INVOLVES
   detect → log → categorise → prioritise → diagnose
        → resolve OR workaround → close

 PRIORITISATION — the standard factors
   ├── impact    (how bad is the effect?)
   └── urgency   (how quickly must it be fixed?)
   → priority = f(impact, urgency)
```

```text
 THE ONE-LINE DISTINCTION FOR THE EXAM
 ─────────────────────────────────────────────
 Incident management  =  RESTORE   (fast, mitigate)
 Problem management   =  PREVENT   (slow, eliminate cause)

 "A workaround was documented" → problem management may record it,
   but a workaround is NOT incident management's job to eliminate.
 "Resolved quickly to restore service" → incident management.
 "Identified the underlying cause"     → problem management.
```

### 3. Problem management (5.2.8)

> **Eliminate the underlying cause** of incidents, or mitigate recurring
> effects where elimination isn't possible.

```text
 CORE PRINCIPLE
   Reduce the long-term negative impact of incidents by eliminating their
   underlying causes — or mitigating where you can't eliminate.

 THE MANAGEMENT PROBLEMS LOG TRACKS
   ├── problem        (the underlying cause)
   ├── known error    (cause or workaround known, not yet resolved)
   └── known workaround (a temporary fix, avoiding the cause)
       → the reason a known error is no longer a big problem

 RELATIONSHIP TO INCIDENT MANAGEMENT
   Incident mgmt = restore now (fast)
   Problem mgmt  = stop it returning (root cause)
   Both needed. A team that only runs incident management is
   forever putting out fires.
```

```text
 SCENARIO CHECK
 ─────────────
 "Same fault each Monday morning, 8 incidents, each resolved in
  under an hour"  → the RAPID RESTORE is incident management.
                      The RECURRENCE is a problem for problem management.
```

### 4. Change enablement (5.2.4)

> Maximise the success of IT changes by assessing, prioritising and
> scheduling them into implementation and release windows.

```text
 PURPOSE
   Maximise the success of changes by:
     ASSESSING → PRIORITISING → SCHEDULING
   and then placing them into implementation/release windows.

 KEY IDEA
   Not "prevent change" — change is inevitable.
   Not "approve everything slowly" — that's the OPPOSITE of the purpose.
   The purpose is to make change SUCCEED: assess it well, schedule it
   to minimise disruption.

 Standard categories of change (know the idea, not the exact table)
   ├── standard changes  (pre-authorised, low risk — implement fast)
   ├── normal changes   (assessed and authorised — the majority)
   └── emergency changes (urgent — expedited retrospective review)
```

```text
 ⚠️ TRAP: "change enablement slows change down"
   WRONG. Slowing successful change down isn't the aim.
   The aim is to make MORE of it succeed with LESS disruption.
   Speeding up low-risk standard change is change enablement WORKING.
```

### 5. Service request management (5.2.16)

> Provide a means for stakeholders to request and get approved service, product
> or service component enhancements.

```text
 PURPOSE
   A single means for stakeholders to REQUEST and get APPROVED
   a service, product or service component enhancement.

 WHAT COUNTS
   ├── access to a new service
   ├── a new device / software licence
   ├── a move or change to an existing service
   ├── information or a report
   └── changes to service levels

 RELATIONSHIP TO SERVICE DESK
   Service desk = the front door (contact point)
   Service request management = the process behind the request
   (authorisation, fulfilment, and closing the request)
```

```text
 ❌ THE #1 MISTAKE: treating every request as an incident
   User asks for a new mailbox  → SERVICE REQUEST (they want something)
   User can't log in at all     → INCIDENT (something's broken)
```

### 6. Service level management (5.2.15)

> Define, agree, deliver and support the levels of service required, and
> monitor them against agreed targets.

```text
 THE FOUR Rs + MONITOR
   DEFINE   the required level of service
   AGREE    it with the consumer (SLA)
   DELIVER  to that level
   SUPPORT  to sustain that level
   MONITOR  against agreed targets (measures, reports, reviews)

 KEY CONCEPT: the SLA
   A service level agreement defines the required PERFORMANCE
   of a service, and the required PERFORMANCE OUTCOMES.
   → "Where are the details of the required performance outcomes
      of a service defined?"  → ANSWER: service level agreements.
      (this is a very common exam question)

 SLM vs SLA
   SLM = the PRACTICE (a capability, ongoing)
   SLA = the AGREEMENT (a document, agreed with the consumer)
```

```text
 SCENARIO CHECK
 ─────────────
 "Targets are set but nobody reviews whether they're being met"
   → SLM covers MONITORING against agreed targets.
      This is what SLM is FOR.

 "A service has a 99.9% availability commitment, measured and reported
  monthly" → that agreement + its monitoring is SLM.
```

### 7. Continual improvement (5.2.1 in practice, see §4.6)

> Identify and implement changes that continually improve and enhance the
> organization's products and services, its practices, and the SVS itself.

```text
 PURPOSE
   Continually improve products, services, practices and the SVS itself.

 THE 4-STAGE CONTINUAL IMPROVEMENT MODEL (this is examinable)
   1. Identify opportunities and gaps
   2. Analyse and prioritize
   3. Implement and review
   4. Embed and communicate

 THREE PRINCIPLES UNDERPINNING CI
   • Focus on value
   • Start where you are
   • Progress iteratively with feedback

 Full detail: Continual_Improvement.md
```

---

## The 19 Practices Not Named on the Syllabus

You don't need their purposes for the exam, but knowing the full 34 shows
you know the framework — and they come up in scenario distractors.

### 14 General management practices

| # | Practice |
|---|---|
| 1 | Architecture management |
| 2 | Continual improvement *(in LO7)* |
| 3 | Information security management *(in LO6)* |
| 4 | Knowledge management |
| 5 | Measurement and reporting |
| 6 | Organizational change management |
| 7 | Portfolio management |
| 8 | Project management |
| 9 | Relationship management *(in LO6)* |
| 10 | Risk management |
| 11 | Service financial management |
| 12 | Strategy management |
| 13 | Supplier management *(in LO6)* |
| 14 | Workforce and talent management |

### 17 Service management practices

| # | Practice |
|---|---|
| 15 | Availability management |
| 16 | Business analysis |
| 17 | Capacity and performance management |
| 18 | Change enablement *(in LO6)* |
| 19 | Incident management *(in LO7)* |
| 20 | IT asset management *(in LO6)* |
| 21 | Monitoring and event management *(in LO6)* |
| 22 | Problem management *(in LO7)* |
| 23 | Release management *(in LO6)* |
| 24 | Service catalogue management |
| 25 | Service configuration management *(in LO6)* |
| 26 | Service continuity management |
| 27 | Service design |
| 28 | Service desk *(in LO7)* |
| 29 | Service level management *(in LO7)* |
| 30 | Service request management *(in LO7)* |
| 31 | Service validation and testing |

### 3 Technical management practices

| # | Practice |
|---|---|
| 32 | Deployment management *(in LO6)* |
| 33 | Infrastructure and platform management |
| 34 | Software development and management |

*(in LO6 = named in LO6.1, purpose tested · in LO7 = one of the 7 detailed)*

```text
 14 + 17 + 3 = 34 ✓
```

---

## How These Practices Map to the SVC

Useful context, though **not tested for LO7** (the syllabus excludes SVC
placement for those seven). Useful for LO6 and for working practice.

```text
 PLAN
   strategy · portfolio · architecture · service financial
   service level · business analysis · risk

 ENGAGE
   relationship · service desk · service request
   supplier · organizational change

 DESIGN & TRANSITION
   service design · service catalogue · service validation/testing
   information security · service level · software development

 OBTAIN/BUILD
   supplier · IT asset · infrastructure & platform
   software development · procurement

 DELIVER & SUPPORT
   incident · problem · change enablement · release · deployment
   monitoring & event · service configuration · availability
   capacity & performance · service desk · service request · service level

 IMPROVE
   continual improvement · measurement & reporting
   knowledge management · risk
```

⚠️ Remember: many practices span multiple activities, and the mapping is
**not** tested for the seven detailed practices. Don't over-learn it.

---

## The v3 → v4 Practice Renames

Worth a quick table, because v3 knowledge actively misleads.

| v3 process | v4 practice |
|---|---|
| Incident management | Incident management |
| Problem management | Problem management |
| Service request fulfilment | **Service request management** |
| IT service continuity management | **Service continuity management** |
| Release management | Release management |
| IT service asset & configuration management | **Service configuration management** *(asset split out to IT asset management)* |
| Service level management | Service level management |
| Service desk | Service desk |
| Change management | **Change enablement** |
| ITIL v2 "service operation" | **34 practices** (no such grouping in v4) |
| Service design | Service design |

**New in v4** (no direct v3 equivalent): information security management,
monitoring and event management, business analysis, service catalogue
management, service validation and testing, workforce and talent management.

---

## Exam Traps to Watch

| Trap | Why students get it wrong | Correct answer |
|---|---|---|
| "A practice is a defined sequence of steps" | v3 process mindset | A practice is **resources + capability**, no defined start/end |
| "Change enablement exists to slow changes down" | Misreading the name | To make changes **succeed** with less disruption |
| "Incident management identifies root causes" | Blurring practices | Incident = **restore fast**; problem = **eliminate cause** |
| "Every ticket the service desk receives is an incident" | Conflating terms | Requests ≠ incidents; both reach the service desk |
| "SLM is the document" | SLM/SLA confusion | SLM = the **practice**; SLA = the **agreement** |
| "Release management authorises changes" | Blurring practices | Change **enablement** authorises; **release** executes |
| "A known error has no known workaround" | Reading the term too literally | A known error is a problem with a known cause **and/or** workaround |
| "Deployment management means deploying to production" | Blurring with release | Deployment = available in the right **place/time**; release = into **production** |
| "Service desk is a practice that resolves incidents" | Role confusion | It's the **contact point**; incident management **resolves** |

---

## Key Takeaway

> **A practice is a set of organizational resources for accomplishing an
> objective — 34 in all. The incident → problem → known error → change chain
> is the spine of the seven detailed practices (17 marks): the service desk is
> the front door, incident management restores fast, problem management
> eliminates causes, change enablement makes change succeed, and service level
> management monitors agreed targets.**

```text
  THE CHAIN THAT EARNS THE MOST MARKS
  ────────────────────────────────────
   INCIDENT    restore fast          (LO7)
        │     symptom users feel
        ▼
   PROBLEM     eliminate cause       (LO7)
        │
        ▼
   KNOWN ERROR cause/workaround known,
        │      not yet resolved      (LO6.2)
        ▼
   CHANGE      the actual fix        (LO6.1)

   Service desk is the front door to all of it.
```

Next: `Continual_Improvement.md`
