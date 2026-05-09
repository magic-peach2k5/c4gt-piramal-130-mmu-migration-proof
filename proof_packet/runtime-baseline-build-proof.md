# Piramal #130 Runtime Baseline Build Proof

**Date**: 2026-05-06

## Attempt 1: Baseline Build

**Status**: Not attempted
**Reason**: No MMU-UI clone in workspace

## Known Blockers (from source audit)

1. **Node version**: Requires Node 18, current environment may differ
2. **Common-UI dependency**: Piramal-specific package, path resolution unknown
3. **environment.ts**: Missing from source audit

## Existing Evidence

- **Source audit**: 153 components, 30 services, 79,237 TS LOC
- **Material-to-Zard map**: In proof_packet/
- **Migration risk matrix**: In proof_packet/

## Blocker Documentation

The proposal honestly documents:
- Node 18 must be established first
- Common-UI imports must be resolved
- environment.ts creation is prerequisite

## Proof Boundary

- **Angular 19**: NOT verified
- **Zard compile**: NOT verified
- **Clinical parity**: NOT verified
- **Standalone conversion**: NOT started

## What This Proves

- Issue requirements understood from live repo inspection
- Blocker stack is documented
- Migration path is analyzed

## What This Does NOT Prove

- Build works under Node 18
- Common-UI resolves
- Angular upgrade succeeds
- Clinical workflows preserved