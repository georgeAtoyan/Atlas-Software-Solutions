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
- VirtualBox
- Linux installation
- Filesystems
- Users and groups
- SSH
- systemd
- Package management
- Basic networking
- Documentation standards

### Exit Criteria: 
The learner can confidently install, configure and administer Linux servers without step-by-step
instructions.

## Phase 2 — Core Networking
## Objective:
Build a routed internal network capable of supporting multiple infrastructure services.

Topics include:
- Router
- IP addressing
- Static routing
- NAT
- Packet forwarding
- nftables/iptables
- DNS fundamentals
- TCP/IP troubleshooting

### Exit Criteria:
The learner understands packet flow throughout the infrastructure.

## Phase 3 — Infrastructure Services
## Objective:
Deploy the essential services required by the company.

Topics include:
- Primary DNS
- Secondary DNS
- Reverse DNS
- DHCP
- NTP
- Internal web services

### Exit Criteria:
Internal services communicate reliably using the infrastructure.

## Phase 4 — Identity & Access
## Objective:
Introduce centralized authentication.

Topics include:
- LDAP
- PAM
- NSS
- SSSD
- SSH authentication
- Permissions

### Exit Criteria:
Identity management is centralized and understood.

## Phase 5 — Security & PKI
## Objective:
Build trust and secure communication.

Topics include:
- Internal CA
- TLS
- Certificates
- HTTPS
- SSH hardening
- Least privilege

### Exit Criteria:
Internal communication is encrypted and trust is centrally managed.

## Phase 6 — Operations
## Objective:
Operate infrastructure professionally.

Topics include:
- Monitoring
- Logging
- Backups
- Recovery
- Runbooks
- Incident response

### Exit Criteria:
Infrastructure can be monitored, maintained and recovered.

## Phase 7 — Automation
## Objective:
Reduce repetitive operational work.

Topics include: 
- Bash
- Python
- Git
- Ansible
- Scheduled automation

### Exit Criteria:
Routine administrative tasks are automated without sacrificing understanding.

## Phase 8 — Containers
## Objective:
Introduce application portability.

Topics include:
- Docker
- Images
- Registries
- Networks
- Volumes
- Compose

### Exit Criteria:
Applications are containerized and managed confidently.

## Phase 9 — Cloud Integration
## Objective:
Extend the existing infrastructure into AWS.

Topics include:
- EC2
- VPC
- IAM
- Security Groups
- Route Tables
- Hybrid networking

### Exit Criteria:
Core infrastructure concepts are successfully applied in the cloud.

## Phase 10 — Production Readiness
## Objective:
Prepare for a Junior Linux System Administrator role.

Topics include:
- Architecture reviews
- Troubleshooting scenarios
- Mock incidents
- Technical interviews
- Documentation review
- Infrastructure improvements

### Exit Criteria:
The learner demonstrates the knowledge, judgement and confidence expected of a professional Junior Linux System Administrator.

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
| Field | Description |
|---|---|
| Task ID | Unique identifier |
| Title | Engineering Task name |
| Phase | Engineering Phase |
| Priority | High / Medium / Low |
| Dependencies | Required prerequisite tasks |
| Related ADR | Applicable architecture decisions |
| Nemeth | Chapters Required reading |
| Required VMs | Systems required for execution |
| Deliverables | Documentation and implementation outputs |
| Status | Current lifecycle stage |

## Initial Engineering Backlog
| ID | Title | Phase | Depends On |
|---|---|---|---|
| INF-001 | Build Administrative Workstation | Phase 1 | — |
| INF-002 | Deploy Debian Router | Phase 1 | INF-001 |
| NET-001 | Configure Internal Networks | Phase 2 | INF-002 |
| NET-002 | Configure Routing & NAT | Phase 2| NET-001 |
| NET-003 | Validate Packet Flow | Phase 2 | NET-002 |
| NET-004 | Deploy Primary DNS | Phase 3 | NET-003 |
| NET-005 | Deploy Reverse DNS | Phase 3 | NET-004 |
| NET-006 | Deploy Secondary DNS | Phase 3 | NET-005 |
| NET-007 | Implement DHCP | Phase 3 | NET-006 |
| OPS-001 | Configure NTP | Phase 3 | NET-007 |
| SEC-001 | Build Internal Certificate Authority | Phase 5 | NET-006 |
| SEC-002 | Secure Internal Web Services with TLS | Phase 5 | SEC-001 |
| INF-003 | Deploy LDAP Server | Phase 4 | NET-006 |
| INF-004 | Configure NSS, PAM and SSSD | Phase 4 | INF-003 |
| OPS-002 | Deploy Monitoring Stack | Phase 6 | INF-004 |
| OPS-003 | Configure Centralized Logging | Phase 6 | OPS-002 |
| OPS-004 | Implement Backup Strategy | Phase 6 | OPS-003 |
| AUT-001 | Automate Administrative Tasks with Bash | Phase 7 | OPS-004 |
| AUT-002 | Introduce Git for Infrastructure | Phase 7 | AUT-001 |
| AUT-003 | Deploy Ansible | Phase 7 | AUT-002 |
| CNT-001 | Deploy Docker | Phase 8 | AUT-003 |
| CNT-002 | Containerize Internal Services| Phase 8 | CNT-001 |
| CLD-001 | Create AWS Foundation | Phase 9 | CNT-002 |
| CLD-002 | Extend Infrastructure into AWS | Phase 9 | CLD-001 |
| OPS-005 | Production Readiness Assessment | Phase 10| CLD-002 |

## Phase Completion Criteria
A phase is complete only when:
- All Engineering Tasks are completed.
- Documentation is current.
- ADRs are updated.
- Architecture remains consistent.
- The Technical Lead approves progression.
- The learner can explain the rationale behind every major decision.
- Advancing without understanding is not permitted.

## Backlog Maintenance
The backlog is reviewed after every completed Engineering Task.

The Technical Lead determines whether:
- new tasks should be added;
- priorities should change;
- dependencies should be updated;
- new ADRs are required.

The backlog reflects the current state of the infrastructure and the business.

## Guiding Principle
The Engineering Backlog is not a checklist to finish as quickly as possible.
It is the structured development plan for both the Atlas Software Solutions infrastructure and the engineer
responsible for designing, operating and improving it.
Each completed task represents not only a technical implementation but also a measurable step toward
becoming a professional Infrastructure Engineer.

## Engineering Backlog Change History

|Version|Date|Description|
|---|---|---|
|1.0|(original)|Initial backlog|
|1.1|2026-07-13|"Task Status" replaced by "Task Tracking States" per ADR-022: declared a tracking model with authoritative mapping to Chapter 5 §5.2; Blocked formalized as exception flag; two states renamed.|
