# ADR-022 — Establish Chapter 5 (Engineering Workflow) as the Single Canonical Definition of the Engineering Lifecycle

**Status:** Accepted
**Date:** 2026-07-13
**Author:** Infrastructure Engineer
**Reviewer:** Technical Lead

---

## 1. Context

### Background

The engineering lifecycle — the sequence of stages every Engineering Task must
pass through — was defined independently in three documents, and the
definitions diverged (audit finding AUD-C-03):

- **Chapter 5 (Engineering Workflow)** defined an 11-stage lifecycle in its
  stage text (§5.3–§5.13), while its own §5.2 diagram omitted Technical Review
  and placed Architecture Review after Documentation — contradicting the text
  of the same chapter.
- **The Engineering Task Specification (ETS)** defined a 10-stage lifecycle
  that omitted Infrastructure Assessment, Design Proposal, and Lessons Learned
  as stages, even though its own template sections require them.
- **The Engineering Backlog** defined a 9-state task status flow that omitted
  Problem Analysis and merged several stages.
- Additionally, Chapter 4 §4.4 ("Learning Model") described a fourth variant,
  and the Engineering Task Template header used a fifth status vocabulary
  (Backlog | Ready | In Progress | Blocked | Under Review | Completed).

Both Chapter 5 and the ETS state that skipping lifecycle stages is not
permitted. A skip-prohibition rule is unenforceable when the stage list itself
is ambiguous.

## 2. Problem Statement

Five documents describe the lifecycle; no two agree. An engineer cannot
determine which stages are mandatory, in which order, or which document wins
in a conflict. This is the same failure pattern resolved for IP addressing by
ADR-021: a normative fact duplicated across documents, drifting independently.

Constraints:

- The lifecycle governs every current and future Engineering Task; ambiguity
  compounds with each task.
- The Backlog legitimately needs a *simpler* vocabulary for tracking task
  progress than the full stage list — simplification is acceptable,
  redefinition is not.
- Per the single-source rule (ADR-021 precedent), the canonical definition
  must exist in exactly one document.

## 3. Decision

1. **Chapter 5 (Engineering Workflow) is the single canonical definition of
   the Engineering Lifecycle.** The canonical lifecycle consists of the twelve
   stages defined in Chapter 5 §5.2 (revised).
2. **No other document may define, redraw, or restate the lifecycle.** The
   ETS, the Engineering Backlog, Chapter 4, all templates, standards, and
   diagrams reference Chapter 5 §5.2 instead.
3. **Task status models are workflow tracking states, not lifecycle stages.**
   Any document using a simplified status vocabulary (e.g. the Engineering
   Backlog) must explicitly label it as a tracking model and provide a mapping
   to the canonical lifecycle stages. The authoritative mapping lives in the
   Engineering Backlog ("Task Tracking States").
4. Changes to the lifecycle are made by amending Chapter 5 §5.2 **through a
   new ADR**.

## 4. Alternatives Considered

### Alternative A — Make the ETS lifecycle canonical

**Advantages**
- The ETS is the document engineers open when executing a task.

**Disadvantages**
- The ETS lifecycle was the least complete of the three (missing
  Infrastructure Assessment, Design Proposal, Lessons Learned as stages).
- The ETS's purpose is to define task *structure and quality standards*; the
  workflow chapter exists precisely to define *process*. Assigning process
  authority to the ETS blurs both documents' single purpose (Documentation
  Standards, Principle 2).

**Reason for Rejection**
Wrong document type; weakest starting definition.

### Alternative B — Reconcile all definitions to be identical everywhere

**Advantages**
- Every document self-contained.

**Disadvantages**
- Retains N copies of a normative fact; guarantees future drift — this is the
  exact mechanism that produced the current conflict and the ADR-005 conflict.

**Reason for Rejection**
Treats the symptom, not the root cause (Engineering Principle 14).

### Alternative C — Create a new standalone "Lifecycle Standard" document

**Advantages**
- A dedicated STD-style document with its own governance header.

**Disadvantages**
- Chapter 5 already exists for exactly this purpose; a new document would
  hollow out Chapter 5 and add one more artifact to maintain.
- Increases document count without increasing clarity — complexity without
  benefit (Engineering Principle 3).

**Reason for Rejection**
Duplicates the purpose of an existing chapter.

## 5. Rationale

Chapter 5's stage text was already the most complete definition, and the
chapter's declared purpose is to define "the standard engineering workflow
used throughout the project." Making the most complete definition, in the
document whose purpose it matches, canonical requires the fewest changes and
the least governance surprise.

Distinguishing lifecycle *stages* from tracking *states* resolves the Backlog
conflict without forcing the Backlog to carry twelve statuses: a tracking
state is a coarse-grained progress label; a lifecycle stage is a mandatory
engineering activity. Simplified views are permitted; competing definitions
are not.

## 6. Consequences

### Positive Consequences
- One unambiguous, enforceable lifecycle; "no stage may be skipped" now has a
  definite meaning.
- The stage/state distinction gives the Backlog a legitimate, documented role
  instead of an accidental contradiction.
- The single-source rule now covers the two most-consumed normative facts in
  the Blueprint (addressing: ADR-021; lifecycle: this ADR).

### Negative Consequences
- Readers of the ETS and Backlog must follow a reference to Chapter 5 for the
  full stage definitions. Accepted trade-off, consistent with ADR-021.
- Five documents required conforming edits in one change set.

### Operational Impact
None on infrastructure. INF-001 (currently in Verification) maps cleanly onto
the canonical lifecycle at Stage 9; no rework required.

### Future Impact
All future Engineering Tasks are planned, tracked, and reviewed against
Chapter 5 §5.2. Review checklists must reject documents that restate the
lifecycle instead of referencing it.

## 7. Risks

| Risk | Impact | Mitigation |
|---|---|---|
| A future document restates the lifecycle | Medium | No-duplication review-checklist item (established in STD-DIAGRAM-001 v1.1; to be propagated via DOC-008) |
| Tracking states drift from the stage mapping | Low | The mapping table lives only in the Backlog; changes require an ADR per this decision |
| Engineers confuse "Technical Review" (Stage 7, design approval) with the post-implementation review (Stage 11) | Low | Stages renamed unambiguously in Chapter 5 §5.2 (revised) |

## 8. Implementation Notes

Documentation-only change. Documents touched: Chapter 5 (canonical
definition), ETS, Engineering Backlog, Chapter 4 §4.4, Engineering Task
Template. See the accompanying revision files.

## 9. Related Documents

- Chapter 5 — Engineering Workflow §5.2 (canonical lifecycle)
- Engineering Task Specification (revised lifecycle section)
- Engineering Backlog (Task Tracking States and mapping)
- Chapter 4 §4.4 (revised)
- Engineering Task Template v1.1
- ADR-021 (single-source precedent)
- AUD-BLUEPRINT-001, finding AUD-C-03

## 10. Review History

| Version | Date | Description |
|---|---|---|
| 1.0 | 2026-07-13 | Initial decision |

## 11. Supersession

**Supersedes:** None
**Superseded By:** N/A

## 12. Approval

| Role | Name | Date |
|---|---|---|
| Infrastructure Engineer | George | 2026-07-13 |
| Technical Lead | Approved | 2026-07-13 |

---

## ADR Summary

| Field | Value |
|---|---|
| ADR ID | ADR-022 |
| Decision | Chapter 5 §5.2 is the sole canonical Engineering Lifecycle definition |
| Status | Accepted |
| Primary Area | Engineering Processes / Documentation |
| Related Engineering Task | — (governance change) |
| Review Date | 2026-07-13 |
