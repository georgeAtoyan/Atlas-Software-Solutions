## **README — cli-admin-01** 

**Engineering Task:** INF-001 cli-admin-01

**Status:** Approved

**Version:** 1.0

**Last Updated:** 2026-07-16

**Verified by:** George

## 1. Purpose
The company has no standardized administrative platform from which the infrastructure can be designed, deployed, documented, and maintained. The current system will play a role of a central administration platform from which the administrator will be able to manage infrastructure, access company resources, and manage documentation. The system will provide the capability of effectively managing the evolving Linux-based infrastructure. 

## 2. Business Role

- serving as the company's standardized engineering workstation;
- providing the administrative environment for infrastructure management;
- acting as the primary platform for documentation, architecture design, and configuration management;
- supporting the deployment and maintenance of the Atlas infrastructure;
- enabling future Engineering Tasks to be performed consistently.

## 3. Architectural Role

Central engineering workstation from which the systems are administered and evolved.

Upstream dependencies:
- Windows host
- VirtualBox
- internet connectivity through VirtualBox built-in NAT network

Downstream dependencies:
- None

Communication partners:
- Windows host
- Internet (through NAT)

Infrastructure responsibilities:
- Infrastructure administration
- Documentation
- Architecture design
- Configuration editing
- Engineering tooling

## 4. Current Status

This system is currently deployed as part of Phase 1. The current implementation uses VirtualBox NAT networking. Migration to the Management LAN will occur during Engineering Task NET-001.

## 5. System Specifications

- VM Name: VirtualBox INF-001 - cli-admin-01
- Hostname: cli-admin-01
- Operating System: Ubuntu Desktop
- Version: 26.04 LTS
- vCPU: 2
- Memory: 4096 MB
- Video Memory: 128 MB
- Storage: 40 GB (dynamically allocated)
- Virtualization Platform: Oracle VirtualBox
- Firmware: UEFI
- Installation Type: Minimal Installation
- Disk Layout: LVM + LUKS
- Network (Current): VirtualBox NAT
- Network (Target): Management LAN (after INF-002/NET-001)

## 6. Network Overview

## Current Network

VirtualBox NAT
DHCP address assigned by VirtualBox.

## Target Architecture

Management LAN
Static IP:
192.168.10.10

Gateway:
rtr-edge-01

DNS:
srv-dns-01

## 7. Installed Software

| Software | Purpose |
|---|---|
| VS Code  | Editing configurations and Markdown documentation |
| Git | Maintain a dedicated Infrastructure Repository alongside separate repositories for future application projects. |
| OpenSSH Client | Connect remotely to other infrastructure nodes |
| draw.io, web-based via Firefox | Primary tool for building infrastructure diagrams |

## 8. Security Overview

- During the installation process of Linux Ubuntu 26.04 LTS, the LUKS encryption was enabled to provide a full-disk encryption. However, it comes with costs: passphrase required at every boot; data is unrecoverable if the passphrase is lost. 
- The root account is locked so all administrative action flows through one named user via sudo, which is auditable and revocable.
- No printing requirements exists. cups.service & cups.socket are disabled and stopped to prevent an unneeded listener per minimal-exposure principle.

## 9. Dependencies

- Internet
- VirtualBox built-in DHCP

## 10. Related Documentation

08A - Infrastructure Decision Record §ADR-004 (Sets the naming convention)
08B - Infrastructure Architecture (Shows where cli-admin-01 fits into the overall infrastructure)
ADR-021 - IP Address Allocation Authority (Documents the authoritative IP addressing policy)
Runbook INF-001
Verification Notes INF-001
Lessons Learned INF-001
Architecture Diagram

## 11. Future Improvements

Migration to Management LAN

## 12. Change History

| Version | Date | Description |
|---|---|---|
| 1.0 | 2026-07-16 | Operational |

## Approval

| Role | Name | Date |
|---|---|---|
| Infrastructure Engineer | George | 2026-07-16 |
| Technical Lead | | 2026-07-16 |
