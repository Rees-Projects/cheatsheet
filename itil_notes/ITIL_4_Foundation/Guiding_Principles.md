# The 7 Guiding Principles

> Syllabus: **LO2 — "Understand how the ITIL guiding principles can help an
> organization adopt and adapt service management"**
> Worth **6 marks of 40** (2.1 nature/use/interaction = 1 mark,
> 2.2 explaining the use of each principle = 5 marks — one per principle).

---

## What They Are

> Universal guides that an organization uses to support actions and decisions.

Note the deliberate word choice:

| Word | Not |
|---|---|
| **guides** | ...they are not rules or mandates |
| **universal** | ...they are not IT-specific or sector-specific |
| **support** | ...they do not replace judgement |

You don't "comply with" a guiding principle. You use them to make better
decisions. An organization that follows all seven perfectly but creates no
value has still failed.

### 2.1 — Their nature, use and interaction (1 mark)

```text
NATURE      universal, directional, guiding not governing
USE         to inform decision-making at every level
INTERACTION they reinforce each other and interact with ALL other
            SVS components — principles do not sit in isolation
```

They are the "how to think" layer of the SVS:

```text
  Guiding principles = the mindset
  Practices          = the capability
  SVC                = the activity
  Governance         = the direction
  Continual improvement = the evolution
```

---

## The Seven Principles

The canonical order, with the key idea for each:

| # | Principle | Core idea |
|---|---|---|
| 1 | **Focus on value** | Everything must deliver value; value is defined by the stakeholder |
| 2 | **Start where you are** | Assess current position with realistic goals, don't copy blindly |
| 3 | **Progress iteratively with feedback** | Small steps, frequent feedback, course correction |
| 4 | **Collaborate and promote visibility** | Reduce silos; make work and its state visible |
| 5 | **Think and work holistically** | Optimise the system, not local parts |
| 6 | **Keep it simple and practical** | Remove anything that adds no value; perfect is the enemy |
| 7 | **Optimize and automate** | Automate the work, and the processes behind the work |

### 1. Focus on value

All products and services are means to an end — **value**. Value is
co-created between provider and consumer.

```text
 ❌ "We deployed the new ticketing tool. Success."
 ✅ "Ticket backlog dropped 40%, so 300 users got help faster.
     That's the value we focused on."
```

The test: *whose value?* Value is only meaningful relative to a **specific
stakeholder**. A change that creates value for the service desk but removes it
for end users has not created value — it has moved it.

```text
Practice this by:  tying every initiative to a stakeholder outcome,
                   and being able to state the value being created
```

### 2. Start where you are

Every organization, program and process needs three things:

```text
 ┌──────────────────────────────────────────────┐
 │  1. A starting point  — where you are NOW    │
 │  2. A desired goal   — where you WANT to be │
 │  3. A roadmap        — how you'll get there │
 └──────────────────────────────────────────────┘
```

```text
 ❌ "We should be like that other company. Copy their model."
 ✅ "Our incident volume is 8% of theirs and our change success is
     97%. Start from that, target change success, fix the changes."
```

It's about being **realistic** and **not reinventing** what's already there.
Adopt what's good, adapt what suits your context, ignore what doesn't.

### 3. Progress iteratively with feedback

Small increments, delivered and evaluated continuously. Contrast with the
big-bang approach:

```text
 BIG BANG (waterfall)                    ITERATIVE
 ─────────────────────                   ─────────────────────
 Plan ─────────► launch                   Plan → build → release → learn
        12 months                                  2 weeks
         ▲                                              ▲
         │                                              │
    one big feedback                            feedback, then next
    at the end                                  increment
      │                                              │
      └──── if it failed, you find out ───────────────┘
            12 months later
```

"Progress" is not "finish the project". It's steady movement with feedback at
every step. This is where **agile** comes into ITIL 4 — iterative delivery and
feedback are the modern expression of this principle.

### 4. Collaborate and promote visibility

Two ideas in one principle:

```text
 COLLABORATE       work across boundaries, not in silos
 PROMOTE VISIBILITY  make work, its state and its blockers visible
```

```text
 BEFORE (silos)                    AFTER (collaborative + visible)
 ────────────────                  ──────────────────────────────
 Dev ──┐                           Dev ←──→ Ops ←──→ Security
 Ops ──┤  no shared                ┌──────────────────────────┐
 Sec ──┘  state                    │ shared backlog, visible  │
                                   │ dependencies, common     │
                                   │ dashboard                │
                                   └──────────────────────────┘
```

Visibility reduces waste because hidden work and hidden risk are where
projects die.

### 5. Think and work holistically

Optimise the **whole system**, not the local maximum. This is the principle
people most agree with and most violate.

```text
 LOCAL OPTIMISATION                    SYSTEM OPTIMISATION
 (makes one number look good)          (makes the org work better)
 ────────────────────────              ───────────────────────────
 "Cut the help desk headcount          "Reduce repeat incidents so
  to hit the budget target"             demand falls and we can
                                        right-size the team"

      local KPI ✔                            whole system ✔
      org suffers ✘                          org benefits ✔
```

Classic local-optimum traps:

- Reducing training budget to hit a cost target, then paying more in errors
- Making each team's utilisation 100%, destroying the slack that absorbs
  incidents
- Optimising a process that shouldn't exist at all

### 6. Keep it simple and practical

Remove anything that doesn't add value. "Simple" means using the minimum
number of components, processes and practices to deliver value.

```text
 BEFORE: 15 steps, 9 tools, 4 approvals, 3 duplicated registers
 AFTER:  6 steps, 2 tools, 1 approval, one source of truth
         ──────────────────────────────────────────────
         both can deliver the same VALUE. The second is
         better because it removes waste.
```

This is the principle that keeps ITIL from becoming bureaucratic. It's also
what makes practices scalable — a practice should be as simple as the
context allows. And it protects against **process for its own sake**.

```text
"If it doesn't add value, it should be removed"
"If a process adds no value, it adds cost and risk"
```

### 7. Optimize and automate

Two distinct moves, and the distinction is examinable:

```text
 OPTIMIZE   do things better  (make the process itself more efficient)
 AUTOMATE    do things without  (remove the human from the execution,
              human hands         leaving them to judgement)
```

```text
 OPTIMIZE:  Simplify the approval route from 4 steps to 2.
 AUTOMATE:  Auto-approve low-risk changes under a defined threshold.
```

An organisation can automate a badly designed process — in which case you've
just made the bad design faster and harder to change. So the ITIL 4 order
matters: **optimize first, then automate.** Also note what should *not* be
automated away: work requiring creativity, empathy and judgement.

---

## How the Principles Interact

The syllabus asks about interaction, so know that they reinforce each other
rather than operating as a checklist.

```text
  Start where you are ──────┐
            │                │ honest baseline
            ▼                │
  Progress iteratively ◄────┘ fast feedback, small steps
            │                │
            ▼                │
       Optimize ──────▶ Automate
            │          (optimize FIRST, then automate)
            │
            ▼
    Keep it simple and practical
            │
            ▼
     Think and work holistically
            │
            ▼
  Collaborate and promote visibility
            │
            ▼
      Focus on value
      (the test everything else is judged against)
```

Worked interactions:

| Combination | What it produces |
|---|---|
| Start where you are + Progress iteratively | Realistic, achievable improvement roadmap |
| Collaborate + Promote visibility | Holistic view of the work across silos |
| Keep it simple + Optimize | Efficiency gains rather than bureaucratic overhead |
| Focus on value + Think holistically | No local optimisation that destroys system value |
| Progress iteratively + Optimize/automate | Incremental efficiency gains that actually stick |

---

## Exam Traps to Watch

| Trap | Why students get it wrong | Correct answer |
|---|---|---|
| "Guiding principles are rules to comply with" | Reading "guidance" as mandate | They are universal **guides** that support decisions |
| "Focus on value means the business defines the value" | Half-remembering | Value is **co-created**; and value is defined by the **stakeholder** |
| "Start where you are means do nothing until perfect" | Misreading | It means assess realistically, then improve from there |
| "Progress iteratively means fix everything first then go live" | Waterfall habits | Small increments delivered and evaluated continuously |
| "Think holistically means a big-bang transformation" | Confusing scope with style | Holistic = think about the whole system; it can still be incremental |
| "Automate the process, then optimize it later" | Wrong order | **Optimize first, then automate** |
| "Keep it simple means avoid practices and be informal" | Over-reading | Remove things that add no value — not rigour |

### Scenario → principle matching (the main question style for 2.2)

```text
"A team is measured on ticket closure count, so they're closing
 tickets without resolving them."
   → THINK AND WORK HOLISTICALLY
     (optimising a local metric at the system's expense)

"Three teams each built their own CMDB and now disagree about
 what assets exist."
   → COLLABORATE AND PROMOTE VISIBILITY
     (silos, no shared visible truth)

"Leadership wants to implement the same tooling used by a
 Fortune 500 bank next quarter, regardless of our size."
   → START WHERE YOU ARE
     (ignoring our actual starting point)

"We automated the incident approval process, but it was a mess,
 so approvals now happen faster and break more often."
   → OPTIMIZE AND AUTOMATE
     (automated before optimizing)

"The steering committee wants all 20 practices implemented
 before we switch on a single service."
   → PROGRESS ITERATIVELY WITH FEEDBACK
     (big-bang, no increments) and
     KEEP IT SIMPLE AND PRACTICAL

"New tooling was delivered, but the business never stopped using
 spreadsheets because nobody showed them the value."
   → FOCUS ON VALUE
     (no value communicated or perceived → no adoption)
```

---

## Key Takeaway

> **Seven universal guides that support — never dictate — decisions across the
> whole SVS: focus on value, start where you are, progress iteratively with
> feedback, collaborate and promote visibility, think and work holistically,
> keep it simple and practical, optimize and automate.**

```text
   F  Focus on value
   S  Start where you are
   P  Progress iteratively with feedback
   C  Collaborate and promote visibility
   T  Think and work holistically
   K  Keep it simple and practical
   O  Optimize and automate

   "FSPC TKO"   ←  F-S-P-C-T-K-O
```

Next: `Four_Dimensions.md`
