# The Four Dimensions of Service Management

> Syllabus: **LO3 — "Understand the four dimensions of service management"**
> Worth **2 marks of 40**. All BL2 — "describe", not "recall".

---

## What They Are

The SVS is enabled and managed across four dimensions. They are the
"management lens" applied to everything in the SVS.

```text
  ┌────────────────────────────────┐  ┌────────────────────────────────┐
  │  Organizations and people      │  │  Information and technology    │
  │  (the human system)            │  │  (the technical system)       │
  └────────────────────────────────┘  └────────────────────────────────┘
  ┌────────────────────────────────┐  ┌────────────────────────────────┐
  │  Partners and suppliers        │  │  Value streams and processes  │
  │  (the external reach)         │  │  (the way work flows)         │
  └────────────────────────────────┘  └────────────────────────────────┘
```

Mnemonic: **OIPV** (Organizations and people · Information and technology ·
Partners and suppliers · Value streams and processes) or **O-I-P-V** in
syllabus order.

---

## The Four in Detail

### 1. Organizations and people

> The organization and its people — structure, culture, roles, skills,
> relationships, and how work is organised and staffed.

```text
 What lives here
 ├── org structure and operating model
 ├── roles, responsibilities, accountabilities
 ├── skills, capacity, competence, training
 ├── culture, engagement, morale
 ├── relationships between teams and stakeholders
 └── the service desk (as an organisational function)
```

The key insight: IT service management is delivered by **people**, and their
capability is a service management asset. This dimension is why ITIL 4 talks
about workforce and talent management as a general practice.

### 2. Information and technology

> The information and technology used to deliver value — and the information
> and knowledge that the service produces and consumes.

```text
 What lives here
 ├── hardware, software, networks, facilities
 ├── data and information
 ├── knowledge
 ├── cloud, automation, tooling
 ├── information security
 └── architecture and technology strategy
```

Note it's **information AND technology** — data quality and knowledge
management are as much part of this dimension as the servers are.

### 3. Partners and suppliers

> The organizations and people the provider buys from or works with to co-create
> value — including the consumers of the provider's services.

```text
 What lives here
 ├── suppliers (external providers of goods and services)
 ├── partners (collaborative arrangements)
 ├── contractors, third parties
 ├── supply chains
 └── agreements, contracts, and the relationships behind them
```

A notable ITIL 4 broadening: this dimension is not just about *buyers* of IT
services. It covers the whole network the provider participates in, and
crucially the **consumers** of its services sit in this space.

```text
Remember: none of the 4 dimensions can deliver value alone.
They're interdependent — improving one in isolation delivers little.
```

### 4. Value streams and processes

> The way work flows through the organisation to create and deliver value.

```text
 What lives here
 ├── value streams (series of steps to create & deliver value)
 ├── processes (how the work actually gets done)
 ├── work in progress
 ├── dependencies, hand-offs
 ├── throughput, bottlenecks
 └── where value is added and where waste can be eliminated
```

### Value stream vs process — the distinction to nail

```text
 VALUE STREAM
   = the series of steps and organisation of resources used to
     create and deliver products and services to a consumer
   = a FLOW, from demand to value. Maps to combinations of SVC activities.

 PROCESS
   = a set of activities that transform inputs into outputs
   = a CONTAINER of work. Operational, detailed, day-to-day.

 Relation:  value streams are built FROM processes
            processes are the machinery the streams run through
```

A value stream crosses multiple processes, and crosses organisational and
technical boundaries too. That's why the dimension has to be managed
alongside the other three.

---

## How the Dimensions Interact

This is the point of the model. Every product, service, practice and value
stream is managed across all four — a **360-degree** view.

```text
  A new employee onboarding value stream, across all four dimensions:

  Organizations and people      ── HR and IT onboarding roles, a
                                   buddy programme, training
  Information and technology    ── accounts, laptop, email, badge system
  Partners and suppliers        ── the payroll provider, the hardware
                                   supplier, the training vendor
  Value streams and processes   ── the onboarding steps, the access
                                   request process, hand-offs

  Improving only ONE of these = the value stream still fails.
  → that's the "think and work holistically" guiding principle in action.
```

### The dimensions and the SVC are different things

A very common confusion:

```text
 FOUR DIMENSIONS  vs  SIX SVC ACTIVITIES
 ───────────────     ───────────────────
 WHAT must be        WHAT work happens
 managed/optimised      to deliver value

 They intersect but they are NOT the same thing.

 SVC activity "Deliver and support" spans all four dimensions:
   people (who delivers), technology (what's delivered),
   suppliers (who supplies it), streams/processes (how it flows)
```

---

## Exam Traps to Watch

| Trap | Why students get it wrong | Correct answer |
|---|---|---|
| "There are three dimensions" | Confusing with the 5 SVS components | **Four** dimensions |
| Listing the SVC activities as dimensions" | Conflating the two models | SVC = activities; dimensions = what you manage |
| "Partners and suppliers means only outsourcing" | Narrow reading | Covers partners, suppliers, contractors and consumers of the service |
| "Information and technology means hardware only" | Literal reading | It's information **and** technology — data and knowledge count too |
| "Value streams and processes is about IT process documentation" | v3 process mindset | It's about how work **flows** to create value, not documentation |
| "You can prioritise one dimension and ignore the rest" | Misapplying the model | All four must be managed; no dimension delivers value alone |

### Quick scenario checks

```text
"People are leaving because there's no career path"           → Organizations and people
"Three systems don't share data"                              → Information and technology
"A supplier missed a delivery commitment"                     → Partners and suppliers
"Work queues behind one approval step"                        → Value streams and processes
"Staff are well-trained but keep crossing org boundaries
 to fix issues"                                                → Organizations and people (the
                                                                blocker is structural,
                                                                not a skills gap)
```

---

## Key Takeaway

> **The four dimensions are the management lens applied across the whole SVS:
> Organizations and people, Information and technology, Partners and
> suppliers, Value streams and processes. Every value stream and practice is
> managed through all four, because none of them delivers value alone.**

```text
  O  Organizations and people        — can the people do it?
  I  Information and technology      — do we have what we need?
  P  Partners and suppliers          — can we rely on others?
  V  Value streams and processes     — does the work actually flow?

  All four, every time. "OIPV"
```

Next: `Key_Concepts.md`
