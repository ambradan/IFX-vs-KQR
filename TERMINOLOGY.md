# Terminology — Fixed Glossary

This glossary defines canonical terms. These definitions are non-negotiable and must be used consistently across all documentation, communications, and implementations.

---

## Primary Terms

### KQR — Knowledge Qualification Regime

A governance framework that defines when outputs produced in non-deterministic environments can be treated as admissible knowledge, and under which constraints.

- **Type:** Governance regime (not a product)
- **Function:** Defines rules, does not execute them
- **Output:** None

### IFX — Inference Forensics Execution

The forensic execution layer that implements KQR rules at runtime via ledger, gate, and signatures.

- **Type:** Enforcement infrastructure
- **Function:** Applies rules, maintains audit trail
- **Output:** SignedOutput, ledger events

---

## Operational Terms

### Admissibility

The property of an output that has passed qualification under KQR rules. Admissibility does not imply truth or correctness.

### SignedOutput

A cryptographically signed artifact containing qualified claims, policy version, and audit references. Carries implicit usage constraints.

### Ledger

Append-only event log. Sole authoritative source of forensic truth. Cannot be modified after write.

### Gate

Deterministic function that evaluates claim admissibility. Pure function with no side effects.

### Policy

Versioned rule set that defines qualification criteria. Authored by system owner. Enforced as written.

### Claim

Atomic unit of content extracted from AI output. Classified by type (FACT, INFERENCE, INSTRUCTION, ASSUMPTION, CODE_ASSERTION).

---

## Boundary Terms

### Consumer

Any application, workflow, or system that uses IFX outputs. Explicitly out of scope for KQR/IFX governance.

### Non-Deterministic Environment

System where identical inputs may produce different outputs (e.g., LLM inference). The subject matter of KQR governance.

### Operational Validity

Property of output that satisfies IFX validity predicate (RunClosed + signature + no supersession). Does not imply epistemic certainty.

---

## Prohibited Terms

The following terms are **forbidden** in all KQR/IFX documentation:

| Forbidden | Reason |
|-----------|--------|
| AI Factory | Implies production, not qualification |
| iFactory | Same as above |
| Factory | Same as above |
| Truth verification | System does not verify truth |
| Decision engine | System does not make decisions |
| Automation | System does not automate |

---

## Usage Rules

1. Terms must be used exactly as defined
2. New terms require formal addition to this glossary
3. Synonyms are not permitted (one term = one concept)
4. Abbreviations must be expanded on first use

---

## Version

Glossary version: 1.0  
Aligned with: IFX Blueprint v1.1.8
