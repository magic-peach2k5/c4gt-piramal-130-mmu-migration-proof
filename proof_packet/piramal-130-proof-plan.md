# Piramal #130 Proof Plan

## Proof Level

- Tier 0: required proposal notes are in progress.
- Tier 1: source audit completed against a fresh MMU-UI clone.
- Tier 2: prototype should be a source-tied migration slice, not a generic mockup.

## Repository Access

- Repo: `https://github.com/PSMRI/MMU-UI`
- Clone path: `/Users/rahul/Desktop/CFGT/worktrees/MMU-UI`
- Clone status: cloned successfully into an isolated project directory because `/Users/rahul/Desktop/CFGT` is not a git repository.
- package.json status: inspected. The project is Angular 16 with Angular Material 16, Bootstrap 5, jQuery, ngx-bootstrap, webcam, RecordRTC, charts, Excel, and crypto dependencies.

## Local Setup Attempt

- Install attempted: yes, `npm install`.
- Install result: completed. npm installed 1,481 packages and reported 86 audit vulnerabilities.
- Build attempted: yes, `npm run build` and `npm run build-dev`.
- Test attempted: not yet.
- Result: build not passing locally yet.
- Exact blocker, if any:
  - `.nvmrc` requires Node 18, while the active shell reports Node `v25.8.1`; build output warned about odd-numbered Node version.
  - `npm run build` failed because `src/environments/environment.ts` did not exist.
  - `npm run build-dev` created an empty `src/environments/environment.ts`, completed browser bundle generation, then failed because `environment.ts` was not a module and `Common-UI` imports could not resolve.
  - Several CommonJS optimization warnings appeared for `file-saver`, `html2canvas`, `exceljs`, `moment`, `recordrtc`, and `crypto-js`.

## Honest Proposal Claims

- Can claim:
  - I audited the live MMU-UI repository structure.
  - I ran dependency installation in an isolated clone.
  - I attempted both default and development builds and captured concrete blockers.
  - The UI migration is not just component replacement; it crosses routing modules, shared UI modules, Bootstrap layout classes, Material overlay/dialog/table flows, and clinical modules.
  - The largest current files make a phased migration safer than a bulk rewrite.
  - A serious proof should target login/service-point plus one clinical worklist or vitals slice before scaling.
- Cannot claim yet:
  - The current MMU-UI build passes locally.
  - A Zard UI component compiles inside MMU-UI.
  - Angular 19 migration conflicts are fully known.
  - Runtime clinical flows are verified end-to-end.

## Next Best Demo

- Recommended demo path: a mi-fi migration proof that ports the login/service-point surface and one worklist table pattern into a Zard-style component sandbox, with before/after mapping and validation notes.
- Why: login/service-point proves core form controls, password visibility, cards, icons, buttons, and selection flow; one worklist proves table/list interaction and clinical workflow density. This is enough to show migration judgment without pretending the full Angular 19 upgrade is done.

## Demo Acceptance Bar

- The demo must name the exact source files it models.
- It must show Material selector mapping, Bootstrap class retention/replacement decisions, and form/table behavior.
- It must include screenshots or rendered HTML output.
- It must state what remains unverified in the real app.
