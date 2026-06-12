<!-- REPO: Google_MODSSP | PATH: docs/public-spec/confidence-model.md -->
<!-- STATUS: §218 Section 9 — 3C approved 2026-06-11 — new file -->
# Confidence Model — Modulr Supply Descriptor Contract

This document defines the confidence model for the Modulr Supply Descriptor Contract.

---

## Purpose

Confidence establishes the certainty associated with descriptor claims.

A descriptor does not only state what signals it contains. It also states how
certain those claims are, at what scope those certainty claims apply, and within
what provenance context those certainty claims must be interpreted.

Confidence is not an independent signal. Confidence is an interpretation of
evidence. Every confidence value must be evaluated within a declared provenance
context.

Confidence describes certainty within an evidence chain. It does not describe
commercial value, activation suitability, or downstream utility.

---

## Confidence Surfaces

Modulr descriptors expose three confidence surfaces.

Each surface answers a distinct certainty question. They are not interchangeable.

### signal_confidence

Certainty in a generated signal family for a specific content item.

`signal_confidence` answers: how certain is Modulr that this signal was correctly
generated for this content item?

### classification_confidence

Certainty that a specific classification applies to a specific content item.

`classification_confidence` answers: how certain is Modulr that this classification
correctly describes this content item?

### descriptor_confidence

Confidence in the descriptor-level summary derived from quality signals.

`descriptor_confidence` answers: how certain is Modulr in the aggregate descriptor
representation produced from the available evidence?

`descriptor_confidence` is the canonical descriptor-level confidence surface. It
is a composite derived from quality signals. It is not a substitute for
episode-level confidence and does not supersede the certainty associated with
underlying content items from which the descriptor was derived.

---

## Confidence Scope

Every confidence value has a scope. Scope defines the nature of the claim
being made.

Confidence scope is not defined by object type. It is defined by claim scope.

### Evidence Scope

Confidence attached to a specific content item.

A confidence value with evidence scope describes certainty about a particular
piece of content. Today this corresponds to episode-level signals. As Modulr's
descriptor architecture expands to cover additional content structures — segments,
clips, chapters, articles — evidence scope applies to any specific content item
at the granularity of generation.

### Descriptor Scope

Confidence attached to an aggregate representation derived from underlying
content items.

A confidence value with descriptor scope describes certainty about the descriptor
summary, not about every underlying content item individually. Today this
corresponds to show-level descriptors. The same scope applies to any aggregate
descriptor derived from a set of underlying content items.

These are different claims. A downstream system interpreting a confidence value
must know its scope before interpreting its meaning.

---

## Confidence Hierarchy

The three confidence surfaces form a hierarchy.

`signal_confidence` and `classification_confidence` are evidence-scope surfaces.
They are generated at content-item granularity and reflect certainty about
specific signals and classifications on specific content.

`descriptor_confidence` is a descriptor-scope surface. It is derived from
evidence-scope signals. It reflects certainty in the aggregate representation.

The hierarchy runs one way. Descriptor confidence is derived from evidence-scope
signals. Evidence-scope signals are not derived from descriptor confidence.

---

## Provenance and Confidence

Provenance is required for confidence interpretation.

A confidence value may exist without provenance as a number. A Modulr confidence
value is meaningful only within a declared provenance context.

The same confidence value carries different interpretive weight depending on
provenance status. A `descriptor_confidence` of 0.88 on a complete descriptor
and a `descriptor_confidence` of 0.88 on a degraded descriptor are not equivalent
claims. The number is the same. The evidence chain behind it is not.

Descriptor confidence must be interpreted alongside provenance status, descriptor
completeness, and confidence scope.

Descriptor completeness is defined in Section 4 — `provenance-model.md`.

Without provenance status, completeness, and scope, a confidence value cannot
be correctly interpreted. It is a number, not a claim.

---

## Descriptor Confidence Doctrine

`descriptor_confidence` reflects confidence in the descriptor-level representation
of supply.

It does not reflect confidence in every underlying content item.
It does not predict episode-level truth.
It does not predict campaign performance.
It does not imply activation suitability.

A descriptor consumer that requires episode-level certainty must access
episode-level signals.

The show descriptor is a discovery object. The episode is the evidence object.
Descriptor confidence describes the summary. Episode-level confidence describes
the truth.

---

## Deferred Surfaces

The following fields are present in the current Modulr implementation but are
not part of the v0 canonical confidence model.

### readiness_score

`readiness_score` is not a confidence surface. It is a conclusion derived
from evidence.

Once a downstream system has access to `descriptor_confidence`, confidence scope,
provenance status, and descriptor completeness, it possesses the evidence
necessary to form its own conclusion about inventory readiness. A readiness score
collapses that evidence into a single output and removes interpretive agency from
the downstream system.

A confidence surface describes certainty. A readiness score describes a
conclusion. Conclusions belong to the systems consuming the descriptor.

`readiness_score` is deferred. It is not part of the v0 canonical descriptor
specification.

### intent_stage

`intent_stage` describes a stage in a decisioning progression. Its fate is
linked to the `readiness_score` verdict.

For the same reason — it answers what should happen next rather than what is
known and how certain we are — `intent_stage` is deferred. It is not part of
the v0 canonical descriptor specification.

---

## Cross-Reference

The provenance model is defined in Section 4 — `provenance-model.md`.

Confidence values must be evaluated within the provenance context established
there. Section 4 and Section 9 are a paired specification. Neither is complete
without the other.
