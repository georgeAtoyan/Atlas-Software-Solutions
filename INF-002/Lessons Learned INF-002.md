## Lessons Learned — rtr-edge-01

**Engineering Task:** INF-002

**Version:** 1.1

**Status:** Approved 

**Completion Date:** 2026-08-11

**Author:** George

## 1. Task Summary

The INF-002 Engineering Task produced Debian edge router with a NAT uplink (enp0s3) and a static Management LAN gateway leg (192.168.10.1 on enp0s8), scoped to deployment with routing/NAT deferred.

- Debian Stable 13.6 installed

## 2. Initial Assumptions

- Debian configures networking using Netplan
- Strong root password needed for security

## 3. Engineering Discoveries

- VirtualBox creates an Internal Network as a side-effect of attaching an adapter.
- Predictable interface naming (enp0sN) is stable on VirtualBox
- a /24 address auto-installs a connected route

## 4. Mistakes and Misconceptions

Assumption: Debian configures networking using Netplan
Reality: Debian uses (ifupdown /etc/network/interfaces) to configure networking
Resolution: Verify OS-specific defaults against the target distribution rather than assuming cross-distro parity.

Assumption: There is no connection between DHCP and DNS configuration
Reality: DHCP Option 6 delivers nameservers and the client populates resolv.conf automatically.
Resolution: Verify how the system actually behaves.

Assumption: Strong root password needed for security
Reality: Blank root password locks root and grants sudo which produces a secure model.
Resolution: Research the installer's specific mechanic, rather then making a conclusion from the forum.

Assumption: Expected a canonical DNS nameserver value to 10.0.2.3
Reality: DHCP Option 6 assigned nameserver value to 192.168.0.1 (VirtulBox passing through host DNS)
Resolution: Verify the mechanism, but don't assume the canonical value. Read the actual value off the system.

## 5. Troubleshooting Insights

| Insight | Application |
|---|---|
| Read the actual interface names from the system before configuring them - never assume them | ip -br addr confirmed enp0s8 was the real name; a config matching a wrong name silently fails to bring the interface up |
| Prove configuration persists by rebooting; don't trust the live state | sudo ifup success only proves it works now; the reboot proves the auto line actually activates it at boot |
| Confirm a negative by reading state, don't assume absence | ss -tlnp showing no listeners proved no services run - this defeated the assumption that SSH installs by default |
| Confirm a condition by its signature, not a proxy | lsblk showing no crypt layer is what proves "no encryption" - a partition existing does not prove it |

## 6. Engineering Decisions Revisited

The original architecture decisions were appropriate. After the reboot no passphrase was needed as LUKS feature was disabled during installation proving the availability-critical argument. Uplink (enp0s3-DHCP) and gateway leg (enp0s8-static) came up as designed. NAT/routing are deferred to NET-002 as the router works as a gateway leg with zero routing configured, proving the scope boundary was drawn correctly.

## 7. Improvements for Future Tasks

- Capture verification evidence immediately instead of later.
- Create documentation while implementing, not afterward.
- Record VirtualBox settings before installation.
- Plan verification criteria before implementation.
- Verify every value against its source before submitting; use an explicit checklist when multiple corrections are in play.

## 8. Recommendations

- Take a snapshot before configuration changes.
- Record default configuration before changing it.
- Document every architectural decision immediately.
- Report any deviation from approved spec immediately, even pre-approved mitigations
- Use snapshots as recovery points of machine stable state. Never delete them without documented reason.

## 9. Outstanding Questions

- Why VirtualBox's NAT handed 192.168.0.1 as host-DNS passthrough instead of proxying via 10.0.2.3 ?

Resolved: VirtualBox NAT delivered the host's own DNS server (192.168.0.1, confirmed via ipconfig /all) to the guest through DHCP, rather than the canonical 10.0.2.3 NAT proxy address. This is default host-resolver passthrough behaviour; no DNS proxy was configured.
Lesson: The DNS value a NAT guest receives depends on the hypervisor's DNS mode - verify the observed nameserver rather than assuming the documented 10.0.2.3.

## 10. Related Documentation

- README - INF-002
- Runbook INF-002
- Verification Notes INF-002
- Design Proposal INF-002
- Architecture Diagram
- ADR-024 - VirtualBox Internal Network Naming Convention

## 12. Change History
| Version | Date | Description |
|---|---|---|
| 1.0 | 2026-08-11 | Initial version |
| 1.1 | 2026-08-11 | Extended description of &1 Task Summary, improved &5 Troubleshooting Insights, added additional details in &6 Engineering Decision Revisited |

## Approval
| Role | Name | Date |
|---|---|---|
| Infrastructure Engineer | George | 2026-08-11 |
| Technical Lead |  | 2026-08-11 |
