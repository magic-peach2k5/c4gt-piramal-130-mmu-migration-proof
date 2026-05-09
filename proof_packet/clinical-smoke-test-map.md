# Piramal #130 Proof Packet - Clinical Smoke Test Map

Date: 2026-05-05

## Issue
[DMP 2026]: MMU-UI Angular 19 + Zard UI Migration | https://github.com/PSMRI/AMRIT/issues/130

## Status
Audit-backed proposal proof - source citation only, no runtime verification.

## Clinical Smoke Test Map

After each migration slice, verify these clinical workflows pass:

| Workflow | Screen | Validation | Pass Condition |
|----------|--------|------------|----------------|
| **1. Registration** | Beneficiary registration | Form submits, data saved | New record in database |
| **2. Nurse Vitals** | Vital signs entry | BP, temperature, weight recorded | Fields save correctly |
| **3. Doctor Consultation** | Consultation notes | Diagnosis selection works | Text and code saved |
| **4. Lab Order** | Lab test ordering | Tests appear in queue | Order reaches lab module |
| **5. Pharmacy** | Medicine dispensing | Stock decrements | Dispense recorded |
| **6. Data Sync** | Background sync | Records upload | Network indicator green |

## Migration Validation Gates

| Gate | Action | Validation |
|------|--------|------------|
| Gate 1 | Node 18 install | `node --version` returns 18.x |
| Gate 2 | Angular 16 baseline | `ng build` passes |
| Gate 3 | Angular 17 upgrade | `ng build` passes |
| Gate 4 | Angular 18 upgrade | `ng build` passes |
| Gate 5 | Angular 19 upgrade | `ng build` passes |
| Gate 6 | Zard wrapper add | UI renders |
| Gate 7 | Tailwind parity | Layout matches |
| Gate 8 | Full build | Production build |
| Gate 9 | Smoke tests | All 6 workflows pass |

## Wrapper Pattern

```
Material Component → Internal Wrapper → Zard Implementation
```

Example:
```typescript
// Material
<mat-form-field>

// Wrapper
<bs-form-field>

// Zard
<zard-form-field>
```

## Active Blockers

| Blocker | Status | Resolution |
|---------|--------|------------|
| Node 18 missing | Active | Install via nvm |
| Common-UI missing | Active | Git submodule |
| environment.ts empty | Active | Add valid module |

## Proof Artifacts

| Artifact | Claim | Status |
|----------|-------|--------|
| Source audit | 153 components, 30 services | ✅ |
| Build attempts | Failed - blockers found | ✅ |
| Material inventory | 29 Mat* modules | ✅ |
| Smoke-test map | Clinical workflows | ✅ NEW |
| Migration gates | 9 validation gates | ✅ NEW |

## What's NOT Proven

- No Angular 19 build
- No Zard compile
- No clinical parity verified

## Proof Boundary

This is **audit-backed proposal proof** - source citation, not runtime verification.