# Architecture Diagram

## Conceptual Model

```
┌─────────────────────────────────────────────────────────────────┐
│                    NON-DETERMINISTIC SOURCES                    │
│                                                                 │
│    ┌──────────┐    ┌──────────┐    ┌──────────┐                │
│    │   LLM    │    │  Tools   │    │  Human   │                │
│    │ Outputs  │    │ Results  │    │  Input   │                │
│    └────┬─────┘    └────┬─────┘    └────┬─────┘                │
│         │               │               │                       │
│         └───────────────┼───────────────┘                       │
│                         │                                       │
│                         ▼                                       │
└─────────────────────────┼───────────────────────────────────────┘
                          │
                          │ unqualified input
                          │
┌─────────────────────────┼───────────────────────────────────────┐
│                         ▼                                       │
│  ┌─────────────────────────────────────────────────────────┐   │
│  │                    IFX LAYER                             │   │
│  │                                                          │   │
│  │   ┌────────────┐  ┌────────────┐  ┌────────────┐        │   │
│  │   │   Ledger   │  │    Gate    │  │ Signatures │        │   │
│  │   │ (forensic) │  │  (rules)   │  │  (binding) │        │   │
│  │   └────────────┘  └────────────┘  └────────────┘        │   │
│  │                                                          │   │
│  │          implements rules defined by KQR                 │   │
│  │                         │                                │   │
│  └─────────────────────────┼────────────────────────────────┘   │
│                            │                                    │
│            ┌───────────────┴───────────────┐                   │
│            ▼                               ▼                    │
│    ┌──────────────┐               ┌──────────────┐             │
│    │ SignedOutput │               │    Ledger    │             │
│    │  (qualified) │               │   Events     │             │
│    └──────────────┘               └──────────────┘             │
│                                                                 │
│                    KQR GOVERNANCE SCOPE                         │
└─────────────────────────────────────────────────────────────────┘
                          │
                          │ qualified output
                          │ (with constraints)
                          │
┌─────────────────────────┼───────────────────────────────────────┐
│                         ▼                                       │
│                    CONSUMERS                                    │
│              (explicitly out of scope)                          │
│                                                                 │
│    ┌──────────┐    ┌──────────┐    ┌──────────┐                │
│    │   Apps   │    │Workflows │    │ Products │                │
│    └──────────┘    └──────────┘    └──────────┘                │
│                                                                 │
└─────────────────────────────────────────────────────────────────┘
```

---

## Layer Explanation

### Non-Deterministic Sources

Systems that produce outputs which may vary given identical inputs. These are the **subjects** of KQR governance, not part of it.

- LLM inference
- Tool execution with external dependencies
- Human judgment and input

### IFX Layer

The enforcement infrastructure that applies KQR rules:

| Component | Function |
|-----------|----------|
| **Ledger** | Append-only forensic record of all events |
| **Gate** | Deterministic evaluation of admissibility |
| **Signatures** | Cryptographic binding of qualified output |

IFX does not generate content. It qualifies and traces content produced elsewhere.

### KQR Governance Scope

The boundary within which qualification rules apply. Everything inside this boundary is governed by KQR policies. Everything outside (sources and consumers) is explicitly excluded.

### Consumers

Applications and systems that use IFX outputs. They are:

- **Not governed** by KQR/IFX
- **Not responsible** for qualification decisions
- **Required** to respect usage constraints in SignedOutput

---

## Data Flow

```
1. Unqualified content enters IFX
2. Claims are extracted and classified
3. Gate evaluates each claim against KQR rules
4. Decisions are recorded in ledger
5. Qualified output is signed
6. SignedOutput exits to consumers
```

At no point does IFX:
- Generate content
- Make autonomous decisions
- Verify truth
- Replace human judgment

---

## Boundary Enforcement

The diagram intentionally shows clear boundaries:

| Boundary | Meaning |
|----------|---------|
| Sources → IFX | Unqualified input crosses into governance scope |
| IFX → Consumers | Qualified output exits with constraints |
| KQR scope box | Everything inside is governed; everything outside is not |

This separation is **critical for risk containment**. Failures in sources or consumers do not compromise the qualification regime.
