# IFX vs KQR — Governance Infrastructure for Non-Deterministic Systems

> *Organizations will not be judged on whether they used AI. They will be judged on whether they knew what they were doing with its outputs.*

## Canonical Definitions

**Knowledge Qualification Regime (KQR)** is a governance framework that defines when outputs produced in non-deterministic environments (e.g., LLM-generated content) can be treated as admissible knowledge, and under which constraints.

**IFX (Inference Forensics Execution)** is the forensic execution layer that implements KQR rules at runtime, ensuring traceability, auditability, and policy compliance.

---

## Relationship

```
KQR defines the rules.
IFX enforces the rules.
Neither produces AI outputs.
```

| Aspect | KQR | IFX |
|--------|-----|-----|
| Nature | Governance regime | Enforcement layer |
| Function | Defines admissibility criteria | Applies criteria at runtime |
| Output | None (rules only) | SignedOutput, ledger events |
| Determinism | Deterministic (fixed rules) | Deterministic (rule application) |
| Audit | Conceptual framework | Complete forensic trail |

---

## What This Is

- A knowledge qualification and control layer
- A forensic enforcement infrastructure  
- A governance primitive for non-deterministic outputs

## What This Is NOT

- An AI product or service
- A prompt engineering framework
- A development methodology
- An automation or decision engine
- A truth-verification system

---

## Architecture Principle

```
Non-Deterministic Sources          Qualified Outputs
(AI, tools, human input)           (traceable, auditable)
           │                                ▲
           └──────────► IFX ───────────────┘
                         │
                    implements
                         │
                        KQR
                   (governance rules)
```

**Consumers** (applications, workflows, products) are explicitly **out of scope**. They consume IFX outputs but are not governed by this specification.

---

## Why This Architecture

**Risk containment:** Does not promise truth. Does not promise automation. Promises control, audit, and explicit limits.

**Regulatory fit:** Designed for environments where errors are not acceptable — healthcare, public administration, legal, finance, enterprise AI governance.

**Modularity:** IFX can be adopted without exposing KQR internals. KQR can evolve without rewriting IFX. Consumers can change without affecting the regime.

---

## Repository Contents

| File | Purpose |
|------|---------|
| [why-kqr?.md](./WHY-KQR?.md) | Executive rationale |
| [ifx-vs-kqr.md](./IFX-VS-KQR.md) | Detailed comparison |
| [terminology.md](./TERMINOLOGY.md) | Fixed glossary |
| [diagram.md](./DIAGRAM.md) | Architecture explanation |
| [boundaries.md](./BOUNDARIES.md) | Scope and limitations |

---

## Key Statement

> IFX enforces the rules defined by the Knowledge Qualification Regime.  
> KQR defines *what* is admissible knowledge.  
> IFX ensures that this decision is traceable, auditable, and defensible.

**IFX is infrastructure. KQR is governance.**
