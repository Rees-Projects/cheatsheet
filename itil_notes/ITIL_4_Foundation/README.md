# ITIL 4 Foundation — Notes Index

Study notes for the ITIL 4 Foundation certification, covering the Service Value
System, the Service Value Chain, and everything else the exam tests.

Facts verified against the official AXELOS/PeopleCert candidate syllabus
(`EN_ITIL4_FND_2019_CandidateSyll_v1.4`) and the PeopleCert product page.

---

## Start Here

| File | What it covers | Marks |
|---|---|---|
| **[Exam_Brief.md](Exam_Brief.md)** | Exam format, question types, full syllabus, mark distribution, career path, ITIL 5 status | — |
| **[Service_Value_System.md](Service_Value_System.md)** | The SVS in depth — 5 components, inputs/outputs, value, traps | 1 |
| **[Service_Value_Chain.md](Service_Value_Chain.md)** | The SVC in depth — 6 activities, interconnection, value streams, worked scenarios | 2 |
| **[Key_Concepts.md](Key_Concepts.md)** | Service, utility, warranty, value, output/outcome, risk, service relationships | 5 |
| **[Guiding_Principles.md](Guiding_Principles.md)** | All 7 principles, their interaction, scenario matching | 6 |
| **[Four_Dimensions.md](Four_Dimensions.md)** | The 4 dimensions and how they interact | 2 |
| **[Practices.md](Practices.md)** | All 34 practices, 15 purposes, 7 key terms, 7 detailed practices | 24 |
| **[Continual_Improvement.md](Continual_Improvement.md)** | The 4-stage CI model, 3 underpinning principles, enabling conditions | (part of 24) |

---

## Recommended Reading Order

Two orders depending on your goal.

### To pass the exam

Study by mark value, biggest prize first:

```text
  1. Practices.md              24 marks  60%   ← start here
  2. Guiding_Principles.md      6 marks  15%
  3. Key_Concepts.md            5 marks  12.5%
  4. Continual_Improvement.md   (inside the 24)
  5. Exam_Brief.md              read early, re-read before booking
  6. Four_Dimensions.md         2 marks   5%
  7. Service_Value_System.md    1 mark   2.5%
  8. Service_Value_Chain.md     2 marks   5%
```

### To actually understand service management

Study conceptually, in the order the framework builds:

```text
  1. Exam_Brief.md              know what you're being tested on
  2. Key_Concepts.md            the vocabulary — value, utility, warranty
  3. Service_Value_System.md    the big picture
  4. Service_Value_Chain.md     where the work happens
  5. Four_Dimensions.md         the lens you manage through
  6. Guiding_Principles.md      how to think
  7. Practices.md               the capabilities
  8. Continual_Improvement.md  how it gets better
```

---

## Exam Snapshot

```text
  Questions       40, one mark each
  Pass mark       26 / 40  (65%)
  Duration        60 min  (75 min non-native language)
  Book            closed book
  Negative marking none — always answer
  Prerequisites   none
  Level           Bloom's 1 & 2 only (recall + understand)
  Renewal         every 3 years, 60 CPD points
```

### Where the 40 marks are

```text
  LO7  7 practices in detail      17  █████████████████  42.5%
  LO6  15 practices + 7 terms       7  ███████            17.5%
  LO2  Guiding principles           6  ██████             15%
  LO1  Key concepts                 5  █████              12.5%
  LO3  Four dimensions              2  ██                  5%
  LO5  Service value chain          2  ██                  5%
  LO4  Service value system         1  █                   2.5%
      ─────────────────────────────────────────
      TOTAL                        40
```

> **Headline:** the SVS (1 mark) and SVC (2 marks) together are worth 3 of 40.
> Learn them because they make everything else make sense — but spend your
> revision hours on the practices, where 24 of 40 marks live.

Full breakdown: [Exam_Brief.md](Exam_Brief.md)

---

## The One-Page Version of ITIL 4

```text
                    OPPORTUNITY OR DEMAND
                             │
                             ▼
  ┌──────────────────────────────────────────────────┐
  │            SERVICE VALUE SYSTEM (SVS)            │
  │                                                  │
  │   • Guiding principles        (7)                │
  │   • Governance                                   │
  │   • Service value chain        (6 activities) ← CENTRAL
  │   • Practices                   (34)              │
  │   • Continual improvement      (4 stages)        │
  │                                                  │
  │   across 4 dimensions:                            │
  │   Organizations and people · Information and      │
  │   technology · Partners and suppliers ·           │
  │   Value streams and processes                     │
  └──────────────────────────────────────────────────┘
                             │
                             ▼
                          VALUE
```

### The SVC's six activities

```text
  PLAN          vision, status, direction
  ENGAGE        stakeholder needs, transparency, relationships
  DESIGN &      meet expectations on quality, cost,
  TRANSITION    time to market
  OBTAIN/BUILD  components available when, where, to spec
  DELIVER &     delivered and supported to agreed
  SUPPORT       specifications and expectations
  IMPROVE       continual improvement across all activities
                and all four dimensions
```

### The seven guiding principles

```text
  Focus on value
  Start where you are
  Progress iteratively with feedback
  Collaborate and promote visibility
  Think and work holistically
  Keep it simple and practical
  Optimize and automate
```

### The four dimensions

```text
  Organizations and people
  Information and technology
  Partners and suppliers
  Value streams and processes
```

### The chain that earns the most marks

```text
  INCIDENT    → restore fast        → incident management
  PROBLEM     → eliminate cause     → problem management
  KNOWN ERROR → cause known, unresolved
  CHANGE      → the fix             → change enablement

  All of it arrives through the SERVICE DESK, and is measured
  against targets by SERVICE LEVEL MANAGEMENT.
```

---

## Note on ITIL 5

ITIL (Version 5) was released on **12 February 2026**, and PeopleCert's current
plan is to **sunset all ITIL 4 modules on 31 December 2027**.

ITIL 4 Foundation is still valid and still sitting, and remains the mature,
in-demand version. If you already hold it, the **ITIL Foundation Bridge
(Version 5)** is a one-day course and short exam covering only the changes
introduced at Foundation level.

Strategy notes: [Exam_Brief.md §11](Exam_Brief.md)

---

## Conventions Used in These Notes

- **Diagrams** are in fenced `text` blocks so they render in any Markdown viewer.
- **Purple blockquotes** are official AXELOS definitions — worth memorising
  close to verbatim.
- **`⚠️ TRAP`** callouts mark the most commonly missed points, based on where
  v3 knowledge actively misleads.
- **Scenario blocks** use the format exam scenario questions actually take, so
  you can practise the mapping.
- Official syllabus wording is quoted where the exam asks you to "describe" or
  "recall" something — the phrasing is what earns the mark.
