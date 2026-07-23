## Lessons Learned — cli-admin-01

**Engineering Task:** INF-001

**Version:** 1.0

**Status:** Approved 

**Completion Date:** 2026-07-20

**Author:** George

## 1. Task Summary

The INF-001 Engineering Task produced Administrative workstation with:

- Ubuntu Desktop installed
- Initial hardening completed
- Documentation produced

## 2. Initial Assumptions

- Expected 4GB RAM suffices for installation
- Increasing RAM would solve the black screen issue while the root cause of black screen was insufficient video memory
- LVM and LUKS were separate installation choices
- Ubuntu installer would work with default VirtualBox choices

## 3. Engineering Discoveries

- Video memory, not RAM, caused the installer graphics failure.
- Ubuntu Desktop includes many services by default.
- Root is locked by default.
- Draw.io is sufficient as a web application.
- VirtualBox NAT provides DHCP automatically.
- Ubuntu phased updates are normal.

## 4. Mistakes and Misconceptions

Assumption: More RAM fixes installer black screen
Reality: Graphics handoff failed because video memory was only 16 MB
Resolution: Increased video memory to 128 MB 

Assumption: LVM and LUKS are independent installation options
Reality: Ubuntu's installer combines them in one workflow
Resolution: Verified during installation

Assumption: Loopback ping verifies networking
Reality: Loopback only verifies local TCP/IP stack
Resolution: Verify using interface addresses and Internet connectivity

Assumption: Executing a pre-approved mitigation doesn't require reporting
Reality: The spec and the running machine diverged for three review cycles; discovered by accident
Resolution: Deviations are reported at the moment they occur

Assumption: A snapshot is a slot to overwrite
Reality: Deleting and reusing the name destroyed the clean-install restore point and made the remaining name lie
Resolution: Snapshots are numbered history with truthful names, never deleted mid-task undocumented

Assumption: A change that didn't help can stay
Reality: The failed RAM increase persisted as unexplained configuration until the README review exposed it
Resolution: Revert failed fixes before trying the next hypothesis


## 5. Troubleshooting Insights

| Insight | Application |
|---|---|
| Test one variable at a time | Isolate the effect of each change before introducing another variable |
| Verify hypotheses with evidence | Confirm suspected causes using observable results rather than assumptions |
| Separate symptoms from root causes | Troubleshoot the underlying cause instead of reacting to visible symptoms |
| Preserve recovery points | Use snapshots to reduce recovery time and support experimentation |
| Record evidence during implementation | Capture command outputs immediately to simplify verification and documentation |
| Observation before conclusion | Record factual observations separately from engineering interpretation |

## 6. Engineering Decisions Revisited

The original architecture decisions were appropriate. The original RAM allocation was confirmed correct by measurement; video memory was the one requirement the approved spec missed. The minimal installation procedure makes the administrative workstation lightweight to manage for future infrastructure builds. To reduce the security concerns the LUKS was implemented; however, the downsides have to be taken into account. All the unnecessary ports were closed to reduce the attack surface.

## 7. Improvements for Future Tasks

- Capture verification evidence immediately instead of later.
- Create documentation while implementing, not afterward.
- Record VirtualBox settings before installation.
- Plan verification criteria before implementation.

## 8. Recommendations

- Take a snapshot before configuration changes.
- Verify VirtualBox video memory before troubleshooting installer failures.
- Record default configuration before changing it.
- Document every architectural decision immediately.
- Report any deviation from approved spec immediately, even pre-approved mitigations
- Use snapshots as recovery points of machine stable state. Never delete them without documented reason.

## 9. Knowledge Gained

- Verification: a system is verified by observable evidence against pre-agreed criteria
- Linux memory: free memory represents unused memory while available memory includes caches and buffers that can be utilized without swapping, making it a more valuable resource
- Network diagnosis: connectivity and name resolution are separate layers and are tested separately (IP ping, hostname ping)
- Attack surface: every listening socket is exposure - audit with command (ss -tlnp)
- Storage stack: partitions, volume management, encryption are independent layers; read the actual stack running a command (lsblk)
- Privilege model: locked root plus one sudo user gives accountable, revocable administration
- Architecture governance: conflicting authoritative documents are resolved by formal supersession, not silent edits and reading the ADRs is part of engineering, not decoration
- Documentation: the record is the recovery mechanism — a runbook good enough to rebuild from converts a lost snapshot from a disaster into an hour's work

## 10. Outstanding Questions

- What is the difference between UEFI vs BIOS firmware?
- What is a Secure Boot and how to enable it?
- What is LUKS key management?
- How to configure automated workstation deployment?

## 11. Related Documentation

- README - INF-001
- Runbook INF-001
- Verification Notes INF-001

## 12. Change History
| Version | Date | Description |
|---|---|---|
| 1.0 | 2026-07-20 | Initial version |

## Approval
| Role | Name | Date |
|---|---|---|
| Infrastructure Engineer | George | 2026-07-20 |
| Technical Lead |  | 2026-07-20
