# ADR-024 — VirtualBox Internal Network Naming Convention

**Status:** Accepted

**Date:** 2026-08-08

**Author:** George

**Reviewer:** Technical Lead

---

## 1. Context

### Background

The INF-002 created the first Internal Network - Management LAN ('mgmt-lan') as a live precedent. The 08B - Infrastructure Architecture.md (&6, &8) names the segments (Management LAN, Server LAN, Client LAN) but no standard governs the internal network naming conventions. And NET-001 will produce the sibling networks needing a consistent, derivable pattern. 

## 2. Problem Statement

The VirtualBox Internal Network identifier is a hand-typed string that must match byte-for-byte across every host on a segment; with no governing standard, NET-001 and upcoming tasks might potentially produce inconsistent strings that silently split one segment into two separate virtual wires with no error message.

Constraints: Identifiers must be reproduced exactly by hand across the tasks.

## 3. Decision

The VirtualBox Internal Network identifier follows a specific name convention <abbr>-lan. 'srv-lan', 'cli-lan' identifiers deriving from Server LAN and Client LAN, respectively, echoing ADR-004's host prefixes naming standards. Whereas 'mgmt-lan' deriving from the segment name (Management LAN).

## 4. Alternatives Considered

### Alternative A — Full words convention (server-lan/client-lan/management-lan)

**Advantages**
- Easier documentation cross referencing.

**Disadvantages**
- Not echoing ADR-004's srv/cli prefixes.

**Reason for Rejection**
- Mild consistency loss.

### Alternative B — Full name convention (Server LAN, Client LAN, Management LAN)

**Advantages**
- Easier documentation cross referencing.

**Disadvantages**
- Combination of spaces and mixed case.

**Reason for Rejection**
- Breaks byte-for-byte hand-matching.

## 5. Rationale

The rule defines the alignment with ADR-004 host prefixes, retypability, and no silent splitting.

## 6. Consequences

### Positive Consequences
The NET-001 and every future segment have a predetermined, unambiguous identifier, eliminating silent segment-splitting.

### Negative Consequences
One more standard to comply with. The 'mgmt-lan' exception (not derived from a host prefix) is a small inconsistency to remember.

### Operational Impact
When creating any Internal Network, the standard should be applied.

### Future Impact
Any segment beyond three - must follow <abbr>-lan pattern.

## 7. Risks

| Risk | Impact | Mitigation |
|---|---|---|
| Identifier name mistyped | Splitting the segment | The identifier is verified against current ADR during the task's verification step (& "C:\Program Files\Oracle\VirtualBox\VBoxManage.exe" showvminfo "rtr-edge-01" | Select-String "NIC")

## 8. Implementation Notes

Documentation-only change. One document touched: this ADR (created). No infrastructure is modified.

## 9. Related Documents

- Engineering Task INF-002
- 08B - Infrastructure Architecture (segment definitions and subnets)
- ADR-004 (host naming - the sibling convention srv/cli derive from)
- ADR-021 (address allocation)

## 10. Review History

| Version | Date | Description |
|---|---|---|
| 1.0 | 2026-08-08 | Initial decision |

## 11. Supersession

**Supersedes:** N/A
**Superseded By:** N/A

## 12. Approval

| Role | Name | Date |
|---|---|---|
| Infrastructure Engineer | George | 2026-08-08 |
| Technical Lead |  | 2026-08-08 |

---

## ADR Summary

| Field | Value |
|---|---|
| ADR ID | ADR-024 |
| Decision | Internal Network identifiers follow <abbr>-lan (mgmt-lan, srv-lan, cli-lan) |
| Status | Accepted |
| Primary Area | Governance |
| Related Engineering Task | INF-002 |
| Review Date | 2026-08-08 |
