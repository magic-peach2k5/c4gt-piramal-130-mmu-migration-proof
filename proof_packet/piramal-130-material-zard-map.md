# Piramal #130 Material To Zard UI Migration Map

## Current Material Surface

The audit found `29` unique `Mat*Module` names across source imports and tests. The central shared Material module includes common Angular Material primitives such as:

- Autocomplete
- Button toggle
- Card
- Checkbox
- Chips
- Datepicker and native date support
- Dialog
- Expansion panel
- Grid list
- Icon
- Input
- List
- Menu
- Paginator
- Progress bar and spinner
- Radio
- Select
- Sidenav
- Slide toggle
- Snackbar
- Stepper
- Table
- Tabs
- Tooltip

Feature modules also import Material modules directly. The migration must therefore include a module/import cleanup plan, not only template replacement.

## Migration Mapping

| Current Surface | Zard/Angular Replacement Direction | Risk | Notes |
|---|---|---:|---|
| `mat-card` | Zard card or app wrapper component | Low | Good first target in login/service pages. |
| `mat-form-field`, `matInput`, `mat-label`, `mat-hint` | Zard input/form wrappers with Angular reactive forms | Medium | Must preserve validation display and accessibility labels. |
| `mat-select`, `mat-option` | Zard select/combobox pattern | Medium | Check keyboard behavior and long option lists. |
| `mat-radio-group`, `mat-radio-button` | Zard radio group | Low | Service-point flow is a good proof target. |
| `mat-checkbox` | Zard checkbox | Low | Mostly mechanical after form wrapper exists. |
| `mat-icon` | Lucide/icon strategy or local icon wrapper | Medium | Must avoid breaking current Material icon font assumptions. |
| `mat-table`, `mat-paginator` | Zard table plus pagination wrapper or Angular CDK-backed table | High | Worklists are clinical and dense; requires visual and data regression checks. |
| `mat-dialog` | Zard dialog/sheet wrapper | High | Camera, IoT, and clinical dialogs depend on runtime behavior. |
| `mat-datepicker`, `MatNativeDateModule`, `ngx-bootstrap` datepicker | Choose one date input strategy | High | Date formats and clinical forms make this a migration risk. |
| `mat-tab-group`, `mat-tab` | Zard tabs | Medium | Data-sync and workflow panels rely on disabled state and layout. |
| `mat-sidenav`, drawer containers | Zard sheet/sidebar or Angular CDK overlay | Medium | Verify layout behavior on smaller clinic devices. |
| `mat-menu` | Zard menu/dropdown | Medium | Keyboard and focus handling matter. |
| `mat-tooltip` | Zard tooltip | Low | Mechanical, but accessibility should be checked. |
| `mat-snack-bar` | Zard toast/notification wrapper | Medium | User feedback behavior must remain consistent. |
| `mat-stepper` | Zard stepper substitute or custom workflow wrapper | High | If used in registration, migrate after form primitives. |
| `mat-progress-spinner`, `mat-progress-bar` | Zard progress/loader | Low | Good early replacement once tokens/styles are set. |
| `mat-grid-list` | CSS grid or app layout utilities | Medium | Current app also uses Bootstrap grid; migrate carefully. |

## Bootstrap And CSS Strategy

The app mixes Material with Bootstrap grid and custom classes. Proposal should not promise to remove Bootstrap immediately. Better claim:

- keep Bootstrap layout classes during early Material replacement,
- introduce Zard wrappers and design tokens,
- remove redundant Bootstrap/jQuery only after Zard coverage and layout parity are proven,
- document any retained Bootstrap dependencies as technical debt with an owner.

## AI-Assisted Migration Governance

For reviewers, the serious plan is not "use AI to replace tags." The serious plan is:

- Build a selector inventory before each phase.
- Generate small mechanical diffs only inside a named workflow slice.
- Review every generated diff for behavior, accessibility, and test coverage.
- Add a migration checklist per component family.
- Keep before/after screenshots and command logs as evidence.

## Demo Slice Mapping

Recommended mi-fi proof:

- Source: `login/login.component.html`, `login/login.component.css`, `service-point/service-point.component.html`, one worklist table.
- Proves: card, input, password visibility, select/radio, buttons, table/worklist density, validation text, and Bootstrap coexistence.
- Does not claim: full Angular 19 migration or full clinical runtime parity.
