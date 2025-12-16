# Boundaries — Scope and Limitations

## What KQR/IFX Governs

| In Scope | Description |
|----------|-------------|
| Claim classification | Categorizing content by epistemic type |
| Admissibility evaluation | Applying qualification rules |
| Evidence requirements | Enforcing evidence policies |
| Human review triggers | Escalating high-risk content |
| Audit trail | Recording all decisions |
| Output signing | Binding qualified content |

---

## What KQR/IFX Does NOT Govern

| Out of Scope | Rationale |
|--------------|-----------|
| AI model behavior | Models are sources, not governed entities |
| Content generation | IFX qualifies, does not produce |
| Consumer applications | Consumers use outputs, are not governed |
| Business logic | Domain-specific rules belong elsewhere |
| User interfaces | Presentation layer is separate |
| Truth verification | Undecidable in general case |

---

## Explicit Non-Claims

KQR/IFX makes **no claim** regarding:

### Factual Correctness

The system does not verify whether claims are objectively true. A claim may be:
- Admissible (passed qualification)
- Factually incorrect (not verified by system)

These are orthogonal properties.

### AI Safety

The system provides governance infrastructure, not safety guarantees. It does not:
- Prevent harmful content generation
- Detect malicious intent
- Guarantee ethical outputs

### Decision Quality

Human overrides are recorded but not evaluated. A human may:
- Override system decisions incorrectly
- Make poor judgment calls
- Introduce errors

The system traces these decisions. It does not prevent them.

---

## Risk Allocation

| Risk | Bearer | Mitigation |
|------|--------|------------|
| Policy correctness | Policy author | Out-of-band review |
| AI output quality | AI provider | Separate concern |
| Human judgment | Human actor | Audit trail |
| Consumer misuse | Consumer | Usage constraints |
| IFX implementation bugs | IFX operator | Testing, monitoring |

---

## Usage Constraints

SignedOutput carries implicit constraints:

### Permitted

- Decision support input
- Audit evidence
- Same policy_version context
- Downstream processing (with constraints)

### Prohibited

- Sole decision basis
- Verified factual record
- Training data (without re-qualification)
- Cross policy_version transfer

---

## Liability Boundaries

This is infrastructure, not a service. Operators assume responsibility for:

1. **Policy definition** — correctness of rules
2. **Deployment** — proper IFX configuration
3. **Consumer education** — usage constraint enforcement
4. **Monitoring** — anomaly detection

The IFX specification defines *how* the system works, not *whether* a specific deployment is fit for purpose.

---

## Regulatory Positioning

KQR/IFX is designed to **support** regulatory compliance, not **guarantee** it.

| Regulatory Need | KQR/IFX Contribution |
|-----------------|---------------------|
| Audit trail | Complete ledger |
| Traceability | Event linkage |
| Accountability | Actor attribution |
| Documentation | Policy versioning |
| Risk management | Qualification gates |

Compliance determination remains with the regulated entity and their legal counsel.

---

## Summary

> KQR/IFX provides governance infrastructure.
> It does not provide truth, safety, or compliance guarantees.
> It provides traceability, auditability, and defensibility.

The value proposition is **control and accountability**, not **correctness**.
