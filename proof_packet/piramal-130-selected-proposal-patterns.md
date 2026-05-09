# Piramal #130 Selected Proposal Pattern Notes

Status: proof-packet note for final P3 proposal.
Project: Piramal #130, MMU-UI Angular 16 to Angular 19 + Zard UI migration.

## C4GT Expected Skeleton

The public C4GT proposal templates and selected-contributor guidance point to a simple reviewer-facing structure:

- Applicant details
- Title
- Summary
- Project overview
- Understanding of the project
- Problems
- Solutions
- Implementation details with milestones
- Availability
- Personal motivation
- Previous experience
- C4GT open community / DPG points / GitHub Classroom status where applicable
- Contribution evidence, solved issues, or proof work

## What Selected-Style Proposals Do Well

- Show real project understanding before solutioning.
- Mention concrete contribution evidence, not only interest.
- Ask mentor-specific questions, not assignment requests.
- Tie milestones to deliverables.
- Include investigation time, coding time, testing time, and documentation time.
- Keep the solution scoped to the maintainers' stated problem.
- Avoid claiming full production certainty before repo access, setup, or mentor confirmation.

## Cosmic Proposal Pattern To Reuse

The Cosmic/Regolith proposal was strong because it did more than describe intent. It gave reviewers proof:

- A concrete failure found during qualification.
- Current architecture and dependency chain.
- Target architecture.
- "What works vs what needs custom code."
- Visual and terminal evidence.
- Upstream contribution proof.
- Verification matrix and definition of done.

For Piramal #130, the equivalent is:

- Current MMU-UI architecture map.
- Angular Material to Zard UI replacement map.
- Bootstrap/jQuery removal surface.
- Clinical workflow smoke-test plan.
- `workarea.component.ts` decomposition risk.
- AI-assisted migration governance section.
- Honest proof status: repo audit, setup/build result, prototype only if source-tied.

## What Piramal #130 Proposal Must Add

The proposal should not read like a generic Angular upgrade plan. It should show:

- MMU-UI is a clinical workflow app, so workflow parity matters more than pixel parity.
- Angular 16 to 19 should happen as 16 -> 17 -> 18 -> 19, with a build gate after each major step.
- NgModule to standalone conversion should be feature-scoped, not one bulk rewrite.
- Zard UI and Tailwind replacement needs a component map before code churn starts.
- The nurse-doctor module and `workarea.component.ts` need separate treatment because they concentrate most of the regression risk.
- AI assistance should be used for repeatable transformations, but every generated patch needs human review, build checks, and workflow smoke tests.

## Proposal Sections To Copy Into Final Draft

- **Proof work before applying:** repo audit, module counts, dependency map, Material/Zard map, risk matrix.
- **Current architecture:** Angular 16, NgModules, Material/Bootstrap UI, service/API layer, clinical modules.
- **Target architecture:** Angular 19, standalone components, lazy routes, Zard UI, Tailwind CSS, preserved services.
- **Verification:** production build, route/module smoke tests, clinical workflow checklist, UI replacement checklist.
- **Mentor questions:** workflow parity vs visual parity, first smoke-test flow, `workarea.component.ts` sequencing, QA/demo credentials.

## Sources Checked

- C4GT DMP 2024 proposal template.
- C4GT community proposal template.
- C4GT selected-contributor story.
- C4GT point-system reference.
- Cosmic/Regolith GSoC proposal and mentor-feedback notes from the vault.
