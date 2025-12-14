# ADR 003: Timeline Gesture Interaction Model

## Status
Accepted

## Context

The timeline is the core interaction surface of TimeBoxPlanner, where users allocate tasks into specific time blocks.

Early versions experimented with a mix of interaction patterns:
- List-based swipe actions (edit / delete / complete)
- Grid-based drag interactions intended to represent time visually

This mixture caused multiple issues:
- Gesture conflicts between vertical scroll, horizontal swipe, and drag
- Unclear affordances for task manipulation
- Inconsistent mental models for time-based planning

A clear and predictable gesture model, aligned with a grid-based timeline, was required.

---

## Decision

The timeline interaction model is defined as follows:

### 1. Background (Empty Grid) Interaction
- **Single Tap on Empty Grid**
  - Opens an add-task bottom sheet
  - The tapped vertical position is converted into a time slot
  - The new task is initialized with that time context

This replaces explicit “+” buttons and allows faster, spatially-driven task creation.

---

### 2. Timeline Block Interactions

Each timeline block supports a limited and explicit set of gestures:

- **Single Tap (Block)**
  - Opens a modal bottom sheet
  - Provides edit and delete actions

- **Double Tap (Block)**
  - Toggles task completion state (done ↔ not done)
  - Applies immediate visual feedback (strikethrough, reduced opacity)

- **Drag (Bottom Handle Only)**
  - Adjusts the task’s end time
  - Start time remains fixed
  - Duration snaps to predefined time slots

> Dragging the block body to move the start time is intentionally not supported in the current version and is reserved as a possible future extension.

---

### 3. Explicitly Excluded Interactions

- Swipe gestures (left/right) are **not supported** on timeline blocks
- List-style interactions are intentionally excluded from the timeline surface

This avoids accidental actions and reduces gesture ambiguity.

---

## Rationale

This interaction model was chosen because it:

- Aligns with a calendar-like mental model (time flows vertically)
- Maps one user intent to one clear gesture
- Prevents conflicts between drag, swipe, and scroll
- Keeps the user focused on time allocation rather than list manipulation
- Simplifies both UX understanding and UI implementation

Replacing action buttons and swipe gestures with spatial tapping and handles results in a calmer and more predictable experience.

---

## Consequences

### Positive
- Clear separation between timeline and list interaction paradigms
- Reduced accidental edits or state changes
- Strong visual correlation between time and task duration
- Easier long-term extension of timeline behavior

### Trade-offs
- Double-tap completion requires subtle discoverability support
- Grid-based layout and gesture handling increase UI complexity
- Start-time movement via drag is deferred to a future iteration

These trade-offs were accepted to prioritize UX clarity and architectural consistency.

---

## Notes

This decision directly reflects the current implementation of `HomeTimeline.kt`
and intentionally mirrors the interaction rules enforced in code.

Any future changes to timeline gestures should be recorded as a new ADR
rather than modifying this decision retroactively.
