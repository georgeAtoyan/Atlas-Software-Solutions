## **README — rtr-edge-01** 

**Engineering Task:** INF-002 rtr-edge-01

**Status:** Approved

**Version:** 1.1

**Last Updated:** 2026-08-11

**Author:** George

## 1. Purpose
The company needs a control network edge - the device that lets the internal segments exist and nodes in these segments reach the Internet.

## 2. Business Role

The foundation upon which the entire segmented network is build on; nothing downstream (Management LAN, future DNS, other segments) can exist without it.

## 3. Architectural Role

rtr-edge-01 is the edge router that sits between the VirtualBox NAT uplink and the internal segments, providing the Management LAN's gateway.

Upstream dependencies:
- VirtualBox NAT (enp0s3 - internet uplink)

Downstream dependencies:
- Management LAN (192.168.10.0/24)

Communication partners:
- Internet (through NAT)

Infrastructure responsibilities:
- Provide Internet access point

## 4. Current Status

The router is operational as a gateway leg (192.168.10.1/24) but routing, forwarding, NAT, firewall are deferred to NET-002. Thus, internal hosts can't reach the Internet yet. And the cli-admin-01 migration is NET-001.

## 5. System Specifications

- VM Name: rtr-edge-01
- Hostname: rtr-edge-01
- Operating System: Debian Stable
- Version: 13.6
- vCPU: 1
- Memory: 1024 MB
- Video Memory: 16 MB
- Storage: 10 GB (dynamically allocated)
- Virtualization Platform: Oracle VirtualBox
- Firmware: BIOS
- Installation Type: Minimal Installation
- Disk Layout: LVM no encryption
- Network (Current): NAT uplink + 'mgmt-lan' gateway leg
- Network (Target): Three segments - Management LAN, Server LAN, Client LAN

## 6. Network Overview

## Current Network

VirtualBox NAT uplink (enp0s3) + 'mgmt-lan' gateway leg (enp0s8 static at 192.168.10.1/24)
DHCP address assigned by VirtualBox.

## Target Architecture

Management LAN
Subnet:
192.168.10.0/24

Gateway:
rtr-edge-01
192.168.10.1

Server LAN:
192.168.20.0/24

Client LAN:
192.168.30.0/24

## 7. Installed Software

base Debian only, no additional packages - and notably no sshd (deferred)

## 8. Security Overview

- During the installation process of Debian Stable 13.6, the LUKS encryption was disabled as the router plays a role of the availability-critical gateway.
- The root account is locked so all actions flow through one named user via sudo, which is auditable and revocable.
- No listening services to minimize the attack surface

## 9. Dependencies

- Internet access (via NAT uplink)
- VirtualBox built-in DHCP

## 10. Related Documentation

- Engineering Task INF-002
- ADR-024 - VirtualBox Internal Network Naming Convention
- Runbook INF-002
- Verification Notes INF-002
- Lessons Learned INF-002
- Architecture Diagram
- Engineering Task NET-001
- Engineering Task NET-002

## 11. Change History

| Version | Date | Description |
|---|---|---|
| 1.0 | 2026-08-11 | Initial version |
| 1.1 | 2026-08-11 | Edited architectural role description, relabel values as Subnet/Network in &6, fixed spelling |

## Approval

| Role | Name | Date |
|---|---|---|
| Infrastructure Engineer | George | 2026-08-11 |
| Technical Lead | | 2026-08-11 |