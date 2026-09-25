# Key Concepts of Service Management

> Syllabus: **LO1 — "Understand the key concepts of service management"**
> Worth **5 marks of 40**:
> 1.1 recall definitions of 7 terms = 2 marks (BL1)
> 1.2 describe 8 value concepts = 2 marks (BL2)
> 1.3 describe 4 service relationship concepts = 1 mark (BL2)

---

## 1.1 The Seven Definitions (BL1 — 2 marks)

Pure recall. Learn these close to verbatim.

### Service

> A means of enabling value co-creation by making outcomes consumable by one
> or more customers (the beneficiaries).

The single most important word is **means**. A service is not the thing that
matters — it's the *means* by which outcomes become usable. A report isn't a
service; a reporting capability that gives someone a decision they can act on
is.

### Utility

> The ability of a product or service to satisfy one or more needs of a
> customer or consumer.

```text
Utility  =  does it actually work for the purpose?
          =  fitness for purpose
          =  functionality, right to use, completeness, convenience, time
```

### Warranty

> The promise that a service will (when used as the customer intends) provide
> useful and desired outcomes as stated in the service level agreement.

```text
Warranty =  will it keep working, as promised?
          =  assurance, grade, dependability
          =  availability, capacity, continuity, security, restore time
```

### Customer

> A person who buys and uses the products or services.

### User

> A person who uses the products or services.

```text
They overlap but are NOT the same.

 In a personal IT scenario:
   Customer = the person who paid for the laptop
   User     = the person who actually works on it
              (the company pays, the employee uses)

 In a consumer scenario:
   Customer = user = the same person
```

### Sponsor

> A person who authorises, funds and sets priority for business change.

```text
Sponsor  =  authorises  +  funds  +  prioritises
Customer =  buys and uses
User     =  uses
```

### Service management

> Specifying the value that a business organization requires from an IT
> service, providing that value, and measuring the value delivered.

```text
Three parts, and note that MEASURING is built in:

   specify  →  provide  →  measure
     the          the         the
    value         value       value
                              delivered

If you can't measure the value delivered, you're not doing service
management — you're just doing IT.
```

### Utility + Warranty = Value

```text
  ┌───────────┐   ┌───────────┐   ┌───────────┐
  │  UTILITY  │ + │ WARRANTY  │ = │   VALUE   │
  │           │   │           │   │           │
  │  does it  │   │ does it   │   │ perceived │
  │  work?    │   │ keep      │   │ benefit,  │
  │           │   │ working?  │   │ gain,     │
  │  fitness  │   │ assurance │   │ importance│
  │  for      │   │           │   │           │
  │  purpose  │   │           │   │           │
  └───────────┘   └───────────┘   └───────────┘
```

Neither alone is enough. A product can be beautifully engineered (high
utility) but unreliable (no warranty) — no value. Or rock-solid (high
warranty) but does the wrong job (no utility) — no value.

### Quick-fire recall table

| Term | Recall in five words |
|---|---|
| Service | means of enabling value co-creation |
| Utility | ability to satisfy a need |
| Warranty | promise to provide useful outcomes as stated |
| Customer | buys and uses |
| User | uses |
| Sponsor | authorises, funds, prioritises |
| Service management | specify, provide, measure the value |

---

## 1.2 Creating Value With Services (BL2 — 2 marks)

Not just recall here — you must be able to *describe* how these relate.

### Value

> The perceived benefit, gain and importance to an organization of using a
> product or service.

Three words doing the work: **perceived**, **benefit/gain/importance**, and
**to an organization**. Value is perception, and it's stakeholder-relative.

### Cost

> The monetary cost of the resources used in the delivery of a service.

```text
 ❌ Common trap: cost is not the same as price, and not the same as value.
    Value is perceived benefit. Cost is resource spend.
    A cheap service that nobody uses has low cost and no value.
```

### Outcome

> The effect for a specific stakeholder of a change or continuing to use a
> product or service.

```text
Outcome = the EFFECT FOR A STAKEHOLDER
         = the result in someone's world
         = what actually changed for them
```

### Output

> A tangible or intangible deliverable. In a service context, an output is
> defined as one or more services.

```text
Output = the DELIVERABLE
       = the thing you produce and hand over
       = the service itself
```

### Output vs Outcome — the classic exam pairing

```text
  OUTPUT                          OUTCOME
  ──────                          ───────
  the deliverable                 the effect for a stakeholder
  produced by the org             of that deliverable

  🔧 "The VPN service is            😊 "Support engineers can now
     deployed to 400 staff"          work from home clients without
                                     losing sessions — 40 minutes
   OUTPUT (the service)               saved per session"

                                    OUTCOME (the effect)
```

Rule of thumb: **output is what the provider does, outcome is what the
consumer gets.** ITIL is oriented toward outcomes, because outcomes are where
value lives.

### Utility and warranty (again, in the value context)

They're in both 1.1 and 1.2 because they sit at the heart of value:

```text
Utility  →  the product/service is FIT FOR PURPOSE (does the job)
Warranty  →  it is FIT FOR PURPOSE RELIABLY (and as promised)
Both     →  the foundation of perceived value
```

### Risk

> A continuous, evolving, complex and systemic set of external and internal
> factors that affect the achievement of objectives.

```text
 ⚠️ THE KEY POINT STUDENTS GET WRONG

 Risk is NOT "bad things happening".
 Risk is a SET OF FACTORS — and those factors can be
 POSITIVE, NEGATIVE, or NEUTRAL.

   A new regulation           → threat
   A new, better regulation   → opportunity
   A vendor price increase    → risk
   A vendor price decrease    → opportunity (same factor, sign flips)

 ITIL 4 deliberately widened risk from v3's purely negative
 "risk management" view to this systemic definition.
 Risk management practice covers BOTH threats and opportunities.
```

This is why risk management is a **general** management practice, not a
service management one — it applies to objectives everywhere, not just
service continuity.

### Organization

> An entity with a defined purpose, comprising people, processes and
> resources, arranged to deliver value.

The reminder: an organization (business unit, department) can be a service
**consumer** as well as IT being a service provider. That's the "service
management, not IT service management" widening in ITIL 4.

### The 8 concepts assembled

```text
  value      perceived benefit, gain, importance of using a product/service
    ▲
    │  is delivered when
    │
  utility + warranty
    │        (fit for purpose + assurance)
    │
    │  measured against
    │
  cost       monetary cost of resources used in delivery
    │
    │  weighed alongside
    │
  risk       a set of factors (positive or negative) affecting objectives
    │
  output     the deliverable ──▶ outcome  the effect for a stakeholder
    │
    │  delivered by
    ▼
  organization   people + processes + resources arranged to deliver value
```

---

## 1.3 Service Relationships (BL2 — 1 mark)

### Service relationship

> An arrangement between two or more parties where one provides a service to
> the other.

```text
A service relationship always has:
  1. at least two parties
  2. a provider of a service
  3. a consumer of that service
  4. an arrangement (formal or informal)
```

### Service offering

> A formal agreement between provider and customer for a defined set of
> services.

```text
The FORMAL, agreed part of the relationship.
Defined in the service level agreement (SLA).
It's a subset of what the relationship might actually involve.
```

### Service provision

> Activities performed by the provider as part of the relationship.

```text
Everything the PROVIDER does:
  running the service · support · maintenance · improvements
```

### Service consumption

> Activities performed by the customer or user as part of the relationship.

```text
Everything the CONSUMER does:
  using the service · providing input · feedback · requests
```

### How the four fit together

```text
                  SERVICE RELATIONSHIP
              (the arrangement between parties)
                            │
        ┌───────────────────┼───────────────────┐
        ▼                                       ▼
  SERVICE OFFERING                        (everything else
  (the FORMAL agreement)                  that isn't agreed)
        │
        ▼
  ┌──────────────┐              ┌──────────────────┐
  │   PROVIDER   │              │    CONSUMER      │
  │              │              │                  │
  │  SERVICE     │◄────────────►│   SERVICE        │
  │  PROVISION   │  the         │   CONSUMPTION    │
  │              │  relationship│                  │
  └──────────────┘              └──────────────────┘
```

```text
The "product and service" umbrella sits under all of this:
  service offering + service provision + service consumption
                    │
                    ▼
              products & services
                    │
                    ▼
                  VALUE
```

The key insight: value is created in the **relationship**, not delivered
through the offering. A well-designed offering that nobody consumes produces
nothing. That's the co-creation point again.

---

## Value Types

Worth knowing for LO1 even though the syllabus doesn't list them explicitly —
they show up in scenario questions:

| Type | Whose value? | Example |
|---|---|---|
| **Individual** | One person | An employee saves 2 hrs/week using a new self-service portal |
| **Collective** | A group or organisation | Reduced cost-to-serve across 400 users |
| **Societal** | Wider society | Accessibility improvements for users with disabilities |

```text
Collective value often has INDIVIDUAL value as its source:
  400 people each saving 30 min  →  a collective gain
                                        made of
                                     individual gains
```

---

## Exam Traps to Watch

| Trap | Why students get it wrong | Correct answer |
|---|---|---|
| "Utility and warranty are the same thing" | They sound similar | Utility = fitness for purpose; warranty = assurance it's sustained |
| "The service is the outcome for the user" | Conflating service and outcome | The service is the **means**; the outcome is the **effect** |
| "Risk means threats to the organization" | v3 mindset | Risk is a **set of factors** — positive or negative |
| "The sponsor is the customer" | Both pay-related | Sponsor **authorises, funds, prioritises**; customer **buys and uses** |
| "A service relationship is always a formal contract" | Assuming formal | An **arrangement**; the service *offering* is the formal part |
| "Service management means delivering IT services" | v3 mindset | It's about value for the business, and applies to **all** services |
| "Value is what the provider thinks it is" | Provider-centric | Value is **perceived**, and relative to a **stakeholder** |
| "Output and outcome are interchangeable" | They sound like synonyms | Output = deliverable; outcome = effect for a stakeholder |

### Scenario checks

```text
"Users are billed £30/month and say the service is invaluable"
   → high value, high cost. Cost is not the measure of value.

"A new supplier contract halves cost but response time doubles
 and users complain"  → does the service still deliver value?

"Warranty period expired, so the service has no utility"
   → FALSE. Utility is about fitness for purpose and is independent
     of warranty. They're separate dimensions.

"A pilot scheme is being trialled with 20 users before
 full rollout"  →  progress iteratively with feedback (guiding
                   principle), and incremental value delivery
```

---

## Key Takeaway

> **Value is perceived benefit to a stakeholder, and it's delivered when the
> service has both utility (fitness for purpose) and warranty (assurance that
> it holds as promised) — while output stays distinct from outcome, and risk
> is a set of factors that can help or harm, not just bad luck.**

```text
  UTILITY  +  WARRANTY  =  VALUE (perceived, by a stakeholder)

  OUTPUT  ≠  OUTCOME
   what you deliver    what it did for them

  RISK  =  a set of factors, positive AND negative
  COST  =  resource spend, not value
  SPONSOR ≠ CUSTOMER ≠ USER
```

Next: `Practices.md`
