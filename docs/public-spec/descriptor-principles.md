<!-- REPO: Google_MODSSP | PATH: docs/public-spec/descriptor-principles.md -->
<!-- STATUS: §218 Section 1 — approved by 3C 2026-06-10 — supersedes §216 version -->
# Descriptor Principles — Modulr Supply Descriptor Contract

These principles govern how Modulr supply descriptors are structured,
what they contain, and what they are designed to do.

All specification decisions in §218 are tested against these principles.
A field that contradicts a principle does not belong in the canonical descriptor.

---

## 1. Episode is the unit of truth.

Supply descriptors are generated at the episode level.
Show-level descriptors are derived views, not independent sources of truth.
Any aggregation above episode granularity must preserve the provenance
of the underlying episode-level signals.

## 2. Determinism before enrichment.

Signals derived directly from content are separated from model-assisted
enrichment. Provenance is declared at the field level, not only at the
descriptor level. Buyers can filter by signal origin if precision
requirements demand it.

## 3. Neutrality is structural, not positional.

Modulr descriptors do not contain pricing, deal terms, negotiation state,
activation rules, delivery constraints, or bidding behavior.
They are emitted once and consumed by downstream systems.
The descriptor contract is upstream of all transaction logic.
Neutrality is enforced by what the descriptor does not contain.

See ownership-model.md for layer boundary definitions.

## 4. The contract is stable.

Implementations may evolve over time.
The purpose of the descriptor contract is to provide a stable,
machine-readable representation of supply that can be consumed
across systems without requiring knowledge of the implementation.

## 5. Interoperability over lock-in.

Descriptors are defined independent of protocol, then mapped to protocols.
No protocol dependency is assumed at the field level.
Descriptors are designed to be consumed across AdCP, OpenRTB, Prebid,
and future agentic environments.

## 6. Provenance is required.

Every signal carries an origin declaration.
Provenance is declared per signal and at descriptor level.
Deterministic signals and model-assisted signals are not interchangeable.
Consumers may not assume provenance — it must be stated.

## 7. Intent and topic are distinct signals.

A descriptor describes what content discusses (topic) and separately
describes the types of commercial objectives the content may be relevant
to (intent). These signals serve different purposes and must not be
treated as interchangeable.

Collapsing intent and topic into a single surface is a specification error.

## 8. Descriptors are evidence, not decisions.

Descriptors exist to increase supply visibility and understanding.
They do not instruct downstream systems how to rank, select,
purchase, or activate inventory.

Decision-making remains the responsibility of buyers,
agents, and execution platforms.

## 9. Ownership is declared, not inferred.

Every field in a descriptor has exactly one system of record.
Field ownership is declared explicitly in the specification.
Consumers must not infer which layer generated a field from its
position in the response or its name alone.

A field whose ownership is ambiguous does not belong in the
canonical descriptor until ownership is resolved.

## 10. Human-readable fields provide context. Structured fields provide meaning.

Descriptor meaning is carried by structured fields such as intent signals,
topics, suitability, provenance, and confidence.

Human-readable text fields are provided for context and inspection,
but are not authoritative semantic surfaces.

A consumer that derives meaning from a text description field rather
than from structured fields is consuming the descriptor incorrectly.
