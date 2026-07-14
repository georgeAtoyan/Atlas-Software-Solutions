

## Architecture Diagram Standard
Document ID: STD-DIAGRAM-001
## Version: 1.1
## Status: Approved
## 1. Purpose
Architecture Diagrams provide a visual representation of the Atlas Software Solutions infrastructure.
Their purpose is to communicate infrastructure design quickly, accurately, and consistently.
A diagram should allow an engineer unfamiliar with the project to understand the overall architecture
within one minute.
Architecture Diagrams complement written documentation but never replace it.
## 2. Scope
This standard applies to all diagrams produced as part of the Atlas Software Solutions Engineering
Blueprint, including:
## Infrastructure Architecture
## Network Topology
## Engineering Tasks
## Security Architecture
## Identity Infrastructure
## Monitoring Architecture
## Storage Architecture
## Cloud Architecture
## Hybrid Infrastructure
## Disaster Recovery
## Service Dependencies
## 3. Engineering Objectives
Every Architecture Diagram should answer the following questions:
What components exist?
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
## 1

How are they connected?
Which networks are involved?
What is the communication flow?
Which systems depend on one another?
Where does the component fit within the infrastructure?
## 4. Engineering Principles
## Principle 1 — Simplicity
A diagram should communicate architecture rather than implementation.
Avoid unnecessary detail.
## Principle 2 — Accuracy
Every diagram must reflect the current infrastructure.
If the architecture changes, the diagram must be updated.
## Principle 3 — Consistency
All diagrams should use the same symbols, naming conventions, and layout principles.
An engineer should immediately recognize any Atlas diagram.
## Principle 4 — Readability
Diagrams should minimize crossed lines, overlapping objects, and visual clutter.
If a diagram becomes difficult to read, divide it into multiple diagrams.
## Principle 5 — Single Responsibility
Each diagram should illustrate one primary aspect of the infrastructure.
Do not combine unrelated concepts into one drawing.
## •
## •
## •
## •
## •
## 2

## 5. Diagram Types
The following diagram types are approved.
## Infrastructure Overview
Shows the complete infrastructure at a high level.
## Audience:
## Technical Lead
## Infrastructure Engineers
New team members
## Network Topology
## Shows:
network segments;
routers;
switches (physical or logical);
gateways;
addressing;
traffic flow.
## Service Architecture
## Shows:
services;
communication paths;
dependencies;
protocols.
## Engineering Task Diagram
Illustrates the infrastructure relevant to a specific Engineering Task.
These diagrams should remain intentionally small.
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
## •
## 3

## Dependency Diagram
Illustrates relationships between infrastructure services.
## Examples:
## DNS → LDAP
## Prometheus → Grafana
## Client → Router → Internet
## 6. Required Elements
Every Architecture Diagram should include:
title;
version or revision;
date (optional but recommended);
legend if custom symbols are used.
Where applicable, diagrams should also identify:
hostnames;
VM names;
network names;
IP subnets;
communication protocols.
## 7. Naming Standards
All system names in diagrams **must comply with ADR-004 — Server Naming Convention**. ADR-004 is the authoritative naming decision; this section provides diagram-specific guidance only and must never define or imply a different convention.

The approved patterns (see ADR-004):

|Component type|Pattern|Compliant examples|
|---|---|---|
|Servers|srv-<role>-<number>|srv-dns-01, srv-dns-02, srv-ntp-01, srv-monitor-01, srv-ca-01, srv-web-01, srv-git-01|
|Routers|rtr-<role>-<number>|rtr-edge-01|
|Workstations|cli-<role>-<number>|cli-admin-01, cli-dev-01|
|Switches (future)|sw-<role>-<number>|sw-core-01|
|Kubernetes nodes (future)|k8s-<role>-<number>|k8s-master-01, k8s-worker-01|

Avoid generic names such as:
- Server1
- LinuxVM
- Test
- MachineA

Avoid inventing alternative patterns (e.g. dns-core-01); every name in a diagram must match a real or planned host named under ADR-004.

## 8. Layout Guidelines
Diagrams should follow a logical flow.
Preferred orientation:
## External Networks
## ↓
## Perimeter
## ↓
## Core Infrastructure
## ↓
## Management Services
## ↓
## Application Services
## ↓
## Client Systems
Traffic should generally flow from top to bottom or from left to right.
Avoid random placement of components.
## •
## •
## •
## •
## 5

## 9. Network Representation
Each network segment should be clearly identified.
## Examples:
## Internet
VirtualBox NAT
Management LAN
Server LAN
Client LAN
DMZ (future)
Each segment should display its subnet where appropriate.
## Example:
Management LAN
## 192.168.10.0/24
## 10. Communication Paths
Communication paths should indicate the relationship between systems.
When useful, label connections with the primary protocol.
## Examples:
## SSH
## DNS
## DHCP
## HTTP
## HTTPS
## LDAP
## NTP
## ICMP
Avoid excessive protocol labels where they reduce readability.
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
## •
## •
## 6

- Level of Detail
Architecture Diagrams should remain high-level.
Do include:
systems;
networks;
major communication paths;
service dependencies.
Do not include:
configuration files;
command outputs;
firewall rules;
package names;
implementation steps.
Those belong in Runbooks or other documentation.
## 12. Diagram Evolution
As the infrastructure grows, diagrams should evolve.
Prefer several focused diagrams over one oversized diagram.
## Examples:
## Infrastructure Overview
## ↓
## Network Topology
## ↓
DNS Architecture
## ↓
PKI Architecture
## ↓
## •
## •
## •
## •
## •
## •
## •
## •
## •
## 7

## Monitoring Architecture
Each diagram should remain understandable on its own.
## 13. Recommended Tool
The standard diagramming tool for Atlas Software Solutions is:
draw.io (diagrams.net)
All source diagrams should be stored in editable format.
Recommended exports include:
## PNG
## SVG
## PDF
Do not store only exported images.
The editable source file is the authoritative version.
- Relationship to Other Documents
Architecture Diagrams complement the remaining engineering documentation.
DocumentPurpose
READMEExplains what the component is
RunbookExplains how the component is built
Verification NotesDemonstrates that the implementation works
ADRExplains why architectural decisions were made
Architecture DiagramShows where the component fits within the infrastructure
Lessons LearnedCaptures engineering knowledge gained during implementation
## •
## •
## •
## 8

## 15. Review Checklist
Before approval verify that:
- the diagram reflects the current architecture;
- all component names comply with ADR-004 (no invented or legacy naming patterns);
- network segments are clearly identified;
- communication paths are understandable;
- unnecessary details have been omitted;
- the layout is clean and readable;
- no normative content (naming rules, address allocations) is duplicated from an authoritative source — reference ADR-004 and Infrastructure Architecture §8 instead;
- related documentation references are correct.
- Definition of Done
An Architecture Diagram is considered complete when:
it accurately represents the implemented infrastructure;
all required components are present;
naming follows the Infrastructure Naming Standard;
communication paths are understandable;
the diagram remains clear and uncluttered;
the editable source file is stored in the repository;
the Technical Lead has reviewed and approved the diagram.
The approved Architecture Diagram becomes the authoritative visual representation of the infrastructure
component throughout its lifecycle.
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
## •
## •
## 9

## Change History

|Version|Date|Description|
|---|---|---|
|1.0|(original)|Initial standard|
|1.1|2026-07-13|§7: non-compliant examples (dns-core-01/02, ntp-core-01, mon-core-01) replaced with ADR-004-compliant forms; ADR-004 declared authoritative; pattern table added. §15: ADR-004 compliance and no-duplication checklist items added. Resolves AUD-C-02.|
