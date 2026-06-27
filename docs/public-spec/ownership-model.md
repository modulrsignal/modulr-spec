<!-- REPO: Google_MODSSP | PATH: docs/public-spec/ownership-model.md -->
<!-- STATUS: §218 Section 2 — 3C approved 2026-06-10 — new file -->
# Ownership Model — Modulr Supply Descriptor Contract

This document defines which layer of the agentic advertising stack
owns each category of descriptor signal.

Ownership means system of record at generation time.
A layer that owns a field is the authoritative source for that field's value.
Downstream layers may consume, transform, or transport a field.
They do not redefine its meaning.

---

## The Stack

The agentic advertising stack consists of four layers.
Each layer has a defined scope. No layer's scope extends into another's.

| Layer | Owns | Does Not Own |
|---|---|---|
| **Modulr** | Supply meaning — what inventory is, what it contains, what commercial intent it carries, how confident we are, where that confidence comes from | Pricing, deal terms, activation, execution, signal transport, policy expression |
| **Signal Container** | Signal transport, policy expression, activation metadata | Signal generation, content understanding, descriptor structure, descriptor governance |
| **Seller Agent** | Transaction execution, deal negotiation, campaign lifecycle management | Supply understanding, content classification, descriptor generation |
| **Buyer Agent** | Planning, evaluation, decisioning | Supply description, signal generation |

---

## Modulr's Ownership Claim

Modulr owns the supply understanding layer.

Specifically, Modulr is the system of record for:

**Identity**
Publisher identity, show identity, episode identity, descriptor version,
and generation timestamp. These fields establish what is being described
and when the description was produced.

**Provenance**
The origin of every signal — whether derived deterministically from content,
generated with model assistance, or produced under degraded conditions.
Provenance is not optional. A descriptor without provenance declarations
is not a Modulr descriptor.

**Content Classification**
What the content is about, expressed as structured topic signals using
a defined taxonomy. Topic classification is distinct from intent classification
and must not be conflated with it.

**Intent Signals**
what commercial reasoning objectives the supply can support, expressed using the Modulr intent taxonomy
Intent is not a topic. Intent is not a sentiment. Intent is a structured
assessment of the types of commercial objectives this content may be
relevant to, expressed using the Modulr intent taxonomy.

**Suitability**
Brand safety tier and distribution across the episode set.
Suitability is generated from content analysis, not from publisher
declaration. The canonical read-time values are standard, caution,
and restricted.

**Confidence**
The degree of certainty in descriptor-level classifications.
Confidence is a composite derived from per-signal generation confidence.
Confidence must always be interpreted alongside provenance status —
a high-confidence value on a degraded descriptor carries different
weight than the same value on a complete descriptor.

**Freshness**
The elapsed time between the latest signal generation and the point
of descriptor consumption. Freshness is derived from the most recent
signal generated_at timestamp. It is not derived from content publish
date and is not a publisher declaration.

---

## What Modulr Does Not Own

The following categories are outside Modulr's scope permanently.
They are not deferred. They are not roadmap items.
They are architectural boundaries enforced at the specification level.

**Pricing and deal terms**
No Modulr descriptor field contains a price, floor, rate, or deal structure.
These belong to the execution layer.

**Activation**
No Modulr descriptor field instructs a downstream system to take action.
Descriptors are evidence. Activation decisions belong to buyer agents
and execution platforms.

**Signal transport and policy expression**
How signals travel between systems and what policy governs their use
in transit — these belong to signal container infrastructure.
Descriptor governance — how the descriptor contract itself evolves —
belongs to Modulr.

**Audience identity**
Modulr descriptors describe supply, not audiences.
No user identity, device graph, or behavioral signal is part of
the descriptor contract.

**Selection decisions**
Descriptors do not make selection decisions.
They do not instruct downstream systems which inventory to purchase,
activate, or prioritize. Decision-making belongs to the systems
consuming the descriptor.

---

## Shared Surfaces

Some fields have implementation presence in multiple layers.
In these cases, Modulr's value is authoritative at generation time.

**Publisher identity**
Modulr carries publisher identity in the descriptor.
Seller agents carry tenant identity in their own systems.
These are parallel representations of the same underlying entity.
Modulr's descriptor value is authoritative for the descriptor.
The seller agent's tenant model is authoritative for execution.

**Content categories**
Modulr carries topic classifications as structured signals.
Seller agents may carry content categories in product objects.
Where both are present, Modulr's structured signal is the more
precise and provenance-declared representation.

---

## Field Ownership Reference

The following table defines ownership verdicts for the fields present
in the current Modulr descriptor implementation. This table governs
§218 schema design decisions.

| Field Group | Fields | Ownership | Notes |
|---|---|---|---|
| Identity | descriptor_id | Modulr (defined, deferred) | Defined in v0 as descriptor-level address. Not required until implementation emits independently addressable instances. See identity-model.md. |
| Identity | collection_id, publisher_id, source_type, name | Modulr | Credibly owned — canonical show-level identity fields per identity-model.md. source_type values: podcast or fast (FAST: Free Ad-Supported Streaming Television). |
| Identity | description | Modulr (label only) | Human-readable context, not semantic signal — Principle 10 |
| Provenance | provenance_status, model_version, input_type, quality_signal_count, total_signal_count | Modulr | Credibly owned. Two model identifiers coexist — show-level is descriptor-facing |
| Freshness | signal_age_days | Modulr | Derived from latest signal generated_at — not content publish date |
| Content classification | topics[].id (IAB) | Modulr | Episode-level. Distinct from intent — Principle 7 |
| Entities | entities[] | Modulr | Canonical at episode granularity. Show-level aggregation undefined in v0 |
| Intent signals | intent_signals[].class (VALID_INTENT_CLASSES) | Modulr | Commercial consideration state. Taxonomy-filtered at write and read |
| Suitability | brand_safety_tier, brand_safety.distribution | Modulr | Canonical values: standard / caution / restricted |
| Confidence | descriptor_confidence | Modulr | Canonical descriptor-level confidence surface. Aggregate across quality signals. |
| Confidence | signal_confidence | Modulr | Per-signal brand safety certainty. Supporting evidence |
| Confidence | classification_confidence | Modulr | Per-category IAB certainty. Episode-level supporting evidence |
| Derived scoring | readiness_score, intent_stage | ⚠ Deferred | Commercial scoring artifact. Deferred — not part of the v0 canonical descriptor. |
| Execution | activation, pricing_options | Not Modulr | Deprecated from canonical descriptor. Execution layer |
| Tone | tone | Not Modulr at show level | Last-signal-only. Cannot credibly aggregate. Episode-level only if surfaced |

---

## Principle 9 Applied

> A field whose ownership is ambiguous does not belong in the canonical
> descriptor until ownership is resolved.

The ⚠ deferred fields above — readiness_score and intent_stage — remain
in the implementation but are not part of the v0 canonical descriptor
specification. Their status will be resolved during the confidence model
specification work.

The deprecated fields — activation and pricing_options — are removed
from the canonical descriptor permanently. They may remain in the
implementation for Phase 1 compatibility reasons, but they do not
represent Modulr's layer and will not appear in the public contract.
