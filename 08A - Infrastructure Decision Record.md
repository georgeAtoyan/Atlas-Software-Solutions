## **Chapter 8A — Foundational Architecture Decisions (ADR-001–ADR-020)**

## **Purpose** 

This document records the foundational architectural decisions made before the implementation of the Atlas Software Solutions infrastructure. 

Architecture Decision Records (ADR) provide a permanent history of why important technical decisions were made. 

Every major architectural change throughout this project should be documented using the same format. 

ADR documents are living engineering records. 

They explain not only **what** was chosen, but also **why** . 


## **0. Governance Preamble**

### 0.1 Document Identity

This document was formerly titled "Infrastructure Decision Record (ADR-0)" and was informally referenced as "ADR-000". Those identities are **retired and must not be used**. The correct reference is **Chapter 8A — Foundational Architecture Decisions (ADR-001–ADR-020)**, or "the Foundational ADRs". The identifiers "ADR-0" and "ADR-000" were never allocated to any record and do not exist.

### 0.2 Historical Status

The twenty records in this document (ADR-001 through ADR-020) are the original architectural foundation of the Atlas Software Solutions infrastructure. They were authored **before STD-ADR-001 (Architecture Decision Record Standard) existed** and therefore do not follow its required structure.

These records are **grandfathered as historical records**:

- They remain valid, authoritative decisions unless individually superseded.
- They will **not** be retroactively rewritten to comply with STD-ADR-001. Retroactive rewriting would fabricate reasoning that was not recorded at the time, violating the principle that architectural history must be preserved honestly (STD-ADR-001 Principle 5; STD-LESSONS-001 Principle 1).
- They may receive **status annotations only** (e.g. Superseded), applied per STD-ADR-001 §8 — never changes to their original decision text.

### 0.3 Compliance Rule for New ADRs

**Every ADR from ADR-021 onward must fully comply with STD-ADR-001** and use the approved ADR Template. No new ADR may cite this preamble as precedent for reduced structure.

### 0.4 Identifier Allocation

ADR identifiers are permanent and never reused (STD-ADR-001 §6.1). Identifiers ADR-001 through ADR-020 are consumed by this document. **All identifier allocation is performed exclusively through the ADR Register (ADR-REGISTER.md)**, which records every allocated number, every status, and the next available identifier. Do not derive the next number by inspecting this document or the repository. In any discrepancy, the ADR Register prevails.

## **ADR-001** 

## **Title** 

Segmented Network Architecture 

## **Status** 

Accepted 

## **Context** 

The infrastructure will continue growing throughout multiple project phases. 

A single flat network would eventually require significant redesign. 

## **Decision** 

The infrastructure will be divided into multiple logical network segments from the beginning. 

Initial segments include: 

- Management • Server • Client 

A DMZ network will be introduced when public-facing services become necessary. 

## **Rationale** 

This design supports long-term scalability while introducing realistic networking concepts early. 

## **Alternatives Considered** 

Single flat LAN. 

Rejected because future infrastructure growth would require disruptive redesign. 

## **Consequences** 

Routing becomes part of the infrastructure from the beginning. 

Future network expansion becomes straightforward. 

## **ADR-002** 

## **Title** 

Dedicated Router Virtual Machine 

## **Status** 

Accepted 

## **Context** 

VirtualBox NAT provides Internet connectivity but hides many important networking concepts. 

## **Decision** 

Deploy a dedicated Debian Router virtual machine responsible for: 

- packet forwarding 

- routing 

- firewalling
  
- NAT 

- future VPN services 

- future DHCP services 

## **Rationale** 

A dedicated router provides significantly better visibility into networking and mirrors real-world infrastructure. 

## **Alternatives Considered** 

VirtualBox NAT only. 

Rejected due to limited educational value. 

## **Consequences** 

One additional virtual machine is required. 

Networking becomes significantly more realistic. 

## **ADR-003** 

## **Title** 

Internal DNS Namespace 

## **Status** 

Accepted 

## **Context** 

The project requires a consistent internal naming convention. 

## **Decision** 

The internal domain shall be: 

atlas.lab 

## **Rationale** 

The namespace reflects the fictional company and remains isolated from public DNS. 
 
## **Alternatives Considered** 

company.lab 

atlas.local corp.local 

## **Consequences** 

Every internal service will use this namespace. 

Examples: 

srv-dns-01.atlas.lab 

srv-web-01.atlas.lab 

srv-git-01.atlas.lab 

## **ADR-004** 

## **Title** 

Server Naming Convention 

## **Status** 

Accepted 

## **Decision** 

Servers follow the convention: 

srv-<role>-<number> 

Examples: srv-dns-01 

srv-web-01 

srv-ca-01 

srv-git-01 srv-monitor-01 Workstations: 

cli-admin-01 cli-dev-01 Network devices: rtr-edge-01 Future switches: 

sw-core-01 

## **Rationale** 

Consistent naming improves readability and scalability. 

## **Consequences** 

Every infrastructure component follows predictable naming. 

## **ADR-005** 

> **⚠ Supersession Notice (2026-07-13):** This record is **superseded by ADR-021**. The ranges below must not be used for any allocation. The single authoritative IP Address Allocation Policy is **Infrastructure Architecture (Chapter 8B), Section 8**. Reason: the ranges below conflict with Chapter 8B §8 (audit finding AUD-C-01). Operational impact: none — no deployed system was addressed under these ranges. The original decision text is preserved unmodified below per STD-ADR-001 §8.

## **Title** 

Static Address Planning 

## **Status** 

**Superseded** — Superseded by ADR-021 (2026-07-13). Original status: Accepted.

## **Decision** 

IP addresses are reserved by functional ranges. 

Infrastructure 

10–19 

Network Services 

20–39 

Application Servers 

40–59 

Client Systems 

60–79 

Temporary Systems 

80–99 

Future Expansion 

100–199 

## **Rationale** 

Predictable addressing simplifies troubleshooting and documentation. 

## **ADR-006** 

## **Title** 

Service Isolation 

## **Status** 

Accepted 

## **Context** 

Each major infrastructure service represents an independent responsibility. 

## **Decision** 

Every major service receives its own virtual machine. 
 
## **Rationale** 

Isolation simplifies troubleshooting, documentation and future migration. 

## **Alternatives Considered** 

Multiple services per server. 

Rejected for educational clarity. 

## **Consequences** 

Higher RAM usage. 

Much cleaner architecture. 

## **ADR-007** 

## **Title** 

Operating System Strategy 

## **Status** 

Accepted 

## **Decision** 

The infrastructure will intentionally use both Debian Stable and Ubuntu Server LTS. 

Debian Stable will host conservative infrastructure services such as routing, DNS, PKI and directory services. 

Ubuntu Server LTS will host application-oriented services such as Git, monitoring and future CI/CD components. 

Ubuntu Desktop will be used as the primary administrative workstation. 

## **Rationale** 

This reflects common enterprise environments and broadens operational experience without introducing unnecessary complexity. 

## **Consequences** 

The learner gains practical familiarity with both Debian-based distributions while recognizing that core Linux administration principles remain consistent. 

## **ADR-008** 

## **Title** 

Incremental Infrastructure Growth 

## **Status** 

Accepted 

## **Decision** 

Virtual machines are created only when business requirements justify their existence. 

## **Rationale** 

Infrastructure should evolve naturally. 

Unused services increase operational complexity. 

## **ADR-009** 

## **Title** 

Identity Management Strategy 

## **Status** 

Accepted 

## **Decision** 

Local Linux accounts are used initially. 

Centralized identity management will be introduced only when business growth requires it. 

## **Rationale** 

The learner must first understand local account management before introducing LDAP, SSSD and PAM. 

## **ADR-010** 

## **Title** 

Certificate Strategy 

## **Status** 

Accepted 

## **Decision** 

Internal services will use an Internal Certificate Authority. 

## **Rationale** 

The project emphasizes understanding PKI concepts rather than relying on publicly issued certificates. 

## **ADR-011** 

## **Title** 

Repository Strategy 

## **Status** 

Accepted 

## **Decision** 

Maintain a dedicated Infrastructure Repository alongside separate repositories for future application projects. 

## **Rationale** 

Separating infrastructure from application code reflects professional engineering practice and keeps responsibilities clear. 


## **ADR-012** 

## **Title** 

Documentation Standard 

## **Status** 

Accepted 

## **Decision** 

Every engineering task must produce: 

- README 

- Architecture Diagram 

- ADR (when applicable) 

- Runbook • Verification Notes 

- Lessons Learned 

## **Rationale** 

Documentation is considered part of the engineering deliverable. 

## **ADR-013** 

## **Title** 

Diagram Standard 

## **Status** 

Accepted 

## **Decision** 

draw.io is the primary tool for infrastructure diagrams. 

Mermaid diagrams may be used for lightweight documentation within Markdown. 

## **Rationale** 

draw.io provides flexibility for detailed architecture diagrams, while Mermaid integrates well with repository documentation. 

## **ADR-014** 

## **Title** 

Backup Philosophy 

## **Status** 

Accepted 

## **Decision** 

Backup strategies will be introduced from the Foundation Phase onward. 

Backups are treated as a core operational responsibility rather than an optional enhancement. 

## **Rationale** 

Operational resilience begins with recoverability. 

## **ADR-015** 

## **Title** 

Logging Strategy 

## **Status** 

Accepted 

## **Decision** 

Native system logging is used initially. 

Centralized logging will be introduced as infrastructure complexity increases. 

## **Rationale** 

The learner should first understand local log analysis before adopting centralized logging platforms. 

## **ADR-016** 

## **Title** 

Monitoring Strategy 

## **Status** 

Accepted 

## **Decision** 

Monitoring will be introduced after multiple infrastructure services are operational. 

The monitoring stack will consist of Prometheus and Grafana. 

## **Rationale** 

Monitoring should observe an existing infrastructure rather than an empty one. 

## **ADR-017** 

## **Title** 

Security by Design 

## **Status** 

Accepted 

## **Decision** 

Security controls are integrated into every engineering task from the beginning. 

Examples include least privilege, SSH hardening, firewall configuration, certificate management and secure service configuration. 

## **Rationale** 

Security is an architectural property, not a later enhancement. 

## **ADR-018** 

## **Title** 

Automation Philosophy 

## **Status** 

Accepted 

## **Decision** 

Manual administration must be mastered before introducing automation. 

Configuration management tools will only appear after manual processes are fully understood. 

## **Rationale** 

Automation should amplify competence rather than compensate for missing fundamentals. 

## **ADR-019** 

## **Title** 

Cloud Adoption Strategy 

## **Status** 

Accepted 

## **Decision** 

The Foundation Project remains on-premises using VirtualBox. 

Cloud technologies will be introduced after the learner demonstrates confidence with core Linux administration and infrastructure concepts. 

AWS will serve as the primary cloud platform for future phases. 

## **Rationale** 

Strong infrastructure fundamentals transfer naturally to cloud environments. 

## **ADR-020** 

## **Title** 

Infrastructure Philosophy 

## **Status** 

Accepted 

## **Decision** 

Architectural decisions prioritize clarity, maintainability and operational understanding over adopting the newest technologies. 

## **Rationale** 

The objective is to develop a strong Infrastructure Engineer rather than to maximize the number of technologies used. 

## **ADR Governance** 

All future architectural decisions shall follow the same ADR structure. 

Existing ADRs should never be modified without documenting: 

- the reason for change; 

- the new decision; 

- the operational impact; 

- the migration strategy. 

Architectural history is considered valuable engineering knowledge. 

## **Final Statement** 

A well-designed infrastructure is not the result of installing many technologies. 

It is the result of making a series of deliberate, documented and well-reasoned engineering decisions. 

This ADR establishes the architectural foundation upon which every future Engineering Task in the Atlas Software Solutions project will be built. 


## **Chapter 8A Change History**

|Version|Date|Description|
|---|---|---|
|1.0|(original)|Initial foundational decisions ADR-001–ADR-020|
|1.1|2026-07-13|Retitled per AUD-C-04; identities "ADR-0"/"ADR-000" retired; Section 0 (Governance Preamble) added: grandfathered status, compliance rule for ADR-021+, allocation via ADR Register. ADR-005 status annotated Superseded by ADR-021 (AUD-C-01). Records otherwise unmodified.|
