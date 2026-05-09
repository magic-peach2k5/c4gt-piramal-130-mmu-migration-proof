# Piramal #130 Migration Risk Matrix

## Risk Summary

The main risk is not visual styling. It is preserving clinical workflow behavior while changing Angular version, component library, overlays, forms, and layout primitives.

| Area | Risk | Why | Mitigation |
|---|---:|---|---|
| Local environment | High | `.nvmrc` requires Node 18, but the current shell is Node 25. | Pin Node 18 before install/build proof; document setup commands. |
| Angular 16 to Angular 19 | High | Framework, compiler, TypeScript, and dependency compatibility can fail before UI work starts. | Upgrade one major version at a time if needed; keep build logs; avoid UI replacement until baseline compiles. |
| Angular Material removal | High | Material modules are centralized and repeated in feature modules/tests. | Create inventory, wrappers, and phased replacement map before removing package dependencies. |
| Forms | High | Login, registration, vitals, and clinical flows depend on validation, disabled states, and form layout. | Start with login/service-point; add form-level regression checks. |
| Tables/worklists | High | Lab, pharmacist, and nurse/doctor worklists drive actual workflow. | Create a table migration wrapper and run worklist smoke tests. |
| Dialogs/overlays | High | Camera, IoT, and clinical flows use dialogs and overlay behavior. | Defer until basic primitives are stable; test focus, close, and data return behavior. |
| Date inputs | High | Material datepicker and ngx-bootstrap datepicker both appear. | Decide a single date strategy; test formatting and validators. |
| Bootstrap/jQuery coexistence | Medium | Templates rely heavily on Bootstrap grid/classes, while dependencies include jQuery. | Keep layout stable initially; remove only after visual parity and dependency audit. |
| Large components | High | `workarea.component.ts` is 3,824 lines and other clinical files exceed 1,000 lines. | Migrate workflow slices, not whole large files. |
| Tests | Medium | Existing specs exist but local test status is not yet verified. | Run build/test under Node 18; add smoke tests around migrated slices. |
| Accessibility | Medium | Material currently provides keyboard/focus behavior. | Use Zard primitives with explicit keyboard/focus checks. |
| Mentor review | Medium | UI library choices can have maintainability preferences. | Ask mentor to confirm migration order and acceptable retained Bootstrap scope early. |

## Proposal Controls

- Week 1 should be discovery, environment alignment, selector inventory, and migration architecture.
- First coding milestone should be a narrow baseline and one low-risk UI slice.
- Large clinical screens should appear after shared primitives are proven.
- The proposal should include rollback criteria: if Angular 19 upgrade blocks, first deliver an Angular 16-compatible Zard migration plan or wrapper spike, then resume framework migration with mentor input.

## Proof We Can Show

- Repo audit with concrete counts and largest-file list.
- Material-to-Zard mapping table.
- Risk matrix tied to exact files and dependencies.
- Optional mi-fi prototype using source-tied login/service-point/worklist screens.
- Setup/build log under Node 18 once environment is aligned.
