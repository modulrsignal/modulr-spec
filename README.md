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

## Descriptor Architecture

```
                    Supply Descriptor

                          │

           ┌──────────────┼──────────────┐

           │              │              │

       Identity       Semantics        Trust

                          │

               Topics · Intent Signals

                          │

          Ownership · Provenance · Confidence
```

Identity answers: what is being described.
Semantics answers: what the supply means and what it enables.
Trust answers: who asserts it, where it came from, and how certain it is.

---

## What This Specification Covers

- **Identity** — how a descriptor instance is addressed and versioned
- **Provenance** — origin declaration for every signal
- **Topics** — structured content classification using a defined taxonomy
- **Intent Signals** — commercial reasoning capabilities the supply structurally affords to autonomous systems
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
- [`docs/public-spec/why-descriptors.md`](docs/public-spec/why-descriptors.md) — why supply descriptors differ from metadata

**Ownership and identity:**
- [`docs/public-spec/ownership-model.md`](docs/public-spec/ownership-model.md)
- [`docs/public-spec/identity-model.md`](docs/public-spec/identity-model.md)

**Evidence and certainty:**
- [`docs/public-spec/provenance-model.md`](docs/public-spec/provenance-model.md)
- [`docs/public-spec/confidence-model.md`](docs/public-spec/confidence-model.md)

**Intent signals:**

- [`docs/public-spec/intent-signal-model.md`](docs/public-spec/intent-signal-model.md)
- [`docs/public-spec/intent-taxonomy.md`](docs/public-spec/intent-taxonomy.md)

**Protocol alignment:**
- [`docs/public-spec/adcp-alignment.md`](docs/public-spec/adcp-alignment.md)
- [`docs/public-spec/prebid-alignment.md`](docs/public-spec/prebid-alignment.md)

**Interoperability:**

- [`interoperability/README.md`](interoperability/README.md)
- [`interoperability/adcp.md`](interoperability/adcp.md)
- [`interoperability/prebid.md`](interoperability/prebid.md)
- [`interoperability/seller-agent.md`](interoperability/seller-agent.md)
- [`interoperability/buyer-agent.md`](interoperability/buyer-agent.md)

**Examples:**

- [`examples/podcast-episode-descriptor.v0.1.json`](examples/podcast-episode-descriptor.v0.1.json)
- [`examples/streaming-video-descriptor.v0.1.json`](examples/streaming-video-descriptor.v0.1.json) *(illustrative — not current production coverage)*

---

## Core Position

Modulr emits supply descriptors.
Downstream systems decide how to use them.

Modulr does not bid, negotiate, price, transact, or execute media buys.

Publisher-native. Protocol-ready. Neutral by design.

---

## Status

**Version:** Draft — Public Specification v1 in progress
**Schema:** Draft schema coming in the first public schema release
**Public review:** Early visibility; formal review begins after completion of the foundational specification packet

---

**Complete:**

- Descriptor Principles
- Ownership Model
- Identity Model
- Provenance Model
- Confidence Model
- Ecosystem Placement
- Intent Signal Model
- Intent Taxonomy
- Why Descriptors

**In progress:**

- Suitability Model
- Governance Model
- JSON Schema

---

**Illustrative examples available in `/examples`.**

---

## Governance

Governance documentation will be published with the first public schema release.

For contribution guidelines, see [`docs/public-spec/CONTRIBUTING.md`](docs/public-spec/CONTRIBUTING.md).

---

https://modulrsignal.com
