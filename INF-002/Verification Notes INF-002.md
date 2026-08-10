## **Verification Notes — rtr-edge-01* 

**Engineering Task:** INF-002

**Version:** 1.1

**Status:** Approved 

**Verification Date:** 2026-08-10

**Verified By:** George


## 1. Verification Summary

Engineering Task: INF-002 — Debian Router

Infrastructure Component:
- Ddebian Router (rtr-edge-01)
- Debian Stable 13.6.0 virtual machine
- VirtualBox-hosted Debian Router

Verification Objective:
- Verify that the Debian router has been implemented in accordance with the approved Design Proposal and Engineering Task Specification.
- Confirm that all approved Success Criteria have been satisfied through objective verification.
- Confirm that the Debian router is operational and ready to support subsequent infrastructure engineering tasks.

## 2. Success Criteria

| ID | Success Criterion | Status |
|---|---|---|
| SC-01 | Hostname resolves to rtr-edge-01 | Pass |
| SC-02 | OS is Debian Stable 13.6 | Pass |
| SC-03 | The machine reaches the internet | Pass |
| SC-04 | The machine completes a full package update | Pass |
| SC-05 | Configuration survives the reboot | Pass |
| SC-06 | Verify two network interfaces (enp0s3, enp0s8) are present | Pass |
| SC-07 | Verify the router assigned with statis IP address (192.168.10.1) on enp0s8 | Pass |
| SC-08 | Verify no unnecessary serices are listening | Pass |
| SC-09 | Verify correct DNS settings applied | Pass |
| SC-10 | Verify correct DNS name resolution | Pass |

## 3. Verification Procedure

| Success Criterion | Verification Method | Expected Result |
|---|---|---|
| SC-01 | hostname | rtr-edge-01 |
| SC-02 | cat /etc/debian_version | 13.6. |
| SC-03 | ping -c 4 8.8.8.8 | 0% packet loss |
| SC-04 | sudo apt update | All packages are up to date |
| SC-05 | Reboot the machine, log in, repeat the critical verification commands (from SC-01 to SC-04) and compare with pre-reboot results | Configuration remains unchanged; all required settings and services are preserved after reboot
| SC-06 | ip link | enp0s3, enp0s8 |
| SC-07 | ip a show enp0s8 | 192.168.10.1 |
| SC-08 | ss -tlnp | No unnecessary services are listening |
| SC-09 | cat /etc/resolv.conf | A valid nameserver present (canonical VirtualBox NAT DNS is 10.0.2.3) |
| SC-10 | ping -c 4 debian.org | 0% packet loss |


## 4. Verification Evidence

| Title | Objective | Command / Method | Observed Result | Conclusion |
|---|---|---|---|---|
| Verification 1 | Verify hostname | hostname | rtr-edge-01 | Pass |
| Verification 2 | Verify OS version | cat /etc/debian_version | 13.6 | Pass |
| Verification 3 | Verify internet connection | ping -c 4 8.8.8.8 | 0% packet loss | Pass |
| Verification 4 | Verify system is fully updated | sudo apt update | All packages are up to date | Pass |
| Verification 5 | Verify the configuration persists after a complete system reboot | 1) Reboot the machine 2) Login 3) Repeat the critical verification commands from SC-01 to SC-04 4) Compare the results with the pre-reboot verification | 1) The system rebooted successfully 2) The login process is successful 3) All the critical configuration settings are unchanged 4) No unexpected configuration changes were observed | Pass |
| Verification 6 | Verify two network interfaces are present (enp0s3, enp0s8) | ip link | enp0s3, enp0s8 | Pass |
| Verification 7 | Verify the router is assigned with static IP address (192.168.10.1) on enp0s8 | ip a show enp0s8 | 192.168.10.1 | Pass |
| Verification 8 | Verify no unnecessary services are listening | ss -tlnp | No unnecessary services are listening | Pass |
| Verification 9 | Verify correct DNS settings applied | cat /etc/resolv.conf | nameserver 192.168.0.1 | Pass |
| Verification 10 | Verify DNS name resolution | ping -c 4 debian.org | 0% packet loss | Pass |

## 5. Functional Testing

| Test | Expected Result | Actual Result | Status |
|---|---|---|---|
| System Boot | System boots successfully to GNOME login screen | Boot completed successfully | PASS |
| User Login | A user can login | Login successful | PASS |
| Internet Connectivity | Internet access available | Successfully reached external hosts | PASS |
| DNS resolution | Domain names resolve successfully | DNS resolution successful | PASS |
| Package management | apt can update package indexes | apt update completed successfully | PASS |

## 6. Reboot Validation

| Verification | Result After Reboot |
|---|---|
| Hostname | Pass |
| Network | Pass |
| Connectivity | Pass |
| Security Configuration | Pass |
| Network Interface | Pass |
| Services | Pass |

## 7. Deviations

| Deviation | Impact | Resolution | Status |
|---|---|---|---|
| Interface Naming | None | None (enp0s3, enp0s8 confirmed as predicted) | Closed |
| DNS nameserver | None | None (VirtualBox NAT passing through host DNS) | Closed |

## 8. Verification Summary

The machine is successfully installed and properly configured based on intended architecture. All success criteria are satisfied. Two deviations are documented and successfully closed. The Debian Router is ready to support subsequent engineering tasks.

## 9. Acceptance Decision

⚠ Passed with Observations
All criteria satisfied; two deviations are benign hence accepted.

## 10. Related Documentation

• Runbook INF-002
• README - INF-002
• Lessons Learned - INF-002
• ADR-024
• Architecture Diagram
• Engineering Task - INF-002

## 11. Change History
| Version | Date | Description |
|---|---|---|
| 1.0 | 2026-08-10 | Initial version |
| 1.1 | 2026-08-10 | Corrected SC-02 verification evidence, closed SC-09 parenthesis, reframed DNS expected result, fixed Verified By, added reboot Services/Security rows and related-doc references |

## Approval
| Role | Name | Date |
|---|---|---|
| Infrastructure Engineer | George | 2026-08-10 |
| Technical Lead |  | 2026-08-10 |