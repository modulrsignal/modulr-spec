# modulr-spec

Modulr Supply Descriptor Contract

---

Modulr defines how advertising supply is understood before execution.

The Modulr Supply Descriptor Contract is a machine-readable specification
for describing advertising inventory, content context, commercial reasoning capability,
suitability, provenance, and confidence in a protocol-neutral format.

---

## Why It Exists

Execution layers have standardized faster than intelligence layers.

Advertising systems can transact inventory, but they often lack a
consistent way to understand what that inventory contains, what it may
be relevant to, and how trustworthy those signals are.

The Supply Descriptor Contract exists to provide a stable,
machine-readable representation of supply before any transaction occurs.

---

## Architectural Position

```
Publisher Content
↓
Supply Descriptor ← this specification
↓
Signal Container
↓
Seller Agent
↓
Buyer Agent
↓
Execution
```

The supply descriptor is upstream of all transaction logic.
It describes inventory. It does not price, negotiate, activate, or execute.

---

## What This Specification Covers

- **Identity** — how a descriptor instance is addressed and versioned
- **Provenance** — origin declaration for every signal
- **Topics** — structured content classification using a defined taxonomy
- **Intent Signals** — commercial consideration state the content may carry
- **Suitability** — brand safety tier derived from content analysis
- **Confidence** — degree of certainty in descriptor-level classifications
- **Freshness** — elapsed time between signal generation and consumption

---

## What This Specification Does Not Cover

- Pricing or deal terms
- Negotiation or activation
- Audience identity or behavioral signals
- Ranking, selection, or purchasing decisions
- Execution, bidding, or campaign management

These belong to execution-layer infrastructure.
See `docs/public-spec/ownership-model.md` for the full layer boundary definition.

---

## Specification Documents

**Start here:**
- [`docs/public-spec/ECOSYSTEM_PLACEMENT.md`](docs/public-spec/ECOSYSTEM_PLACEMENT.md) — supply intelligence chain and ecosystem placement
- [`docs/public-spec/non-goals.md`](docs/public-spec/non-goals.md)
- [`docs/public-spec/descriptor-principles.md`](docs/public-spec/descriptor-principles.md)

**Ownership and identity:**
- [`docs/public-spec/ownership-model.md`](docs/public-spec/ownership-model.md)
- [`docs/public-spec/identity-model.md`](docs/public-spec/identity-model.md)

**Evidence and certainty:**
- [`docs/public-spec/provenance-model.md`](docs/public-spec/provenance-model.md)
- [`docs/public-spec/confidence-model.md`](docs/public-spec/confidence-model.md)

**Protocol alignment:**
- [`docs/public-spec/adcp-alignment.md`](docs/public-spec/adcp-alignment.md)
- [`docs/public-spec/prebid-alignment.md`](docs/public-spec/prebid-alignment.md)

**Schema definitions and example payloads:**
Coming in the first public schema release.

---

## Core Position

Modulr emits supply descriptors.
Downstream systems decide how to use them.

Modulr does not bid, negotiate, price, transact, or execute media buys.

Publisher-native. Protocol-ready. Neutral by design.

---

## Status

**Version:** Draft — foundational specification in progress  
**Schema:** Not yet published  
**Public review:** Early visibility; formal review begins after completion of the foundational specification packet

The specification is under active development.

Complete:
- Descriptor Principles
- Ownership Model
- Identity Model
- Provenance Model
- Confidence Model

In progress:
- Intent Signals
- Suitability
- Governance

---

## Governance

Governance documentation will be published with the first public schema release.

For contribution guidelines, see [`docs/public-spec/CONTRIBUTING.md`](docs/public-spec/CONTRIBUTING.md).

---

https://modulrsignal.com
