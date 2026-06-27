# Buyer Agent

## What a buyer agent owns

A buyer agent executes media buys on behalf of advertisers. It evaluates available supply, determines bid eligibility, manages targeting, and submits bids into auction environments.

## Where Modulr fits

Modulr descriptors are designed to be consumed by buyer agents as pre-bid supply context.

Modulr does not tell buyer agents whether to bid. Modulr does not set targeting rules. Modulr does not determine campaign eligibility.

The descriptor describes supply. The buyer agent determines how to reason against that description in its own execution context.

## What crosses the boundary

Supply descriptor fields provide the buyer agent with machine-readable evidence about what inventory contains, what commercial reasoning it supports, how suitable it is for a given adjacency, and how confident the descriptor is in those claims.

This is distinct from audience signals. Modulr descriptors contain no user identity, behavioral data, or audience profile information.
