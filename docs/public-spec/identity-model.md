<!-- REPO: Google_MODSSP | PATH: docs/public-spec/identity-model.md -->
<!-- STATUS: §218 Section 3 — 3C approved 2026-06-10 — new file -->
# Identity Model — Modulr Supply Descriptor Contract

This document defines the identity envelope of a Modulr supply descriptor.

Identity fields establish what is being described, who published it,
and when the description was produced. They are not semantic signals.
They are the minimum required context for a descriptor to be
unambiguously addressed and retrieved.

---

## Minimum Identity Envelope

A valid Modulr descriptor must contain all of the following fields.
A descriptor missing any of these fields is incomplete.

| Field | Type | Description |
|---|---|---|
| `descriptor_version` | string | Schema version this descriptor conforms to (e.g. `"0.1"`) |
| `generated_at` | ISO 8601 timestamp | When this descriptor was produced |
| `publisher_id` | string (UUID) | Modulr-assigned publisher identifier |
| `collection_id` | string (UUID) | Modulr-assigned show or series identifier |
| `source_type` | enum | Content format: `podcast` or `fast` |

These five fields are required in every descriptor regardless of
content type, publisher configuration, or signal availability.

---

## descriptor_id

`descriptor_id` is the stable identifier for a descriptor instance.

It is defined in v0 as the intended descriptor-level address — the field
by which downstream systems may cache, reference, or retrieve a specific
descriptor independently of the collection or installment it describes.

`descriptor_id` is not required in v0. It becomes required when the
implementation emits descriptor instances with independent addressability.
It is expected to be required in v0.2 or the first implementation-aligned
schema version.

Downstream systems should not attempt to derive a descriptor-level
identifier from `collection_id` or `installment_id`. Those fields
identify inventory, not descriptor instances.

---

## Extended Identity Fields

The following fields are present in current descriptors and carry
useful identity context, but are not required for a descriptor to be valid.

| Field | Type | Description |
|---|---|---|
| `name` | string | Show or series title, from feed |
| `description` | string | Human-readable show description — context only, not semantic signal |
| `product_type` | string | Inventory classification (current value: `collection`) |

`name` and `description` are human-readable. Per Principle 10, they
provide context for inspection. They are not authoritative semantic surfaces.
Downstream systems must not derive meaning from these fields.

---

## Episode-Level Identity

Modulr descriptors are generated at the episode level.
Per Principle 1, the episode is the unit of truth.

Episode-level identity fields:

| Field | Type | Description |
|---|---|---|
| `installment_id` | string (UUID) | Modulr-assigned episode identifier |
| `episode_title` | string | Episode title, from feed |
| `published_at` | ISO 8601 timestamp | Episode publish date, from feed |

Show-level descriptors are derived views aggregated across episodes.
When operating at show level, `collection_id` identifies the aggregation unit.
Episode-level `installment_id` values are available within
`adcp_installments` on the show-level descriptor.

---

## descriptor_version

`descriptor_version` refers to the schema version this descriptor
conforms to — not a generation run identifier.

Version `"0.1"` is the first specification version of the Modulr
supply descriptor contract.

Descriptors produced before this specification was published do not
carry a `descriptor_version` field. Consumers encountering a descriptor
without this field should treat it as pre-specification.

Version increments follow the governance model defined in Section 10.

---

## What Identity Does Not Include

Identity fields describe the descriptor and its subject.
They do not carry semantic signal.

The following are not identity fields and do not belong in
the identity envelope:

- Signal quality assessments
- Intent classifications
- Topic classifications
- Confidence scores
- Provenance declarations
- Freshness values

These belong in their respective descriptor sections.
