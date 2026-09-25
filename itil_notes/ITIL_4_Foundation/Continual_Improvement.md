# Continual Improvement

> Syllabus: **part of LO7** — "Continual improvement (5.1.2) *including the
> continual improvement model* (4.6, fig 4.3)" — within the **17 marks**.

---

## Why It's a Whole SVS Component

Continual improvement isn't one practice among many. It sits in the SVS as one
of the five components *and* exists as one of the 34 practices. That dual
status is deliberate:

```text
  As an SVS COMPONENT → it's what stops the whole system stagnating
  As a PRACTICE        → continual improvement practice (5.1.2),
                        the capability that drives it
```

> **Purpose:** identify and implement changes that continually improve and
> enhance the organization's products and services, its practices, and the
> SVS itself.

Note the three levels it applies to:

```text
  1. PRODUCTS AND SERVICES   better outcomes for consumers
  2. PRACTICES               better ways of working
  3. THE SVS ITSELF         a better way of doing service management
```

Level 3 is the one people forget. You can improve a service *and* improve
*how you manage services*.

---

## The Four-Stage Continual Improvement Model

This is **fig 4.3** and it is explicitly named in the syllabus — so expect to
be asked to recall or describe these four stages.

```text
  ┌────────────────────────────────────────┐
  │  1. IDENTIFY OPPORTUNITIES AND GAPS    │
  │     what could be better?              │
  │     what are the gaps?                 │
  └───────────────┬────────────────────────┘
                  ▼
  ┌────────────────────────────────────────┐
  │  2. ANALYSE AND PRIORITIZE            │
  │     what's the value? what's the       │
  │     effort? what order?                │
  └───────────────┬────────────────────────┘
                  ▼
  ┌────────────────────────────────────────┐
  │  3. IMPLEMENT AND REVIEW               │
  │     make the change, then check        │
  │     whether it worked                  │
  └───────────────┬────────────────────────┘
                  ▼
  ┌────────────────────────────────────────┐
  │  4. EMBED AND COMMUNICATE              │
  │     make it stick; share the learning   │
  └────────────────────────────────────────┘
```

### Stage detail

| Stage | What happens | Watch out for |
|---|---|---|
| **1. Identify opportunities and gaps** | Find where value isn't being delivered; spot opportunities, and gaps against the SVS's other components | Not a suggestion box — evidence and data |
| **2. Analyse and prioritize** | Evaluate value, effort, risk; decide the order to do things in | Value first — this is where "focus on value" gets applied |
| **3. Implement and review** | Make the change, then measure whether it achieved the intended value | Reviewing is part of the stage, not an afterthought |
| **4. Embed and communicate** | Make the change part of normal working; share the learning | If you don't embed it, you repeat the same project twice |

### Where it's drawn from: PDCA

The model is a service-management rendering of the Plan-Do-Check-Act cycle:

```text
  PDCA                          CI model
  ────                          ────────
  Plan                          1. Identify opportunities and gaps
                                2. Analyse and prioritize

  Do                            3. Implement (and review)

  Check ──────────────────────▶    (the "review" in stage 3)

  Act                           4. Embed and communicate
```

The difference worth knowing: ITIL 4's version makes the *whole thing* a
continual cycle with a defined **prioritization** stage, and it explicitly
includes the three guiding principles below as its foundation.

---

## The Three Principles Underpinning CI

The CI approach is grounded in three guiding principles — not all seven:

```text
  1. FOCUS ON VALUE
     Improvement is only improvement if it creates value.
     → "improvement" that doesn't help a stakeholder is just change

  2. START WHERE YOU ARE
     Understand your current position before choosing what to improve.
     → an honest baseline; realistic goals

  3. PROGRESS ITERATIVELY WITH FEEDBACK
     Small steps, tested as you go, adjusted by the feedback.
     → not a three-year transformation programme
```

So if a question asks which principle underpins continual improvement, the
answer is **those three** — not all seven.

---

## CI and the SVC's Improve Activity

Note the relationship between the CI model and the SVC:

```text
  SVC activity "IMPROVE"
     = "ensures continual improvement of products, services and practices
        across all value chain activities and the four dimensions
        of service management"
              │
              ▼
     is DELIVERED BY the continual improvement practice,
     which runs the 4-stage model, across ALL other
     value chain activities and ALL four dimensions
```

```text
  The "IMPROVE" activity spans everything:

     PLAN ─┐
   ENGAGE ─┤
   DESIGN ─┤
   OBTAIN ─┼── all improved by continual improvement
   DELIVER─┤
  IMPROVE ─┘   (and Improve improves itself)
```

---

## Enabling CI: The Approach

A practice can be "in place" on paper and still produce nothing. ITIL 4
therefore points at the *conditions* that make improvement possible.

### CI enabling conditions

```text
  1. CREATE A SAFE ENVIRONMENT
     People must be able to raise problems and admit mistakes
     without punishment. Improvement dies in a blame culture.

  2. EMBED RESPONSIBILITY
     Improvement can't be a side duty of a service desk team.
     It needs owners with authority and time.

  3. EMBED A CULTURE OF COLLABORATION
     Improvement crosses team boundaries. If the boundaries are
     walled off, cross-cutting improvements don't happen.

  4. FOSTER CREATIVITY
     New solutions need room to be proposed and trialled.
     Not every improvement is obvious up front.

  5. KEEP PEOPLE INFORMED
     Communication is what embeds a change. Silence kills adoption.
```

### Progress, not perfection

The 4-stage model is **iterative**. It is explicitly a cycle, not a project
with an end date. That is why stage 3 includes *review* and stage 4 includes
*embed* — the loop feeds back into stage 1.

```text
   Improve continuously, not occasionally:

   ┌──►[1] identify ──►[2] prioritise ──►[3] implement+review
    │                                          │
    └──────[4] embed+communicate ◄─────────────┘
                     │
              feeds new gaps back into [1]
```

---

## Improvement Activities in ITIL 4

The CI practice covers what people broadly call methodologies. ITIL 4
recognises a family of approaches, all of which are "progress iteratively
with feedback" in practice:

```text
  ┌────────────────────────────────────────────────────┐
  │  AGILE   iterative delivery, short sprints,        │
  │          feedback-driven, prioritised backlogs      │
  ├────────────────────────────────────────────────────┤
  │  LEAN    eliminate waste; optimise flow;           │
  │          value from the consumer's perspective     │
  ├────────────────────────────────────────────────────┤
  │  DevOps  unite development and operations;         │
  │          shorten feedback loops; shared ownership   │
  └────────────────────────────────────────────────────┘
```

None of these is a separate practice — they're approaches the continual
improvement practice can draw on, consistent with the guiding principles.

```text
  Where each maps onto a guiding principle:
    AGILE  ← progress iteratively with feedback
    LEAN   ← keep it simple and practical
    DevOps ← collaborate and promote visibility
            (also: think and work holistically)
```

---

## Scenario Checks

```text
"Teams are frightened to report incidents because they get
 blamed for them"                        → create a safe environment
                                           (an enabling condition)

"The improvement project delivered 40% fewer tickets, but six
 months later the number is back to normal"
                                           → the change wasn't EMBEDDED
                                            (stage 4 skipped)

"Three improvement ideas were chosen because the team thought
 they were interesting, not because they created value"
                                           → focus on value not applied
                                            (stage 2 went wrong)

"A six-month programme is switching everything over on one
 fixed date"                             → progress iteratively with
                                            feedback violated

"The service owner is responsible for driving improvement
 for their own service"
                                           → embed responsibility
                                            (good enabling condition)
```

---

## Exam Traps to Watch

| Trap | Why students get it wrong | Correct answer |
|---|---|---|
| "Continual improvement is a one-off project" | Project mindset | It's a **continuous cycle**, never finished |
| "The model is Identify → Prioritise → Implement → Done" | Skipping stages | Stage 3 includes **review**; stage 4 **embeds and communicates** |
| "CI is underpinned by all seven guiding principles" | Over-generalising | Specifically **three**: focus on value, start where you are, progress iteratively |
| "Improve is the last SVC activity" | Reading the figure as a flow | Improve **spans all** activities and all four dimensions |
| "CI only improves the service" | Narrow scope | It improves **products/services, practices, and the SVS itself** |
| "The review step comes after the model finishes" | Separating it out | Review is **inside** stage 3 |
| "CI needs a dedicated improvement team to work" | Believing in silos | It needs **responsibility embedded** in normal work |

---

## Key Takeaway

> **Continual improvement is both an SVS component and one of the 34
> practices. Its four-stage model — identify opportunities and gaps, analyse
> and prioritize, implement and review, embed and communicate — is grounded in
> three guiding principles, and its purpose spans products and services,
> practices, and the SVS itself.**

```text
  1. IDENTIFY OPPORTUNITIES AND GAPS
              ▼
  2. ANALYSE AND PRIORITIZE
              ▼
  3. IMPLEMENT AND REVIEW
              ▼
  4. EMBED AND COMMUNICATE
              └──► back to 1 (it's a cycle)

  Grounded in: focus on value · start where you are ·
               progress iteratively with feedback
```

Next: `README.md` (index)
