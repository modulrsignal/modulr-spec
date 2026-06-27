# Why Descriptors?

Supply descriptors are not metadata.

This distinction matters because metadata and descriptors serve different purposes, carry different trust properties, and answer different questions for downstream systems.

---

## The Difference

| Dimension       | Metadata                        | Supply Descriptor                        |
|-----------------|---------------------------------|------------------------------------------|
| Origin          | Publisher declared              | Machine generated from content evidence  |
| Describes       | Labels and categories           | Meaning and capability                   |
| Oriented toward | Human readers                   | Autonomous systems                        |
| Structure       | Static                          | Versioned and evidence-bound             |
| Unit            | Category                        | Capability                               |
| Claim type      | Context assertion               | Evidenced claim with provenance          |

---

## What Metadata Answers

> What did the publisher say this content is?

Metadata tells you a publisher labeled content as "Personal Finance" or "Technology." It tells you the title, the description, the RSS category.

These are useful signals. But they are publisher assertions. They are not verified. They are not evidence-bound. They do not tell an autonomous system what it can accomplish using this supply.

---

## What a Supply Descriptor Answers

> What can a machine reason about using this supply?

A supply descriptor answers:

- What subjects does this content cover? (topics)
- What commercial reasoning objectives does this supply structurally support? (intent signals)
- How suitable is this supply for a given adjacency? (suitability)
- How confident is the descriptor in each claim? (confidence)
- Where did each signal originate? (provenance)
- Who is the authoritative owner of each field? (ownership)

Every claim in a descriptor has an owner, a provenance, and a confidence value. Downstream systems know exactly what kind of claim they are reading — whether it was asserted by the publisher, observed from content, or derived from multiple signals.

---

## Why This Matters for Autonomous Systems

A buyer agent operating programmatically cannot evaluate publisher self-description alone. Self-description is unverified, inconsistently structured, and optimized for human readers.

A supply descriptor provides machine-readable evidence with explicit lineage. It does not replace execution-layer signals. It does not bid, negotiate, or transact. It describes what supply is — in a form that autonomous systems can reason against before any transaction occurs.

---

## The Trust Architecture

Modulr descriptors are organized around four foundational questions:

- **Identity** — What is being described?
- **Ownership** — Who is authoritative for this field?
- **Provenance** — What evidence produced this signal?
- **Confidence** — How strongly is the claim supported?

Together, these make a descriptor a trustworthy artifact — not just a formatted label.

See `docs/public-spec/ownership-model.md`, `docs/public-spec/provenance-model.md`, and `docs/public-spec/confidence-model.md`.
