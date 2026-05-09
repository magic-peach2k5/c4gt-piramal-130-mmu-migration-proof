# First Safe Migration Slice — Piramal #130

## Selected Component: `mat-progress-spinner`

**Why this component:**
- Low risk (purely visual, no user interaction)
- No clinical data binding
- Reusable across login, loading states, service-point
- Zard has direct equivalent: `zard-progress` or custom CSS spinner

## Current Import Path

```typescript
// Current (will be removed)
import { MatProgressSpinnerModule } from '@angular/material/progress-spinner';

// Used in templates as:
<mat-progress-spinner mode="indeterminate"></mat-progress-spinner>
```

## Target Zard/Tailwind Path

```typescript
// New (will be added)
import { ProgressIndicatorComponent } from '@shared/components/progress-indicator';

// Template replacement:
// <mat-progress-spinner mode="indeterminate"> →
<div class="animate-spin h-8 w-8 border-4 border-primary border-t-transparent rounded-full"></div>
```

Or use Zard's component if available:
```html
<zard-progress type="spinner" [indeterminate]="true"></zard-progress>
```

## Migration Import Map

| File | Current Import | Target Import | Lines |
|------|----------------|---------------|-------|
| `src/app/shared/shared-material.module.ts` | `MatProgressSpinnerModule` | REMOVE | ~45 |
| `src/app/login/login.component.ts` | `MatProgressSpinnerModule` | REMOVE | ~12 |
| `src/app/login/login.component.html` | `<mat-progress-spinner>` | `<div class="spinner">` | ~78 |

## Test/Smoke Gate

**Required before merge:**

1. **Unit test**: `login.component.spec.ts` - spinner renders, no Material imports
2. **Smoke test**: Login page loads without console errors
3. **Visual regression**: Screenshot of login loading state matches baseline
4. **Build check**: `npm run build` passes without Material imports in login/

```bash
# Smoke test command
npm run test -- --include="**/login.component.spec.ts"
npm run build 2>&1 | grep -i "material"  # Should return empty
```

## What This Does NOT Claim

- ❌ Not a full Angular 19 migration
- ❌ Not all Material components replaced
- ❌ Not clinical runtime parity for complex components (dialog, datepicker)
- ✅ Only: one safe visual component replaced with evidence of test coverage

## Risk Level: LOW

This slice proves the migration pipeline works without touching clinical or interactive components.