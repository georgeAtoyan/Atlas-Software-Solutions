# ADR-023 — Repository Access and Commit Authority

**Status:** Accepted

**Date:** 2026-07-27

**Author:** George

**Reviewer:** Technical Lead

---

## 1. Context

### Background

Prior to INF-001 Phase all the documentation was pushed from the host machine to the GitHub repository as a trade-off. However, the administrative workstation 'cli-admin-01' is an authoritative administrative environment (reference ADR-007: Operating System Strategy). Thus, all the necessary documents have to be stored locally on administrative workstation 'cli-admin-01' and managed from it (reference ADR-011: Repository Strategy). 

## 2. Problem Statement

The Infrastructure documents are stored on host machine. It potentially raises the security concern as a principle of isolation has to be taken into account. 

## 3. Decision

The documentation is authored and committed from 'cli-admin-01' via SSH-authenticated Git. 

## 4. Alternatives Considered

### Alternative A — Perform Git operations from the host

**Advantages**
- Direct access to host filesystem
- No need to configure Git inside the administrative workstation
- Simple initial setup

**Disadvantages**
- Engineering workflow depends on the host OS
- Infrastructure changes are no longer performed entirely within the managed engineering workstation
- Git configuration and credentials are split between host and administrative workstation

**Reason for Rejection**
Non-compliant with the approved governance model.

## 5. Rationale

Infrastructure documentation, configuration, and engineering artifacts shall be committed to the Git repository from the administrative workstation 'cli-admin-01'. The host machine is not used for routine engineering commits.

## 6. Consequences

### Positive Consequences
- Consistent engineering workflow
- Reduced dependence on the host operating system
- Centralized Git configuration and credentials

### Negative Consequences
- The administrative workstation must be available to perform commits
- Git credentials (SSH keys or PAT) must be securely managed on cli-admin-01
- If cli-admin-01 is unavailable, recovery requires rebuilding the workstation from the Runbook INF-001 and restoring the repository from the remote Git service.

### Operational Impact
- Engineering documentation and infrastructure changes are committed from cli-admin-01
- The administrative workstation requires Git, Git identity, and authentication to the remote repository
- The Windows host continues to provide only virtualization services and it's not part of the engineering workflow

### Future Impact
- Additional administrative workstations can follow the same workflow
- Migration to another host operating system or hypervisor does not change the engineering process
- Git authentication and credential management policies may later be standardized across all administrative workstations.

## 7. Risks

| Risk | Impact | Mitigation |
|---|---|---|
| Administrative workstation becomes unavailable | Low | Rebuild cli-admin-01 using the Runbook INF-001 and clone the repo from the remote Git service |
| Git authentication credentials are lost or compromised | Low | Revoke the affected credential (SSH key or PAT), generate a replacement, and update the Git hosting service  |
| Repository exists only locally (not pushed to remote) | High | Push the repo to a remote Git service and verify synchronization |
| SSH private key stored on the workstation compromised | High | Protect the key with filesystem permissions and a strong passphrase; revoke and replace the key if compromise is suspected |

## 8. Implementation Notes

Documentation-only change. One documents is touched: this ADR (created). No infrastructure is modified.

## 9. Related Documents

- Runbook INF-001 


## 10. Review History

| Version | Date | Description |
|---|---|---|
| 1.0 | 2026-07-27 | Initial decision |

## 11. Supersession


## 12. Approval

| Role | Name | Date |
|---|---|---|
| Infrastructure Engineer | George | 2026-07-27 |
| Technical Lead |  | 2026-07-27 |

---

## ADR Summary

| Field | Value |
|---|---|
| ADR ID | ADR-023 - Repository Access and Commit Authority |
| Decision | Engineering commits originate from cli-admin-01 via SSH-authenticated Git |
| Status | Accepted |
| Primary Area | Governance |
| Related Engineering Task | INF-001 |
| Review Date | 2026-07-27 |