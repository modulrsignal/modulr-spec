<!-- REPO: Google_MODSSP | PATH: docs/public-spec/provenance-model.md -->
<!-- STATUS: §218 Section 4 — 3C approved 2026-06-11 — new file -->
# Provenance Model — Modulr Supply Descriptor Contract

This document defines the provenance requirements for the Modulr Supply Descriptor Contract.

---

## Purpose

Provenance establishes the evidence chain behind a descriptor.

A descriptor is not defined solely by the signals it contains. It is also defined
by the origin of those signals, the methods used to generate them, the completeness
of the inputs available at generation time, and the lineage through which the
descriptor was produced.

Provenance exists to make descriptor claims traceable, auditable, and interpretable.
A signal without provenance is an assertion. A signal with provenance is evidence.

Every canonical Modulr descriptor MUST include a provenance declaration.

---

## Provenance Declaration

A provenance declaration answers four questions.

### Origin

Where did the information originate?

A descriptor MUST identify the source category and source type used to generate
its signals.

The specification defines the requirement to declare origin. It does not define
or enumerate all possible source types. Source enumerations are implementation
concerns and may evolve as new media formats, content types, and ingestion methods
emerge.

### Method

How was the information produced?

A descriptor MUST declare the method by which a signal was generated.

Canonical methods are:

- `deterministic`
- `model_assisted`
- `publisher_declared`

These methods describe the generation process. They do not imply signal quality,
confidence, or commercial value.

### Completeness

What information was available at generation time?

A descriptor MUST declare the completeness of the evidence available during
signal generation.

Completeness is represented through:

- quality signal counts
- total signal counts
- degradation indicators
- provenance status

Completeness describes evidence availability. It does not describe descriptor
usefulness or downstream applicability.

### Lineage

When and through what generation chain was the descriptor produced?

A descriptor MUST provide lineage sufficient to determine:

- when signals were generated
- when the descriptor was produced
- which descriptor version produced the output

Lineage exists to support traceability and auditability across descriptor revisions.

---

## Provenance Metadata

Additional provenance metadata may be attached to a descriptor.

Examples include:

- model identifiers
- implementation-specific generation metadata
- processing environment information

Such metadata may support operational analysis and debugging but does not replace
the required provenance declaration.

The descriptor contract recognizes a single authoritative descriptor-facing
`model_version` value. Additional model identifiers are implementation details
and are not part of the canonical descriptor contract.

---

## Provenance Status

Every descriptor MUST declare a provenance status.

Canonical provenance states are:

- `complete`
- `partial`
- `degraded`
- `unknown`

These states describe the completeness and reliability of the evidence chain
available during descriptor generation.

They do not describe confidence, suitability, quality, performance, or
commercial value.

### Complete

All required inputs were available and successfully processed.

### Partial

Some expected inputs were unavailable or incomplete, but sufficient evidence
existed to generate the descriptor.

### Degraded

Significant portions of the expected evidence chain were unavailable, incomplete,
or failed during generation.

A degraded descriptor remains valid. Its evidence chain is reduced.

### Unknown

The completeness of the evidence chain cannot be determined.

`unknown` should be treated as an exceptional condition and not as a normal
operating state.

---

## Provenance Interpretation Contract

Provenance provides context for interpreting descriptor claims.

Downstream systems MAY use provenance declarations to:

- evaluate evidence quality
- assess trustworthiness
- interpret confidence surfaces
- apply their own weighting methodologies

Downstream systems MUST NOT treat provenance as an activation signal.

Provenance declarations do not instruct a downstream system to:

- purchase inventory
- reject inventory
- prioritize inventory
- deprioritize inventory
- activate campaigns
- suppress campaigns

Such decisions belong to the systems consuming the descriptor.

---

## Provenance and Confidence

Provenance and confidence are related but distinct concepts.

Provenance describes the evidence chain.

Confidence describes certainty within that evidence chain.

A confidence value without provenance may exist as a score. A Modulr confidence
value is meaningful only within a declared provenance context.

The confidence model is defined in Section 9 — `confidence-model.md`.
