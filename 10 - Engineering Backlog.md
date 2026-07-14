

## Engineering Backlog
## Purpose
The Engineering Backlog is the master implementation roadmap for the Atlas Software Solutions
infrastructure.
It defines every Engineering Task required to design, build, operate and evolve the environment.
Tasks are completed in dependency order rather than chronological order.
Progression is based on demonstrated understanding and successful implementation—not on time.
The backlog is a living engineering document and will evolve as the infrastructure grows.
## Engineering Phases
The project is divided into engineering phases.
A phase is complete only when all required Engineering Tasks have been successfully implemented, verified
and documented.
## Phase 1 — Linux Foundations
## Objective:
Establish the core infrastructure required for all future engineering work.
Topics include:
VirtualBox
Linux installation
## Filesystems
Users and groups
## SSH
systemd
Package management
Basic networking
Documentation standards
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

## Exit Criteria:
The learner can confidently install, configure and administer Linux servers without step-by-step
instructions.
## Phase 2 — Core Networking
## Objective:
Build a routed internal network capable of supporting multiple infrastructure services.
Topics include:
## Router
IP addressing
Static routing
## NAT
Packet forwarding
nftables/iptables
DNS fundamentals
TCP/IP troubleshooting
## Exit Criteria:
The learner understands packet flow throughout the infrastructure.
## Phase 3 — Infrastructure Services
## Objective:
Deploy the essential services required by the company.
Topics include:
Primary DNS
Secondary DNS
Reverse DNS
## DHCP
## NTP
Internal web services
## Exit Criteria:
Internal services communicate reliably using the infrastructure.
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
## 2

## Phase 4 — Identity & Access
## Objective:
Introduce centralized authentication.
Topics include:
## LDAP
## PAM
## NSS
## SSSD
SSH authentication
## Permissions
## Exit Criteria:
Identity management is centralized and understood.
Phase 5 — Security & PKI
## Objective:
Build trust and secure communication.
Topics include:
Internal CA
## TLS
## Certificates
## HTTPS
SSH hardening
Least privilege
## Exit Criteria:
Internal communication is encrypted and trust is centrally managed.
## Phase 6 — Operations
## Objective:
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

Operate infrastructure professionally.
Topics include:
## Monitoring
## Logging
## Backups
## Recovery
## Runbooks
Incident response
## Exit Criteria:
Infrastructure can be monitored, maintained and recovered.
## Phase 7 — Automation
## Objective:
Reduce repetitive operational work.
Topics include:
## Bash
## Python
## Git
## Ansible
Scheduled automation
## Exit Criteria:
Routine administrative tasks are automated without sacrificing understanding.
## Phase 8 — Containers
## Objective:
Introduce application portability.
Topics include:
## Docker
## Images
## Registries
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
## 4

## Networks
## Volumes
## Compose
## Exit Criteria:
Applications are containerized and managed confidently.
## Phase 9 — Cloud Integration
## Objective:
Extend the existing infrastructure into AWS.
Topics include:
## EC2
## VPC
## IAM
## Security Groups
## Route Tables
Hybrid networking
## Exit Criteria:
Core infrastructure concepts are successfully applied in the cloud.
## Phase 10 — Production Readiness
## Objective:
Prepare for a Junior Linux System Administrator role.
Topics include:
Architecture reviews
Troubleshooting scenarios
Mock incidents
Technical interviews
Documentation review
Infrastructure improvements
## Exit Criteria:
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
## •
## 5

The learner demonstrates the knowledge, judgement and confidence expected of a professional Junior
## Linux System Administrator.
## Task Tracking States

> **These are workflow tracking states, not lifecycle stages.** The Engineering Lifecycle is defined exclusively in **Chapter 5 (Engineering Workflow), Section 5.2** (ADR-022). Tracking states are coarse-grained progress labels; each maps to one or more canonical lifecycle stages as shown below. This section must never be cited as a lifecycle definition.

Every Engineering Task carries exactly one tracking state:

Backlog → Ready → Research → Design Review → Implementation → Verification → Documentation → Review → Completed

A task's state may only advance when all lifecycle stages mapped to the previous state are complete.

### Tracking State → Lifecycle Stage Mapping (authoritative)

|Tracking State|Canonical Lifecycle Stages (Ch. 5 §5.2)|Meaning|
|---|---|---|
|Backlog|— (pre-lifecycle)|Requirement identified; task defined, not started|
|Ready|Stage 1 — Business Requirement|Task assigned; requirement confirmed|
|Research|Stages 2–4 — Problem Analysis, Infrastructure Assessment, Research & Theory|Understanding problem, environment, theory|
|Design Review|Stages 5–7 — Architecture Discussion, Design Proposal, Design Review & Approval|Designing and obtaining approval|
|Implementation|Stage 8 — Implementation|Executing the approved design|
|Verification|Stage 9 — Verification|Proving Success Criteria per STD-VERIFY-001|
|Documentation|Stage 10 — Documentation|Producing required deliverables|
|Review|Stage 11 — Post-Implementation Review & Lessons Learned|Outcome review; Lessons Learned|
|Completed|Stage 12 — Task Closure|Exit criteria confirmed; task closed|

### Exception Flag: Blocked

**Blocked** is not a state in the sequence; it is an exception flag applicable in any state when progress is prevented by an external dependency. A blocked task records the state it was in, the blocking dependency, and the unblocking condition; when unblocked it resumes in its recorded state.

### Naming Note

The former state "Architecture Review" is renamed **Design Review** and the former "Technical Review" is renamed **Review**, matching the canonical stage names.

## Task Registry
Each task is recorded using the following fields:
FieldDescription
Task IDUnique identifier
TitleEngineering Task name
PhaseEngineering Phase
PriorityHigh / Medium / Low
DependenciesRequired prerequisite tasks
Related ADRApplicable architecture decisions
Nemeth ChaptersRequired reading
Required VMsSystems required for execution
DeliverablesDocumentation and implementation outputs
StatusCurrent lifecycle stage
## Initial Engineering Backlog
IDTitlePhaseDepends On
INF-001Build Administrative WorkstationPhase 1—
INF-002Deploy Debian RouterPhase 1INF-001
NET-001Configure Internal NetworksPhase 2INF-002
NET-002Configure Routing & NATPhase 2NET-001
NET-003Validate Packet FlowPhase 2NET-002
NET-004Deploy Primary DNSPhase 3NET-003
NET-005Deploy Reverse DNSPhase 3NET-004
NET-006Deploy Secondary DNSPhase 3NET-005
NET-007Implement DHCPPhase 3NET-006
OPS-001Configure NTPPhase 3NET-007
SEC-001Build Internal Certificate AuthorityPhase 5NET-006
## 7

IDTitlePhaseDepends On
SEC-002Secure Internal Web Services with TLSPhase 5SEC-001
INF-003Deploy LDAP ServerPhase 4NET-006
INF-004Configure NSS, PAM and SSSDPhase 4INF-003
OPS-002Deploy Monitoring StackPhase 6INF-004
OPS-003Configure Centralized LoggingPhase 6OPS-002
OPS-004Implement Backup StrategyPhase 6OPS-003
AUT-001Automate Administrative Tasks with BashPhase 7OPS-004
AUT-002Introduce Git for InfrastructurePhase 7AUT-001
AUT-003Deploy AnsiblePhase 7AUT-002
CNT-001Deploy DockerPhase 8AUT-003
CNT-002Containerize Internal ServicesPhase 8CNT-001
CLD-001Create AWS FoundationPhase 9CNT-002
CLD-002Extend Infrastructure into AWSPhase 9CLD-001
OPS-005Production Readiness AssessmentPhase 10CLD-002
## Phase Completion Criteria
A phase is complete only when:
All Engineering Tasks are completed.
Documentation is current.
ADRs are updated.
Architecture remains consistent.
The Technical Lead approves progression.
The learner can explain the rationale behind every major decision.
Advancing without understanding is not permitted.
## Backlog Maintenance
The backlog is reviewed after every completed Engineering Task.
## •
## •
## •
## •
## •
## •
## 8

The Technical Lead determines whether:
new tasks should be added;
priorities should change;
dependencies should be updated;
new ADRs are required.
The backlog reflects the current state of the infrastructure and the business.
## Guiding Principle
The Engineering Backlog is not a checklist to finish as quickly as possible.
It is the structured development plan for both the Atlas Software Solutions infrastructure and the engineer
responsible for designing, operating and improving it.
Each completed task represents not only a technical implementation but also a measurable step toward
becoming a professional Infrastructure Engineer.
## •
## •
## •
## •
## 9

## Engineering Backlog Change History

|Version|Date|Description|
|---|---|---|
|1.0|(original)|Initial backlog|
|1.1|2026-07-13|"Task Status" replaced by "Task Tracking States" per ADR-022: declared a tracking model with authoritative mapping to Chapter 5 §5.2; Blocked formalized as exception flag; two states renamed.|
