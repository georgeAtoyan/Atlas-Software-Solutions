# ADR-021 — Establish Infrastructure Architecture §8 as the Single Authoritative IP Address Allocation Policy

**Status:** Accepted

**Date:** 2026-07-16

**Author:** george

**Reviewer:** Technical Lead

---

## 1. Context

### Background

The foundational decision set (ADR-001 through ADR-020) was authored before the Infrastructure Architecture document (Chapter 8B). ADR-005 ("Static Address Planning") defined IP address ranges by functional category. Chapter 8B §8 later defined a more complete Address Allocation Policy for the same /24 networks.

The two documents were never reconciled. The documentation audit (AUD-BLUEPRINT-001, finding AUD-C-01) confirmed that they define **two different allocation schemes**, and that the conflict was resolved informally during Engineering Task INF-001 — where Chapter 8B was treated as authoritative — without the formal supersession required by ADR governance.

This ADR formalizes that resolution.

## 2. Problem Statement

Two governed documents each claim to define the IP address allocation policy, and their contents contradict each other:

| Aspect | ADR-005 | Chapter 8B §8 |
|---|---|---|
| Gateway address | Not defined | .1 |
| Reserved block | Not defined | .2–.9 |
| Infrastructure range | 10–19 | .10–.29 (Core Infrastructure) |
| Services range | 20–39 (Network Services) | .30–.59 (Platform Services) |
| Applications range | 40–59 | .60–.99 |
| Clients range | 60–79 | .100–.149 |
| Temporary range | 80–99 | .150–.199 |
| Expansion range | 100–199 | .200–.254 |
| Coverage of the /24 | Partial (.1–.9, .200–.254 undefined) | Complete |

An engineer following ADR-005 and an engineer following Chapter 8B would allocate the same host to different addresses. Because IP allocation is consumed by every future Engineering Task (INF-002, NET-001 onward), the contradiction must be eliminated before further network work begins.

Constraints:

- ADR-005 is **Accepted** and therefore may not be edited to change its decision (STD-ADR-001 §8; ADR Governance, Chapter 8A).
- The audit established a single-source rule: each normative fact must have exactly one owning document.
- One allocation already exists in production use: `cli-admin-01` at 192.168.10.10 (INF-001).

## 3. Decision

1. The **IP Address Allocation Policy defined in Infrastructure Architecture (Chapter 8B), Section 8** is the **single authoritative source** for all IP address allocation within the Atlas Software Solutions infrastructure.
2. **ADR-005 is superseded** by this ADR. Its allocation ranges must not be used for any future allocation.
3. The allocation table shall exist **only** in Chapter 8B §8. No other document — including this ADR — may reproduce the table. All other documents reference Chapter 8B §8.
4. Future changes to the allocation policy are made by amending Chapter 8B §8 **through a new ADR**, preserving this governance chain.

## 4. Alternatives Considered

### Alternative A — Edit ADR-005 in place to match Chapter 8B

**Advantages**
- Fewest documents; no new ADR number consumed.

**Disadvantages**
- Directly violates STD-ADR-001 §8 ("An accepted ADR should not be edited to change its original engineering decision") and the ADR Governance rules in Chapter 8A.
- Destroys architectural history: a future engineer finding artifacts based on the old ranges would have no record that a second scheme ever existed.

**Reason for Rejection**
Non-compliant with the approved governance model; erases the traceability the ADR system exists to protect.

### Alternative B — Keep both tables and edit them until they match

**Advantages**
- Both documents remain "complete" in isolation.

**Disadvantages**
- Retains two copies of a normative fact; this duplication is the root cause of the original conflict and would inevitably drift again.
- Doubles the maintenance cost of every future allocation change.

**Reason for Rejection**
Violates the single-source principle; treats the symptom, not the root cause (Engineering Principle 14 — Solve the Root Cause).

### Alternative C — Move the allocation table into this ADR and remove it from Chapter 8B

**Advantages**
- The ADR would be fully self-contained.

**Disadvantages**
- The allocation table is a living operational reference consulted on every allocation; STD-ADR-001 §9 directs ADRs to avoid configuration-level detail and remain stable over years.
- Every future range adjustment would require superseding an ADR rather than amending the architecture reference, adding process weight with no benefit.
- Engineers performing tasks work from the Infrastructure Architecture document; splitting the addressing plan away from the network architecture (§6–§8) would fragment the reference.

**Reason for Rejection**
Wrong document type for living reference data; the ADR records *why*, the Architecture document records *what*.

## 5. Rationale

Chapter 8B §8 is selected as the surviving scheme because it is the more complete engineering artifact: it reserves the gateway (.1), defines a reserved block (.2–.9), and covers the entire /24 without gaps, whereas ADR-005 leaves 65 addresses undefined. Chapter 8B also declares itself "the authoritative technical reference for all infrastructure-related Engineering Tasks," and the only allocation performed to date (`cli-admin-01`, 192.168.10.10 in INF-001) was made under the 8B scheme.

A superseding ADR — rather than an edit — is required by STD-ADR-001 Principle 5 (Preserve Architectural History) and §8 (Amendments). Exercising the supersession process now, on the first real conflict, establishes the governance habit while the cost is low.

Holding the table in exactly one location follows Documentation Standards Principle 2 (Every Document Has One Purpose; documents must never duplicate one another) and eliminates the failure mode that produced this conflict.

## 6. Consequences

### Positive Consequences
- Exactly one authoritative allocation policy; the contradiction identified in AUD-C-01 is closed.
- The supersession process defined in STD-ADR-001 has now been exercised in practice, not only on paper.
- Future allocation changes have a defined path: new ADR → amend Chapter 8B §8.

### Negative Consequences
- This ADR is not fully self-contained; a reader must consult Chapter 8B §8 for the current ranges. This is an accepted trade-off in favor of the single-source rule.
- ADR-005 remains in the record in a superseded state, which readers must notice (mitigated by the status field and supersession block).

### Operational Impact
None. The only existing allocation (`cli-admin-01`, 192.168.10.10) is valid under the surviving scheme. **No re-addressing is required.** This constitutes the complete migration strategy.

### Future Impact
INF-002, NET-001 and all subsequent tasks allocate addresses exclusively from Chapter 8B §8. Any document, diagram or template found to contain a copy of the allocation table must be corrected to a reference.

## 7. Risks

| Risk | Impact | Mitigation |
|---|---|---|
| A future engineer reads ADR-005 without noticing its superseded status | Low | Status changed to Superseded; supersession block added at the top of ADR-005 pointing here |
| The allocation table is duplicated again in a future document | Medium | Single-source rule stated in this ADR and in Chapter 8B §8; add "no duplicated normative tables" to documentation review checklists (see audit DOC-008) |
| Chapter 8B §8 is changed without an ADR | Medium | Governance note added directly to §8 requiring an ADR for changes |

## 8. Implementation Notes

Documentation-only change. Three documents are touched: this ADR (created), ADR-005 (status + supersession block), Chapter 8B §8 (authority note + change history). No infrastructure is modified.

## 9. Related Documents

- ADR-005 — Static Address Planning (superseded)
- Infrastructure Architecture, Chapter 8B §8 — Addressing Plan (authoritative)
- STD-ADR-001 — Architecture Decision Record Standard
- Documentation Standards (Chapter 11)
- AUD-BLUEPRINT-001 — Documentation Audit, finding AUD-C-01
- Engineering Task INF-001 — Administrative Workstation (first allocation under the surviving scheme)

## 10. Review History

| Version | Date | Description |
|---|---|---|
| 1.0 | 2026-07-13 | Initial decision |

## 11. Supersession

**Supersedes:** ADR-005
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
| ADR ID | ADR-021 |
| Decision | Chapter 8B §8 is the sole authoritative IP Address Allocation Policy |
| Status | Accepted |
| Primary Area | Networking |
| Related Engineering Task | INF-001 |
| Review Date | 2026-07-13 |
