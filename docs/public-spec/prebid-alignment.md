# Prebid Alignment — Modulr Supply Descriptor Contract

---

## What Prebid governs.

Prebid governs auction participation, signal activation, and execution
workflows across buyer and seller infrastructure.

Modulr does not govern any of these things.

---

## What Modulr contributes.

Modulr generates supply descriptors before auction participation occurs.

These descriptors may be consumed by systems operating within
Prebid-compatible environments.

Modulr descriptors remain valid outside of Prebid and do not require
Prebid for generation or use.

---

## The relationship.

Prebid is execution infrastructure.
Modulr is supply intelligence infrastructure.

Prebid governs activation.
Modulr governs description.

---

## What this document does not claim.

Modulr is not a bidder.
Modulr is not a seller agent.
Modulr is not a Prebid module.
Modulr has not been adopted by the Prebid project.

This document describes conceptual alignment only.

---

## On future interoperability.

Future integrations may map Modulr descriptors into
Prebid-compatible workflows.

The descriptor contract is intentionally independent
of any specific execution environment.
