## **Verification Notes — cli-admin-01** 

**Engineering Task:** INF-001

**Version:** 1.0

**Status:** Approved 

**Verification Date:** 2026-07-23

**Verified By:** George


## 1. Verification Summary

Engineering Task: INF-001 — Administrative Workstation

Infrastructure Component:
- Administrative Workstation (cli-admin-01)
- Ubuntu Desktop 26.04 LTS virtual machine
- VirtualBox-hosted management workstation

Verification Objective:
- Verify that the workstation has been implemented in accordance with the approved Design Proposal and Engineering Task Specification.
- Confirm that all approved Success Criteria have been satisfied through objective verification.
- Confirm that the workstation is operational and ready to support subsequent infrastructure engineering tasks.

## 2. Success Criteria

| ID | Success Criterion | Status |
|---|---|---|
| SC-01 | Hostname resolves to cli-admin-01 | Pass |
| SC-02 | OS is Ubuntu 26.04 LTS | Pass |
| SC-03 | The machine reaches the internet | Pass |
| SC-04 | Successful DNS resolution | Pass |
| SC-05 | The machine completes a full package update | Pass |
| SC-06a | A required tool executes and reports its version: Git | Pass |
| SC-06b | A required tool executes and reports its version: openssh-client | Pass |
| SC-06c | A required tool executes and reports its version: VS code | Pass |
| SC-07 | The system has enough available memory and free swap space (added during verification: memory investigation) | Pass |
| SC-08 | Verify no unnecessary services are listening on ports :22, :631 | Pass |
| SC-09 | Configuration survives the reboot | Pass |


## 3. Verification Procedure

| Success Criterion | Verification Method | Expected Result |
|---|---|---|
| SC-01 | hostname | Correct hostname |
| SC-02 | cat /etc/os-release | Correct OS version |
| SC-03 | ping -c 4 8.8.8.8 | No packet loss |
| SC-04 | ping -c 4 ubuntu.com | No packet loss |
| SC-05 | apt update, apt upgrade, apt list --upgradable | No packages to upgrade |
| SC-06a | git --version | Git reports its version |
| SC-06b | ssh -V | OpenSSH reports its version |
| SC-06c | code --version | VS Code report its version |
| SC-07 | free -h | There is enough available memory and free swap space (idle measurement). There is enough memory under load. |
| SC-08 | ss -tlnp | No unnecessary services are listening on ports :22, :631 |
| SC-09 | reboot the machine, log in, repeat the critical verification commands (from SC-01 to SC-08) and compare with pre-reboot results | Configuration remains unchanged; all required settings and services are preserved after reboot |


## 4. Verification Evidence

| Title | Objective | Command / Method | Observed Result | Conclusion |
|---|---|---|---|---|
| Verification 1 | Verify hostname | hostname | cli-admin-01 | Pass |
| Verification 2 | Verify OS version | cat /etc/os-release | 26.04 LTS | Pass |
| Verification 3 | Verify internet connection | ping -c 4 8.8.8.8 | 0% packet loss | Pass |
| Verification 4 | Verify DNS resolution | ping -c 4 ubuntu.com | 0% packet loss | Pass |
| Verification 5 | Verify system is fully updated | sudo apt update, sudo apt upgrade | All packages are up to date except two held by Ubuntu's phased rollout | Pass |
| Verification 6a | Verify Git installed | git --version | git version 2.53.0 | Pass |
| Verification 6b | Verify OpenSSH installed | ssh -V | OpenSSH_10.2p1 | Pass |
| Verification 6c | Verify VS Code installed | code --version | 1.128.0 | Pass |
| Verification 7 | Verify system has enough available memory and free swap space (idle measurement) | free -h | Memory available space - 2.2Gi, Swap free space - 4.0Gi (no load), Memory available space - 1.5Gi, Swap free space - 3.9Gi (under load) | Pass |
| Verification 8 (before) | Verify no unnecessary services are listening on ports :22 (OpenSSH Server) and :631 (CUPS) | ss -tlnp | Listeners: systemd-resolved on 127.0.0.54:53, 127.0.0.53:53 (loopback only), and 127.0.0.1:631. | Fail |
| Verification 8 (after) | Verify no unnecessary services are listening on ports :22 (OpenSSH Server) and :631 (CUPS) | ss -tlnp | Listeners: systemd-resolved on 127.0.0.54:53, 127.0.0.53:53 (loopback only). No listener on :22. No listener on :631. | Pass |
| Verification 9 | Verify the configuration persists after a complete system reboot | 1) Reboot the machine 2) Login with administrative account 3) Repeat the critical verification commands from SC-01 to SC-08 4) Compare the results with the pre-reboot verification | 1) The system rebooted successfully 2) The login process is successful 3) All the critical configuration settings are unchanged 4) No unexpected configuration changes were observed | Pass |

## 5. Functional Testing

| Test | Expected Result | Actual Result | Status |
|---|---|---|---|
| System Boot | System boots successfully to GNOME login screen | Boot completed successfully | PASS |
| User Login | Administrative user can login | Login successful | PASS |
| Internet Connectivity | Internet access available | Successfully reached external hosts | PASS |
| DNS resolution | Domain names resolve successfully | DNS resolution successful | PASS |
| Package management | apt can update package indexes | apt update completed successfully | PASS |
| Git | Git launches and reports a version | git --version executed successfully | PASS |
| VS Code | VS Code starts successfully | Application launched normally | PASS |
| Firefox | Firefox starts and can browse websites | Browser launched and websites loaded | PASS |
| SSH Client | SSH Client executes successfully | ssh -V reports version information | PASS |

## 6. Reboot Validation

| Verification | Result After Reboot |
|---|---|
| Hostname | Pass |
| Network | Pass |
| Connectivity | Pass |
| Security Configuration | Pass |

## 7. Deviations

| Deviation | Impact | Resolution | Status |
|---|---|---|---|
| Two packages are not upgrading due to phasing | Low | None required: expected phased-rollout behavior | Closed |
| draw.io delivered web-based | Low | approved design change | Closed |
| 128 MB video memory required beyond approved spec (black screen at graphics handoff) | Low | Video memory set to 128 MB | Closed |
| The temporary RAM increase to 6048 MB | Medium | Reverted to 4096MB | Closed |


## 8. Verification Summary

The machine is successfully installed and properly configured based on intended architecture. All success criteria are satisfied. Ubuntu phased updates (python3-software-properties, software-properties-common) but they do not negatively affect the overall performance of the system. Four deviations are documented and successfully closed. The workstation is ready to support subsequent engineering tasks.

## 9. Acceptance Decision

⚠ Passed with Observations
All criteria satisfied; one deviation accepted pending Ubuntu's phased rollout.

## 10. Related Documentation

• Runbook INF-001
• README - INF-001
• Lessons Learned - INF-001

## 11. Change History
| Version | Date | Description |
|---|---|---|
| 1.0 | 2026-07-19 | Initial version |

## Approval
| Role | Name | Date |
|---|---|---|
| Infrastructure Engineer | George | 2026-07-19 |
| Technical Lead |  | 2026-07-19 |