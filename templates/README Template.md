

README Template
## Instructions
This template shall be copied for every infrastructure component or Engineering Task
requiring a README.
Replace all placeholder text enclosed in < >.
Remove instructional notes before final publication.
All hostnames and VM names must comply with ADR-004 — Server Naming Convention (e.g. srv-dns-01, rtr-edge-01, cli-admin-01). Do not invent alternative naming patterns.
<System Name>
Engineering Task: <INF-001 / NET-004 / OPS-001>
## Status: Planned | In Progress | Operational | Under Maintenance | Deprecated
## Version: 1.0
Last Updated: YYYY-MM-DD
## 1. Purpose
Describe the primary purpose of this system.
Explain why the system exists.
Example questions:
What business problem does it solve?
Why was it introduced?
What capability does it provide?
## 2. Business Role
Describe how this component supports Atlas Software Solutions.
## •
## •
## •
## 1

## Examples:
Infrastructure management
Internal authentication
DNS resolution
## Monitoring
## Backup
## Logging
## 3. Architectural Role
Describe where this component fits within the infrastructure.
## Include:
upstream dependencies;
downstream dependencies;
communication partners;
infrastructure responsibilities.
## 4. Current Status
Describe the current implementation state.
## Example:
This system is currently deployed as part of Phase 1 (Foundation).
The current implementation uses VirtualBox NAT networking.
Migration to the Management LAN will occur during Engineering Task NET-001.
## 5. Technical Specifications
PropertyValue
VM Name<vm-name>
## Hostname<hostname>
Operating System<Operating System>
## •
## •
## •
## •
## •
## •
## •
## •
## •
## •
## 2

PropertyValue
Version<Version>
vCPU<Number>
Memory<Amount>
Storage<Amount>
Virtualization PlatformVirtualBox
## 6. Network Overview
## Current Network
Describe the current network configuration.
## Example:
VirtualBox NAT
DHCP address assigned by VirtualBox.
## Target Architecture
Describe the intended production architecture.
## Example:
Management LAN
Static IP:
## 192.168.10.10
## Gateway:
rtr-edge-01
## DNS:
srv-dns-01

Address allocations must follow the IP Address Allocation Policy in Infrastructure Architecture §8 (per ADR-021). Do not reproduce the allocation table here.
## 3

## 7. Installed Software
SoftwarePurpose
<Software><Purpose>
<Software><Purpose>
<Software><Purpose>
Only list intentionally installed software.
Avoid documenting default operating system packages.
## 8. Security Overview
Describe significant security decisions.
## Examples:
disk encryption;
authentication model;
privilege model;
firewall policy;
SSH policy;
update strategy.
Do not include passwords, private keys or sensitive information.
## 9. Dependencies
List systems required for correct operation.
## Example:
## Internet
## Router
## DNS
## DHCP
## NTP
## LDAP
## •
## •
## •
## •
## •
## •
## •
## •
## •
## •
## •
## •
## 4

## 10. Related Documentation
DocumentPurpose
RunbookSystem installation and operational procedures
Verification NotesVerification evidence
Architecture DiagramInfrastructure placement
ADRArchitectural decisions
Engineering TaskTask implementation record
Lessons LearnedEngineering knowledge gained
## 11. Future Improvements
(Optional)
List planned improvements.
## Examples:
migration to Management LAN;
SSH hardening;
centralized authentication;
monitoring integration.
## 12. Change History
VersionDateDescription
1.0YYYY-MM-DDInitial version
## Approval
RoleNameDate
Infrastructure Engineer<Name>YYYY-MM-DD
## •
## •
## •
## •
## 5

RoleNameDate
Technical Lead<Name>YYYY-MM-DD
## 6

## Template Change History

|Version|Date|Description|
|---|---|---|
|1.0|(original)|Initial template|
|1.1|2026-07-13|§6 example corrected (dns-core-01 → srv-dns-01) per ADR-004 (AUD-C-02); ADR-004 compliance instruction added; §6 references Infrastructure Architecture §8 per ADR-021.|
