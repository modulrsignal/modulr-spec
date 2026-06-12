# AdCP Alignment — Modulr Supply Descriptor Contract

---

## What AdCP governs.

AdCP (Ad Context Protocol) governs agent communication, transaction
structure, and the negotiation layer between buyers and sellers.

Modulr does not govern any of these things.

---

## What Modulr contributes.

Modulr generates supply descriptors upstream of the transaction layer.
These descriptors can inform product discovery, signal disclosure,
and inventory evaluation within AdCP-compatible environments.

Modulr descriptors are designed to be mapped into AdCP-compatible
objects. The descriptor contract does not depend on AdCP, but it is
designed to be interoperable with it.

Modulr descriptors remain valid outside of AdCP environments and may
be consumed by systems that do not implement the protocol.

---

## The relationship.

AdCP is a protocol surface.
Modulr is upstream infrastructure.

AdCP governs how agents transact.
Modulr governs what supply looks like before any transaction occurs.

---

## What this document does not claim.

Modulr does not replace AdCP.
Modulr has not been adopted by the AdCP working group.
Modulr descriptors are not AdCP-native objects.

AdCP is an evolving specification. This document reflects alignment
with the current specification and will be updated as the protocol
evolves.

---

## On agent discovery.

The current AdCP adagents.json specification provides vocabulary
for publisher property declarations and sales agent authorization.
It does not currently model non-transactional infrastructure services
or descriptor providers.

Modulr's discovery approach will be defined when the specification
introduces vocabulary appropriate for this role.
