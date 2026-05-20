# Mass-Nudge AI Chat — Flightboard Placement Options

**POC Context**  
Engineering is exploring an AI chat interface (HITL) that lets dispatchers mass-nudge providers — via WO message + push notification — to confirm their assignments for the day or next day. This eliminates the current one-by-one, WO-by-WO workflow. The pattern is intended to be repeatable for other exception types (not checked out, schedule dates passed, inactive assignments, etc.).

**Confirmation Window Background**  
Field Nation's confirmation window is a threshold — typically a set number of hours before a WO's scheduled start — within which an assigned provider is expected to confirm. If they haven't confirmed by that point, the assignment transitions to an "Assigned: At Risk" status on the Flightboard and an alert badge appears on the row. These are the primary targets for the mass-nudge.

---

## Current Flightboard Design — Placement Options

### Option A: Tab-Level Action (Assigned Tab)
**Where:** Inline with the "Assigned 1037" tab label, or as a secondary action bar that appears when the Assigned tab is active.  
**What it looks like:** A pill button — e.g., "Nudge Unconfirmed (47)" — sits adjacent to the tab label. Clicking it opens the AI chat interface pre-filtered to unconfirmed providers.  
**Pros:** Contextually tied to the right status group; count surfaced immediately; low cognitive load.  
**Cons:** Tab labels are already dense; button could feel visually noisy at that level.

---

### Option B: Issue Tab / Dedicated Exception Tab
**Where:** The existing "Issue 29" tab, or a new tab explicitly for unconfirmed/at-risk assignments.  
**What it looks like:** The Issue tab (or a new "Unconfirmed" tab) becomes the exception-handling home. A prominent CTA — "Nudge All Unconfirmed" or a chat icon with a badge count — lives above the table when in this view.  
**Pros:** Consolidates exception handling in one place; sets up the repeatable pattern for other exception types; scoped context for the AI.  
**Cons:** Dispatchers who already work from the Assigned tab may not pivot to a separate tab; some friction in adoption.

---

### Option C: Bulk Checkbox Action Bar
**Where:** The table already has checkboxes on each row. When one or more rows are selected, a contextual action bar appears above (or pinned below) the table.  
**What it looks like:** Select multiple "At Risk" or unconfirmed rows → a bar appears with options including "Nudge Selected Providers (X)" → opens the AI chat with those WOs pre-loaded.  
**Pros:** Familiar bulk-action UX pattern; gives dispatchers precise control over who gets nudged; fits naturally into existing checkbox UI.  
**Cons:** Requires dispatchers to manually identify and select the right rows — defeats some of the efficiency gain unless combined with a smart filter.

---

### Option D: Alert Badge Expansion + "Nudge All Alerts" Header Action
**Where:** The "Alert (1)" badges in the Status column already signal the exception. Option 1: a "Nudge All" action on the Alert column header. Option 2: clicking an Alert badge expands a popover with "Add to nudge queue."  
**What it looks like:** An action on the Status column header — "Nudge All (X alerts)" — triggers the AI chat pre-populated with all alerted rows. Or, the badge click reveals a mini-menu with nudge options.  
**Pros:** Closest to the data signal; meets the dispatcher at the point of awareness.  
**Cons:** Column header actions are non-standard and may be easy to miss; badge popover adds interaction complexity.

---

### Option E: Global Top-Right Action / Notification Area
**Where:** Adjacent to the existing notification bell or the "Create" button in the top-right of the Flightboard header.  
**What it looks like:** A megaphone or alert icon with a red badge count (e.g., "47 unconfirmed"). Clicking it opens the AI chat interface as a side panel or modal.  
**Pros:** Always visible regardless of which tab or filter is active; badge count creates urgency; natural home for a proactive/AI-initiated surface.  
**Cons:** Competes with existing global nav icons; may feel disconnected from the table context.

---

### Option F: Pre-Call Status Column Action
**Where:** The "Pre-Call Status" column header, which already tracks whether providers have been reached pre-shift.  
**What it looks like:** A "Nudge Unconfirmed" action lives in or below the Pre-Call Status column header, since confirmation is semantically related to pre-call readiness.  
**Pros:** Contextually logical — confirmation and pre-call status are tightly related concepts.  
**Cons:** Pre-Call Status is a secondary column; less visible unless dispatchers actively use it.

---

## New Flightboard Design — General Principles

*(The new design was not fully accessible for rendering, but the following applies based on typical Flightboard redesign patterns.)*

If the new design introduces any of the following, the recommended placements shift:

**Exceptions / Needs Attention panel or sidebar** → The chat trigger should live here. This is the natural home for a repeatable exception-handling pattern, and surfaces proactively rather than requiring the dispatcher to hunt for it.

**Proactive action bar or "today's priority" surface** → A prominent "X providers need confirmation" prompt above the work order list, with a single-click to open the AI chat, would align with a more intelligent/proactive Flightboard UX direction.

**AI assistant entry point already present** → If the new design has a general AI assistant button, the mass-nudge flow could be one of its primary intents rather than a standalone trigger.

**More structured exception type filtering** → The repeatable pattern argument is strongest here. If the new design categorizes exceptions (unconfirmed, not checked out, past schedule date), the chat trigger can be scoped per exception type with contextual pre-filtering.

---

## Recommended Starting Point

**Option C (Bulk Checkbox) + a smart filter/pre-selection** is the lowest-friction entry into the current design: it builds on existing UI, gives dispatchers control, and doesn't require a new surface. Pair it with a one-click "Select All At Risk / Unconfirmed" filter option so dispatchers don't have to manually select rows.

**Option B (dedicated exception tab)** sets up the strongest long-term pattern if the goal is to expand to other exception types — it gives the AI chat a consistent home.

For the new design, advocating for a first-class **Exceptions or Needs Attention surface** with the AI chat as the primary action would be the architecturally cleanest fit.

---

*Sources:*  
- [Assigned statuses: definitions and recommended actions](https://support.fieldnation.com/s/article/Assigned-statuses-definitions-and-recommended-actions)  
- [Work Order Status - Buyer Focus](https://support.fieldnation.com/s/article/Work-Order-Status)  
- [Field Nation API Reference - Statuses](https://developer.fieldnation.com/apireference/components/statuses/)
