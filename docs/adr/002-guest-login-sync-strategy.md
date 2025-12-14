# ADR 002: Guest Mode & Account Data Sync Strategy

## Status
Accepted

## Context

TimeBoxPlanner supports both guest usage and authenticated usage.

Requirements:
- Users can start immediately in **Guest Mode** (offline-first, local Room DB)
- After Google login, existing local data should be uploaded to Firestore
- After login, the app should support **bidirectional sync** (local ↔ Firestore)
- On logout, user data should not be destroyed accidentally, but the app should return to a clean guest experience
- On account deletion, all related data must be removed (server + local)

A clear strategy was needed to avoid data duplication, data loss, and “mixed account” states.

---

## Decision

### Data Ownership Model
- In Guest Mode, data is stored only in local Room DB.
- When the user logs in:
  - Guest data is **migrated/uploaded** to the authenticated user space in Firestore.
  - After upload, the app treats Firestore as the sync source for that user.

### Logout Behavior
- Logout does **not** delete persisted account data.
- Instead, the app **hides** the logged-in user’s dataset and switches to a fresh guest context.
- When the user logs in again with the same account, the previously hidden dataset becomes visible again.

### Account Deletion Behavior
- Account deletion removes:
  - Firestore user data (server-side)
  - Local cached data related to that user (device-side)
- After deletion, the app returns to a clean guest state.

---

## Rationale

This strategy was chosen because it:
- Enables immediate start (no-login barrier)
- Minimizes accidental data loss (logout ≠ delete)
- Prevents cross-account data mixing by isolating datasets
- Supports offline-first UX with eventual consistency
- Provides a clear and safe lifecycle: guest → login → sync → logout → relogin / delete

---

## Consequences

### Positive
- Predictable user experience across guest/login/logout/delete
- Reduced risk of “data tangled between accounts”
- Clear migration path from local-only to synced usage
- Works well with background sync (e.g., WorkManager)

### Trade-offs
- Requires dataset separation logic (guest vs user-scoped)
- Needs careful handling of “first login migration” vs regular sync
- Must define conflict resolution rules for bidirectional sync

---

## Notes

Implementation details (e.g., session management, dataset scoping, and worker scheduling) may evolve, but the user-facing behavior described here should remain stable.
