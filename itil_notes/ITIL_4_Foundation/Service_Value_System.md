# The ITIL 4 Service Value System (SVS)

> Syllabus: **LO4 — "Understand the purpose and components of the ITIL service value system"**
> Worth **1 mark of 40** on the exam, but it is the conceptual spine of the whole framework.

---

## What It Is

The official AXELOS definition:

> A model representing how all the components and activities of an organization
> work together to facilitate value creation.

Read that definition carefully, because every word is load-bearing:

| Word in the definition | What it is telling you |
|---|---|
| **model** | It's a way of *thinking*, not a procedure to follow |
| **how** | It explains mechanisms, it doesn't dictate steps |
| **all components and activities** | Nothing is optional, nothing sits outside |
| **work together** | Interconnection is the point, not the parts |
| **facilitate value creation** | IT is an enabler, value is the goal |

### What the SVS is NOT

This is a favourite exam trap area. The SVS is:

- NOT a process or a sequence to follow
- NOT a lifecycle (it replaced the ITIL v3 **service lifecycle**)
- NOT only about IT — it's about the whole organization
- NOT a "best practice" pick-and-mix; it's one integrated system

```text
ITIL v3                          ITIL 4
──────────                       ──────
Service Lifecycle                Service Value System
(5 sequential stages)            (interconnected, no fixed order)
     ↓                                 ↓
"Service Management"              "Service Management" (widened)
```

The shift in v4: from managing **IT services** to managing **services** (which are tech-enabled but owned by the business).

---

## The Shape of the SVS

```text
                          OPPORTUNITY OR DEMAND
                          (stakeholder need — internal or external)
                                       │
                                       ▼
     ┌─────────────────────────────────────────────────────────────────┐
     │                                                                 │
     │   ┌───────────────┐    ┌────────────────┐    ┌────────────────┐   │
     │   │   Guiding     │    │   Governance   │    │  Continual     │   │
     │   │   principles  │    │                │    │  improvement   │   │
     │   └───────────────┘    └────────────────┘    └────────────────┘   │
     │                                                                 │
     │   ┌──────────────────────────────────────────────────────┐      │
     │   │              SERVICE VALUE CHAIN                    │      │
     │   │   (the central element — where the work happens)    │      │
     │   └──────────────────────────────────────────────────────┘      │
     │                                                                 │
     │   ┌──────────────────────────────────────────────────────┐      │
     │   │   34 Practices (14 general / 17 service / 3 tech)    │      │
     │   └──────────────────────────────────────────────────────┘      │
     │                                                                 │
     └─────────────────────────────────────────────────────────────────┘
                                       │
                                       ▼
                                    VALUE
                       (outcomes for stakeholders — good AND bad)
```

Five components. The Service Value Chain sits in the middle and is described as
the **central element** of the SVS.

### Inputs and Outputs

```text
INPUT   = Opportunity or demand
          ├── External demand (customers, users, partners)
          └── Internal demand (other departments, business units)

OUTPUT  = Value
          ├── Perceived benefit, gain and importance
          ├── For a specific stakeholder
          └── Can be NEGATIVE — value is the *total* effect
```

### Co-creation, not delivery

This is a key v4 message. ITIL 4 says value is **co-created**, not handed over.

```text
ITIL v3 mindset                ITIL 4 mindset
─────────────                  ──────────────
Provider ──delivers──►         Provider ◄──co-create──► Consumer
  service                          value
                                     │
                    (both parties contribute; the provider
                     cannot create value alone)
```

The provider supplies the **means**; the consumer determines whether value
actually materialises.

---

## The Five Components in Detail

### 1. Guiding principles

Universal guides that underpin **all** decisions and actions.

- 7 principles
- They are directional, not rules
- Full detail: `Guiding_Principles.md`

```text
Focus on value            Start where you are
Progress iteratively      Collaborate and promote visibility
with feedback             Think and work holistically
Keep it simple and        Optimize and automate
practical
```

### 2. Governance

> The act of directing, controlling and monitoring an organization's work
> to meet organizational objectives and create value.

Without governance, value-creation activity drifts away from organizational
objectives. The SVS diagram shows governance as the control layer that keeps
the whole system pointed at the right target.

```text
           Organizational objectives
                     │
                     ▼
   ┌───────────────────────────────────────┐
   │             GOVERNANCE               │
   │   direct  ·  control  ·  monitor     │
   └───────────────────────────────────────┘
                     │
      keeps aligned ─┴─ holds the SVS to account
```

### 3. Service value chain

The operating model listing the activities that turn demand into value.

- 6 activities
- Interconnected, no required order
- Full detail: `Service_Value_Chain.md`

```text
Plan · Engage · Design and transition · Obtain/build · Deliver and support · Improve
```

### 4. Practices (34 of them)

> A practice is a set of organizational resources designed for performing work
> or accomplishing an objective.

Replace the v3 word **"process"**. The shift matters:

```text
ITIL v3: process (a defined sequence of steps)
ITIL 4: practice (resources + capability, scaled to fit the context)
```

A practice is not a procedure. It has **no defined start or end**, and an
organization implements it to whatever degree suits it.

```text
 14 General management practices
 17 Service management practices
  3 Technical management practices
 ────────────────────────────────
 34 total
```

Full list: `Practices.md`

### 5. Continual improvement

The mechanism that makes the whole system get better rather than drift.

- Modelled on PDCA
- 4-stage continual improvement model
- Full detail: `Continual_Improvement.md`

---

## The Four Dimensions (supporting the SVS)

The SVS is enabled by management across four dimensions. They sit *outside* the
five components but every component and practice operates across all four.

```text
 ┌──────────────────────────┐   ┌──────────────────────────┐
 │  Organizations and       │   │  Information and         │
 │  people                  │   │  technology              │
 └──────────────────────────┘   └──────────────────────────┘
 ┌──────────────────────────┐   ┌──────────────────────────┐
 │  Partners and suppliers  │   │  Value streams and       │
 │                          │   │  processes               │
 └──────────────────────────┘   └──────────────────────────┘
```

Full detail: `Four_Dimensions.md`

---

## Why "System" and Not "Framework"?

A **framework** is a collection of parts you can select from. A **system** means
the parts are interdependent and the whole is greater than the sum.

```text
Framework = toolbox. Pick the tools you like.
System    = organism. Remove a limb and the rest must compensate.
```

Consequences for the exam and for practice:

- You cannot "just implement" incident management in isolation; it needs the
  other practices, the practices need the SVC, the SVC needs the dimensions.
- Improvement in one place has knock-on effects elsewhere.
- Practitioner's job is to fit practices to context, not to copy a reference
  process library.

---

## Value in the SVS

**Value** is the perceived benefit, gain and importance of using a product or
service. Two things determine whether value is delivered:

```text
  UTILITY   +   WARRANTY   =   VALUE
 (does it work?)   (does it keep working as promised?)
```

```text
Utility   : the ability of a product/service to satisfy one or more needs
            of a customer or consumer
            → fitness for purpose

Warranty  : the promise that a service will, when used as the customer
            intends, provide useful and desired outcomes as stated in the
            service level agreement
            → assurance, grade, dependability
```

Value is also perceived differently by different groups:

| Value type | Whose value? | Example |
|---|---|---|
| **Individual** | One person | Employee saving 2 hrs/week with a new self-service tool |
| **Collective** | A group / org | Reduced cost to serve across 400 users |
| **Societal** | Wider society | Accessible design for users with disabilities |

More on this in `Key_Concepts.md`.

---

## Stakeholders and Value

Value is always value **for someone**. The SVS converts demand from many
stakeholders into value for those same stakeholders.

```text
         STAKEHOLDERS
   ┌─────────┬──────────┬───────────┬──────────────┐
   │Sponsor  │ Customer │   User    │  Provider    │
   │authorise│ buys &   │ uses the  │  (and their  │
   │& budgets│ uses     │ products  │   own staff)  │
   └─────────┴──────────┴───────────┴──────────────┘
        │          │            │            │
        └──────────┴──── demand ─┴────────────┘
                          │
                          ▼
                  demand enters the SVS
                          │
                    value returns
```

Note the provider's own people are stakeholders too — value co-creation is not
one-directional.

---

## Exam Traps to Watch

| Trap | Why students get it wrong | Correct answer |
|---|---|---|
| "The SVC is a lifecycle" | v3 muscle memory | It is an operating model, explicitly **not** a lifecycle |
| "Practices are processes" | v3 muscle memory | Practices are sets of **resources**, no defined start/end |
| "The SVS includes IT only" | Over-narrow reading | Service management applies to **all** services |
| "The SVC activities happen in order" | Reading the figure left-to-right | No required order; they are interconnected |
| "Value is always positive" | Common assumption | Value is the **total** effect, good and bad |
| "Governance is optional for small orgs" | Assuming | Governance is a core SVS component |
| "The SVC is one of five optional parts" | Miscounting | The SVC is the **central element** |

---

## Key Takeaway

> **The SVS shows how everything in the organization works together to create
> value — demand goes in, value comes out, and the five components (guiding
> principles, governance, service value chain, practices, continual improvement)
> are what make that conversion happen.**

```text
              OPPORTUNITY / DEMAND
                        │
                        ▼
   ┌────────────────────────────────────────────┐
   │  guiding principles · governance            │
   │  service value chain (CENTRAL)              │
   │  34 practices · continual improvement       │
   │                                            │
   │  across all 4 dimensions                    │
   └────────────────────────────────────────────┘
                        │
                        ▼
                     VALUE
```

Next: `Service_Value_Chain.md`
