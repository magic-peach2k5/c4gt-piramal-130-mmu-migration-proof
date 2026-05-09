# Piramal #130 Mi-Fi Prototype Notes

## Purpose

This is reviewer evidence, not a claimed implementation. It shows how the proposal will convert source-backed Angular Material screens into a Zard/Tailwind-style design surface while keeping clinical workflow density visible.

## Source-Tied Scope

The prototype should model these current MMU-UI surfaces:

- `src/app/app-modules/login/login.component.html`
- `src/app/app-modules/service-point/service-point.component.html`
- `src/app/app-modules/lab/worklist/worklist.component.html`
- `src/app/app-modules/pharmacist/worklist/worklist.component.html`

## Controls Demonstrated

- Card layout
- User/password inputs
- Password visibility affordance
- Button states
- Radio/select service choice
- Dense worklist/table rows
- Status chips
- Bootstrap grid coexistence decision
- Migration notes beside the UI

## What It Proves

- The proposal has a concrete first migration slice.
- The applicant understands that low-risk auth/service screens and a worklist/table pattern should precede large clinical workarea migration.
- The proof can be discussed with mentors before touching high-risk clinical components.

## What It Does Not Prove

- It does not prove Angular 19 compatibility.
- It does not prove Zard UI compiles inside MMU-UI.
- It does not prove end-to-end clinical runtime parity.
- It does not replace build/test verification.

## Prototype File

- `/Users/rahul/Desktop/CFGT/tasks/piramal-130-mifi-prototype.html`
