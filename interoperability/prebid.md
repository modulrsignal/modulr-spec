# Prebid

## What Prebid owns

Prebid is an open-source framework for header bidding. It manages auction execution, bid requests, and demand-side coordination for publishers operating programmatic inventory.

## Where Modulr fits

Modulr descriptors are designed to be consumed by systems operating within Prebid-based environments. Modulr is designed to complement existing Prebid workflows rather than replace them.

Modulr does not participate in Prebid auctions. Modulr does not bid. Modulr does not modify bid requests or auction outcomes.

Modulr supply descriptors can be made available to Prebid-adjacent components — including real-time data modules — as pre-bid supply context. The descriptor informs what supply is before the auction begins.

## What crosses the boundary

Supply descriptor fields can be surfaced in Prebid RTD (Real-Time Data) module contexts, made available to buyer-side systems before bid evaluation.

The integration point is the RTD layer. The descriptor is the artifact. Prebid auction mechanics remain unchanged.
