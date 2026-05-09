# Piramal #130 MMU-UI System Map

## Snapshot

- Repository: `PSMRI/MMU-UI`
- Local audit path: `/Users/rahul/Desktop/CFGT/worktrees/MMU-UI`
- Framework baseline: Angular `^16.2.0`, Angular Material `^16.2.x`, TypeScript `~5.1.3`
- Runtime note: `.nvmrc` asks for Node 18; current shell showed Node `v25.8.1`
- Source size signal: TypeScript audit found `79,237` total lines across `.ts` files.

## Angular Inventory

- Components: `153`
- Services: `30`
- Modules: `15`
- Directives: `11`

## Route And Module Shape

Root routing uses `RouterModule.forRoot(..., { useHash: true })` and lazy-loads major areas:

- `registrar`
- `nurse-doctor`
- `lab`
- `pharmacist`
- `datasync`
- `feedback`

Child routing modules exist for registrar, nurse-doctor, lab, pharmacist, and data-sync. This means the proposal should not promise a single UI sweep. It should propose migration by routed workflow clusters.

## Largest Files

The highest-risk migration surfaces are concentrated in clinical workflow files:

| File | Lines | Why It Matters |
|---|---:|---|
| `nurse-doctor/workarea/workarea.component.ts` | 3,824 | Main clinical workarea; high state and interaction risk. |
| `nurse-doctor/shared/services/doctor.service.ts` | 2,973 | Shared doctor service; UI changes can expose API/data assumptions. |
| `nurse-doctor/shared/services/nurse.service.ts` | 2,203 | Shared nurse service; same migration blast radius risk. |
| `nurse-doctor/vitals/general-patient-vitals/general-patient-vitals.component.spec.ts` | 2,120 | Existing test surface can anchor clinical regression checks. |
| `nurse-doctor/idrs/idrs.component.ts` | 1,412 | Large clinical component; avoid early migration until patterns settle. |
| `nurse-doctor/quick-consult/quick-consult.component.ts` | 1,387 | Workflow-heavy screen with IoT/modal hooks. |
| `nurse-doctor/vitals/general-patient-vitals/general-patient-vitals.component.ts` | 1,271 | Good later migration target after basic controls are proven. |
| `registrar/registration/register-demographic-details/register-demographic-details.component.ts` | 1,230 | Registration flow; high form risk and candidate for later phase. |
| `registrar/registration/registration.component.ts` | 1,134 | Large registration container. |
| `lab/workarea/workarea.component.ts` | 1,095 | Worklist/table style validation target. |

## UI Technology Mix

The current app is not Material-only:

- Angular Material is centralized in `core/material.module.ts` and repeated in feature modules.
- Bootstrap and grid classes are spread through templates, including login, service, worklist, data-sync, reports, and vitals screens.
- `ngx-bootstrap` is used for datepicker in registrar.
- jQuery is still a direct dependency.
- Webcam/RecordRTC and IoT flows exist in core and nurse-doctor modules.

## Migration Implication

The proposal should define the project as a staged modernization:

1. Establish a buildable Angular 19 baseline.
2. Create a Zard UI adapter/design-system layer.
3. Replace low-risk shared Material components first.
4. Migrate routed workflow slices with regression checks.
5. Defer large clinical components until form/table/dialog patterns are proven.

## Best First Slices

- Login and service-point: proves form-field, input, card, icon, button, radio/select, and validation behavior.
- Lab or pharmacist worklist: proves dense table/worklist behavior.
- General vitals: later proof for clinical form density, IoT buttons, and dialog behavior.
