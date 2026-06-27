# Intent Signal Model

## Purpose

Intent signals describe the commercial reasoning capabilities a unit of supply structurally affords to an autonomous system.

They do not describe what content is about.

They do not describe audience psychology.

They do not infer user intent.

They describe what a machine can accomplish using this supply as context for commercial reasoning.

---

## The Governing Question

> What is this supply fundamentally organized to help an autonomous system reason about?

This is distinct from:

- What subject matter does this content cover? (answered by topics)
- Who is the likely audience? (not answered by this specification)
- What is the content's commercial value? (not answered by this specification)

---

## Relationship to Topics

Topics and intent signals are separate signal types. They must not be treated as interchangeable.

A topic describes subject matter.

An intent signal describes capability.

A personal finance episode is not necessarily organized to support a financial decision. A travel episode may be organized to support a purchasing decision even when travel is incidental to the episode's structure.

Topic proximity does not imply commercial capability.

---

## Assignment Rules

Intent signals are assigned only when the corresponding capability is the dominant organizing characteristic of the supply.

Three assignment rules apply:

**Dominance required.** A capability must be the organizing structure of the supply — not simply something that occurs within it. Incidental, conversational, or illustrative reasoning does not qualify.

**Sparse assignment preferred.** Most supply correctly produces zero or one intent signal. An empty signal array is an accurate result, not a failure.

**Conservative assignment when evidence is insufficient.** The specification favors under-assignment over over-assignment. An absent signal is accurate. An incorrect signal misleads downstream systems.

---

## The Six Primitives

See `docs/public-spec/intent-taxonomy.md` for the complete primitive definitions.

---

## Provenance

Intent signals are machine-generated from content evidence.

They are not publisher-asserted.

They are not audience-derived.

They are Modulr-owned fields, generated under the Modulr descriptor contract.

See `docs/public-spec/ownership-model.md` and `docs/public-spec/provenance-model.md` for field ownership and evidence lineage.

---

## Confidence

Each assigned intent signal carries a confidence value.

Confidence reflects the strength of observable evidence for the assignment.

It does not reflect activation suitability.

It does not direct downstream systems to act or not act.

Downstream systems determine how to interpret confidence in their own execution context.

See `docs/public-spec/confidence-model.md`.

---

## Specification Boundary

This document defines what an intent signal means.

It does not define how intent signals are generated.

The generation methodology is an internal implementation asset. It may evolve without changing this specification.
