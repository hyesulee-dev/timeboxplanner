# ADR 001: Grid-based Timeline UI

## Status
Accepted 

## Context

TimeBoxPlanner is a time-block planning app where users place tasks directly onto a daily timeline.

In early iterations, the timeline UI mixed two different interaction models:
- A list-based layout with swipe gestures (edit / delete / complete)
- A grid-based layout intended to visually represent time blocks

This combination caused several UX and technical issues:
- Gesture conflicts between vertical scrolling, horizontal swipes, and drag interactions
- Inconsistent visual representation of task duration
- Difficulty maintaining predictable interactions as features expanded

A clearer and more consistent timeline interaction model was required.

---

## Decision

The timeline UI was redesigned as a **grid-based layout**, where:

- The vertical axis represents time
- Each task is displayed as a block
- **Block height directly corresponds to the task’s time duration**
- Tasks can be repositioned and resized via drag gestures

All list-based swipe interactions were removed from the timeline view to avoid gesture conflicts.

---

## Rationale

The grid-based timeline UI was chosen because it:

- Provides an intuitive mental model similar to calendar applications
- Makes time allocation visually explicit
- Reduces interaction ambiguity by unifying gestures
- Scales better as timeline-related features grow

Separating timeline interactions from list-based interactions also simplified both UI logic and user expectations.

---

## Consequences

### Positive
- Improved UX clarity and predictability
- Reduced gesture conflicts
- Clear visual representation of task duration
- Easier long-term maintenance of timeline features

### Trade-offs
- More complex layout and measurement logic
- Requires careful handling of drag and resize interactions

These trade-offs were considered acceptable given the UX and maintainability benefits.

---

## Notes

List-based interactions remain appropriate for non-timeline areas such as Todo lists and dialogs, but are intentionally excluded from the timeline view.
