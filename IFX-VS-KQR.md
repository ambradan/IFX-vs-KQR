# IFX vs KQR — Detailed Comparison

## Core Distinction

| Dimension | KQR | IFX |
|-----------|-----|-----|
| **Nature** | Governance regime | Enforcement layer |
| **Type** | Conceptual / normative | Technical / operational |
| **Role** | Defines *what* qualifies as admissible | Applies and traces decisions |
| **Specification** | Abstract rules | Concrete implementation |

---

## Functional Comparison

| Function | KQR | IFX |
|----------|-----|-----|
| Defines admissibility rules | ✓ | — |
| Applies rules at runtime | — | ✓ |
| Produces output | ✗ | ✗ |
| Signs output | — | ✓ |
| Maintains ledger | — | ✓ |
| Provides audit trail | Conceptual | Complete |

---

## Determinism

| Aspect | KQR | IFX |
|--------|-----|-----|
| Rule definitions | Deterministic | — |
| Rule application | — | Deterministic |
| Subject matter (AI outputs) | Non-deterministic | Non-deterministic |

**Clarification:** The *inputs* to the system (AI-generated content) are non-deterministic. The *governance rules* (KQR) and their *application* (IFX) are fully deterministic. This separation is fundamental.

---

## Stakeholder View

| Stakeholder | Primary Interest | Relevant Layer |
|-------------|------------------|----------------|
| Board / Investors | Risk governance | KQR |
| Legal / Compliance | Audit trail | Both |
| Engineering | Implementation | IFX |
| Operations | Runtime behavior | IFX |
| Product | Output consumption | Neither (out of scope) |

---

## Boundary Clarification

| Question | Answer |
|----------|--------|
| Can KQR exist without IFX? | Yes (as abstract governance framework) |
| Can IFX exist without KQR? | No (requires rules to enforce) |
| Does KQR produce anything? | No (defines criteria only) |
| Does IFX produce AI content? | No (qualifies and signs only) |
| Who decides admissibility? | KQR defines rules, IFX applies them |

---

## Common Misconceptions

| Misconception | Reality |
|---------------|---------|
| "KQR is a product" | KQR is a governance category |
| "IFX generates AI outputs" | IFX qualifies outputs, does not generate |
| "They are competing approaches" | They are complementary layers |
| "KQR is optional" | Without KQR, IFX has no rules to enforce |

---

## Integration Model

```
┌─────────────────────────────────────────┐
│           KQR (Governance)              │
│  - Admissibility criteria               │
│  - Policy definitions                   │
│  - Qualification rules                  │
└─────────────────┬───────────────────────┘
                  │ implements
                  ▼
┌─────────────────────────────────────────┐
│           IFX (Enforcement)             │
│  - Ledger (append-only)                 │
│  - Gate (deterministic evaluation)      │
│  - Signatures (forensic binding)        │
│  - RPC (controlled mutations)           │
└─────────────────────────────────────────┘
                  │ produces
                  ▼
┌─────────────────────────────────────────┐
│         SignedOutput (Artifact)         │
│  - Qualified claims                     │
│  - Audit trail reference                │
│  - Usage constraints                    │
└─────────────────────────────────────────┘
```

---

## Summary Statement

> **KQR governs. IFX executes. Neither produces AI.**

This separation ensures that governance logic can evolve independently from enforcement infrastructure, and that both remain isolated from downstream consumers.
