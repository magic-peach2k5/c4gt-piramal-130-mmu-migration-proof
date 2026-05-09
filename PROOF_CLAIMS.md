# Proof of Work — P3 Piramal #130

**Project:** MMU-UI Angular 19 and Zard UI Migration With Clinical Workflow Parity  
**DMP:** https://github.com/PSMRI/AMRIT/issues/130  
**Proof repo:** https://github.com/magic-peach2k5/c4gt-piramal-130-mmu-migration-proof  

## Claim Boundary
Audit-backed migration plan only. No Angular 19/Zard compile is claimed yet.

## Proof Artifacts

### Source Audit
Analysis of MMU-UI Angular surfaces covering:
- Angular version and dependency tree
- Material component usage (focus, dialogs, date inputs, tables)
- Bootstrap styling and layout dependencies
- Common-UI dependency surface
- Environment configuration and build requirements
- Large workflow components (Workarea, clinical screens)

### Build Blocker Notes
Documented blockers preventing current compile:
- Node version requirements vs current setup
- Common-UI import errors
- Environment configuration gaps
- Angular 16-to-19 upgrade path requirements

### Material-to-Zard Map
Mapping document showing:
- Material components and their Zard equivalents
- Behavior differences requiring wrapper or adaptation
- Styling migration approach per component type
- Dialog, date input, table, and form migration patterns

### First Safe Migration Slice
A spinner component migration demonstrating:
- Wrapper primitive approach
- Behavior parity verification
- Zard component integration
- Visual regression check

### Risk Matrix
Risk assessment for migration phases:
- Angular upgrade risks
- Material behavior parity risks
- Bootstrap/Tailwind layout risks
- Large component decomposition risks
- Timeline and dependency risks

### Screenshots
Screenshots of:
- Current Material spinner in MMU-UI
- Zard spinner component
- Migration wrapper approach
- Risk matrix visualization

## Upgrade Path
Next: Rerun under Node 18 with Common-UI/env handled, or compile one tiny Zard wrapper slice if the baseline can be resolved.
