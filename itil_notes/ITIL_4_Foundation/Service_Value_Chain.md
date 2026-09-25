# The ITIL 4 Service Value Chain (SVC)

> Syllabus: **LO5 — "Understand the activities of the service value chain,
> and how they interconnect"**
> Worth **2 marks of 40** (5.1 interconnectedness = 1 mark, 5.2 the six
> activities = 1 mark).

---

## What It Is

> An operating model which outlines the key activities required to respond to
> demand and facilitate value realization through the creation and management
> of products and services.

It is the **central element** of the Service Value System. If the SVS is the
whole organism, the SVC is its operating engine.

### Three words that matter

| Word | Implication |
|---|---|
| **operating model** | Describes how work actually flows, not an org chart or a process |
| **respond to demand** | Demand-driven, not plan-driven |
| **facilitate value realization** | Value must actually land, not just be produced |

---

## The Six Activities

```text
                         PLAN
                          │
   ┌──────────────────────┼──────────────────────┐
   │                      │                      │
   ▼                      ▼                      │
 ENGAGE ──▶ DESIGN & TRANSITION ──▶ OBTAIN/BUILD │
              │                          │         │
              └──────────┬───────────────┘         │
                         ▼                         │
                 DELIVER & SUPPORT                 │
                         │                         │
                         ▼                         │
                       IMPROVE ─────────────────────┘
```

Official order as listed in the syllabus:

1. **Plan**
2. **Improve**
3. **Engage**
4. **Design & transition**
5. **Obtain/build**
6. **Deliver & support**

Mnemonic for the set: **PIE D-O-D** — *Plan, Improve, Engage, Design,
Obtain, Deliver*. Another: **"Plan Engages Design, Obtains Delivery, Improves"**.

---

## Each Activity's Purpose

These wordings come straight from the ITIL 4 Foundation syllabus — learn them
close to verbatim, because "describe the purpose of" questions are near-verbatim
scraps of these.

### 1. Plan

> Ensures a shared understanding of the vision, status and improvement
> direction for all four dimensions and all products and services across
> an organization.

```text
What it nails down:
  VISION        where are we going
  STATUS        where are we now
  DIRECTION     how we improve
  SCOPE         all 4 dimensions, all products & services
```

Keyword to remember: **shared understanding**. Plan is about alignment and
direction, not about producing a project plan.

### 2. Improve

> Ensures continual improvement of products, services and practices across all
> value chain activities and the four dimensions of service management.

```text
Scope of improvement (three levels):
  ├── Service improvement          (better outcomes for users)
  ├── Process improvement          (better ways of working)
  └── Organizational improvement  (better across the board)
```

Keyword: **continual**. Not a project, not a one-off. Note it explicitly spans
*all* activities and *all* four dimensions.

### 3. Engage

> Provides a good understanding of stakeholder needs, transparency, and
> continual engagement and good relationships with all stakeholders.

```text
Engagement is:
  ├── two-way, not one-way
  ├── continuous, not a project phase
  ├── about NEEDS, not just requirements capture
  └── across ALL stakeholders, internal and external
```

Keyword: **relationships**. This is where customer/user value is actually
understood. Business engagement is a major driver of SVC success.

### 4. Design and transition

> Ensures products and services continually meet stakeholder expectations
> related to quality, costs and time to market.

```text
The three test criteria:
  QUALITY          does it meet expectations
  COSTS            is it affordable to run
  TIME TO MARKET   does it arrive when needed
```

Keywords: **meet expectations** + the three dials quality / cost / speed.
Note this covers *both* designing something new and transitioning what exists.

### 5. Obtain/build

> Ensures service components are available when and where they are needed and
> meet agreed specifications.

```text
The build-vs-buy decision lives here:
  OBTAIN  →  procure / outsource / lease
  BUILD   →  develop in-house
  Either way: components must be:
              ✓ available WHEN needed
              ✓ available WHERE needed
              ✓ matching AGREED SPECIFICATIONS
```

Keywords: **when**, **where**, **specification**.

### 6. Deliver and support

> Ensures services are delivered and supported according to agreed
> specifications and stakeholders' expectations.

```text
TWO halves:
  DELIVER   the service as specified
  SUPPORT   help, fix, answer, advise

Constraints: agreed specifications + stakeholder expectations
```

Keywords: **agreed specifications** and **support**. This is where most of the
34 practices actually operate day to day.

---

## How the Activities Interconnect

This is the most misunderstood part of the SVC.

### Rule 1: Every activity transforms inputs into outputs

```text
        INPUTS                        OUTPUTS
  ┌──────────────────┐          ┌──────────────────┐
  │ resources        │          │  products &      │
  │ information      │  ────▶   │  services        │
  │ demand           │          │  outcomes        │
  │ other activities'│          │  triggers for    │
  │ outputs          │          │  next activity   │
  └──────────────────┘          └──────────────────┘
```

### Rule 2: Inputs come from two places only

```text
              INPUTS to an activity
         ┌────────────┴────────────┐
         ▼                         ▼
  Demand from OUTSIDE        Outputs of OTHER
  the value chain             activities INSIDE
         │                         │
         └────────────┬────────────┘
                      ▼
             activity runs,
             produces output
```

### Rule 3: Triggers, not queues

Each activity both **receives** triggers for further action and **provides**
triggers to others. The chain is a feedback web, not a conveyor belt.

```text
         ┌──────────┐
         │  ENGAGE  │──── trigger ────┐
         └────┬─────┘                  │
              │                        ▼
              │ trigger        ┌──────────────┐
              ▼                │ DESIGN &     │
         ┌──────────┐          │ TRANSITION   │
         │ OBTAIN / │◀─────────┤              │
         │  BUILD   │          └──────────────┘
         └────┬─────┘
              │ trigger
              ▼
         ┌──────────────┐
         │ DELIVER &    │──── feedback ──▶ back into ENGAGE
         │  SUPPORT     │
         └──────────────┘
```

### Rule 4: There is NO required order

This is the single most examable misconception. The SVC is **not** a sequence
and **not** a lifecycle.

```text
 ❌ WRONG — reading the figure as a pipeline:

   Demand → Plan → Design → Build → Deliver → Improve → done
                             (linear, one pass, fixed order)

 ✅ RIGHT — the SVC as an operating model:

   All six activities available, interconnected, iterated,
   concurrent, and re-entered as many times as the
   organization's work demands.
```

A single real-world service will pass through the same activity many times.
An organization may be designing one service while supporting ten others.

### Rule 5: Value streams are formed *from* SVC activities

```text
  SVC activity types (6, general)  ──combined into──▶  VALUE STREAM
                                                       (specific to an org)
                                                       (a series of steps the
                                                        org uses to create and
                                                        deliver value)

  Value stream: "the series of steps and organization of resources
                 used to create and deliver products and services
                 to a consumer"
```

```text
Example — a value stream "New Employee Onboarding":

  Engage  (find out what the new hire needs)
     ▼
  Plan    (decide what's involved across the 4 dimensions)
     ▼
  Obtain/build  (buy laptops, licences)
     ▼
  Design & transition  (set up accounts, agree how it works)
     ▼
  Deliver & support  (day-one access, help desk help)
     ▼
  Improve  (feedback: onboarding took too long, fix it)

  Every step above is one of the 6 SVC activity TYPES.
  The particular combination is THIS org's value stream.
```

---

## Which Practices Sit Where

The SVC is the "why" and practices are the "how". Most practices are anchored
to a primary activity, though many support more than one.

| SVC activity | Practices you'd most associate |
|---|---|
| **Plan** | Strategy management, portfolio management, architecture management, service financial management, service level management, business analysis |
| **Engage** | Relationship management, service desk, service request management, supplier management |
| **Design & transition** | Service design, service catalogue management, service validation and testing, information security management, organizational change management |
| **Obtain/build** | Supplier management, IT asset management, software development and management, infrastructure and platform management, procurement |
| **Deliver & support** | Incident management, problem management, change enablement, release management, deployment management, monitoring and event management, service configuration management, availability management, capacity and performance management, service desk |
| **Improve** | Continual improvement, measurement and reporting, knowledge management, risk management, information security management |

The syllabus asks for practice **purposes** and the **7 detailed practices** —
not a practice-to-activity mapping table. See `Practices.md`.

---

## Plan and Improve Are Different in Kind

The other four activities do the production work. Plan and Improve are
**meta** — they operate across the whole chain.

```text
  META ACTIVITIES (span everything)     VALUE-ADDING ACTIVITIES
  ┌──────────────────────────┐          ┌──────────────────────────┐
  │  PLAN     direction      │          │  ENGAGE                  │
  │  IMPROVE  getting better │          │  DESIGN & TRANSITION     │
  │                          │          │  OBTAIN/BUILD            │
  │  "how shall we work?"    │          │  DELIVER & SUPPORT       │
  │                          │          │                          │
  │                          │          │  "what work shall we do?" │
  └──────────────────────────┘          └──────────────────────────┘
```

This is why they can be shown spanning the chain in the official figure while
the other four flow between them.

---

## Worked Scenario Questions

The exam will not test SVC theory in the abstract — it tests whether you can
match a situation to the right activity. Practise these mappings.

### Q: A CIO notices three departments each running their own monitoring tools with no shared view of estate health. Which activity, and why?

```text
ANSWER: PLAN

The gap is a lack of a shared understanding of status and direction
across the organization — "a shared understanding of the vision, status
and improvement direction ... across an organization" — combined with a
breakdown in the Information and technology dimension.

NOT Engage:  no stakeholder relationship problem stated
NOT Improve: no existing capability being made better
NOT Obtain/build: not about acquiring components
```

### Q: A supplier contract is being renewed. Buy again or build in-house?

```text
ANSWER: OBTAIN/BUILD

That is the build-vs-buy decision. Purpose: ensure service components
are available when and where needed and meet agreed specifications.

NOT Design & transition: the criteria there are quality, cost and
time to market for the product/service, not the sourcing decision.
```

### Q: A team is restructuring, and new tooling must be adopted by 400 engineers with no resistance.

```text
ANSWER: DESIGN & TRANSITION

Transition is the movement of people and systems into a new state —
adoption is part of it, and it must meet expectations on quality,
cost and time to market.

Also spans: organizational change management (a general practice),
information security management, service design.

NOT Plan: planning the change is not the same as transitioning it.
```

### Q: Ticket backlog grows, users unhappy, and the same fault recurs monthly.

```text
ANSWER: ENGAGE  (stakeholder needs, transparency, relationships)
        +  DELIVER & SUPPORT  (service delivered to expectation)

Recurring faults also point at INCIDENT MANAGEMENT,
PROBLEM MANAGEMENT, CHANGE ENABLEMENT and SERVICE LEVEL
MANAGEMENT (all LO7 practices, 17 marks — see Practices.md).

The SVC framing: the delivery activity is not meeting stakeholder
expectations, and engagement has failed to surface that.
```

---

## Exam Traps to Watch

| Trap | Why students get it wrong | Correct answer |
|---|---|---|
| "The SVC replaces the service lifecycle, and works the same way" | v3 muscle memory | It replaces the lifecycle but is **an operating model with no fixed order** |
| "Plan is the first activity and Improve is the last" | Reading the figure as a flow | No required order; Plan and Improve span all activities |
| "Design and transition is about designing only" | Over-reading "design" | It covers design **and** transition to the new state |
| "Obtain/build is only about buying" | Ignoring the slash | It's obtain **or** build — sourcing includes developing in-house |
| "Deliver and support is only delivery" | Ignoring "and support" | Support (help, fix, advise) is explicitly half of it |
| "Value streams are part of the SVC" | Category confusion | Value streams are **created by combining** SVC activities; the dimension is separate |
| "The SVC only applies to IT services" | Narrow reading | It applies to products and services generally |

---

## Key Takeaway

> **The SVC is an operating model of six interconnected activity types — Plan,
> Improve, Engage, Design and transition, Obtain/build, Deliver and support —
> each transforming inputs into outputs, each both receiving and providing
> triggers. There is no required order, and value streams are formed by
> combining these activities.**

```text
              Opportunity or demand
                       │
     ┌─────────────────┼─────────────────┐
     ▼                 ▼                 ▼
  ENGAGE      DESIGN & TRANSITION   OBTAIN/BUILD
     └─────────────────┬─────────────────┘
                       ▼
               DELIVER & SUPPORT
                       │
                       ▼
                     VALUE

   PLAN      ── sets vision, status, direction (spans all)
   IMPROVE   ── continual improvement      (spans all)
```

Next: `Practices.md` (where the exam's 17 marks live)
