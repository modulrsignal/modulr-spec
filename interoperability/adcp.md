# AdCP

## What AdCP owns

AdCP (Ad Context Protocol) is a protocol for structured communication between advertising system components. It defines message formats, agent roles, and interaction patterns for programmatic advertising infrastructure.

## Where Modulr fits

Modulr supply descriptors are designed to be mapped into AdCP-compatible objects. Modulr descriptors are protocol-agnostic — their semantic meaning is preserved when transported through AdCP-compatible systems.

Modulr is not an AdCP participant in the transactional sense. Modulr does not bid, negotiate, or execute. Modulr generates the pre-bid supply intelligence that AdCP-compatible systems can consume.

The descriptor is upstream of AdCP interactions. It provides the supply context against which AdCP governance and context queries operate.

## What crosses the boundary

Supply descriptor fields — topics, intent signals, suitability tier, confidence, provenance status — map to AdCP context object fields.

The mapping is performed by the consuming system. Modulr does not prescribe how downstream systems use descriptor fields within their AdCP implementations.
