

README Standard
Document ID: STD-README-001
## Version: 1.0
## Status: Approved
## 1. Purpose
The README is the primary entry point for every Engineering Task and infrastructure component.
Its purpose is to provide engineers with a concise but complete overview of the system without requiring
them to read implementation procedures or configuration files.
A reader should understand the purpose, role and current state of the system within five minutes.
## 2. Scope
This standard applies to all infrastructure components maintained by Atlas Software Solutions, including
but not limited to:
## Virtual Machines
## Network Services
## Infrastructure Projects
## Automation Projects
## Security Components
## Monitoring Systems
## Cloud Resources
Every Engineering Task must produce a README unless explicitly exempted by the Technical Lead.
## 3. Engineering Objectives
A README must answer the following questions:
What is this system?
Why does it exist?
What business problem does it solve?
What role does it play within the infrastructure?
What technologies are used?
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

What documentation should be read next?
If a reader cannot answer these questions after reading the README, the document is incomplete.
## 4. Design Principles
Principle 1 — High-Level Overview
The README introduces the system.
It does not teach how to build or operate it.
Principle 2 — Concise but Complete
The README should contain enough information to understand the system, but should avoid
implementation details.
## Principle 3 — Architecture Before Configuration
The README explains architectural purpose before discussing technical characteristics.
Readers should understand why the component exists before learning how it is implemented.
Principle 4 — Single Source of Overview
The README serves as the authoritative overview document.
Detailed information belongs in specialized documents such as Runbooks or ADRs.
## 5. Required Structure
Every README should contain the following sections.
## 5.1 Purpose
Describe the business objective of the system.
## •
## 2

Explain why the component exists.
## 5.2 Business Role
Explain how the system supports Atlas Software Solutions.
Focus on business functionality rather than technical implementation.
## 5.3 Architectural Role
Describe how the component interacts with the rest of the infrastructure.
## Include:
dependencies;
upstream systems;
downstream systems;
communication paths.
## 5.4 Current Status
Describe the implementation status.
## Examples:
## Planned
## In Progress
## Operational
## Under Maintenance
## Deprecated
## 5.5 Technical Specifications
Summarize the technical characteristics.
Typical information includes:
## Operating System
## Version
## CPU
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

## Memory
## Disk
## Virtualization Platform
## Hostname
VM Name
Only include information relevant for understanding the system.
## 5.6 Network Overview
Provide a high-level description of networking.
Examples include:
current network location;
target architecture;
addressing plan;
major network dependencies.
Detailed configuration belongs in the Runbook.
## 5.7 Installed Software
List the major software components.
Each item must include a short justification explaining why it exists.
## Example:
SoftwarePurpose
GitVersion control
Visual Studio CodeDocumentation and configuration editing
FirefoxAccess to engineering resources
Avoid listing default operating system packages.
## 5.8 Security Overview
Summarize important security decisions.
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

## Examples:
encryption;
authentication model;
firewall philosophy;
SSH policy;
privileged access model.
Do not include sensitive information such as passwords or cryptographic keys.
## 5.9 Dependencies
List infrastructure dependencies.
## Examples:
## DNS
## DHCP
## NTP
## LDAP
Internet access
## 5.10 Related Documentation
Reference additional documentation.
Typical references include:
## Runbook
## ADR
## Verification Notes
## Architecture Diagram
## Engineering Task
## Related Engineering Tasks
The README should serve as the entry point to the complete documentation set.
- Information That MUST NOT Appear
The README must not contain:
installation instructions;
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
## •
## •
## 5

command sequences;
troubleshooting procedures;
configuration file contents;
lengthy terminal output;
verification evidence;
temporary implementation notes.
These belong in other documentation.
## 7. Writing Guidelines
The README should:
use clear engineering language;
explain terminology where appropriate;
avoid unnecessary jargon;
remain concise;
focus on architecture rather than implementation;
remain understandable by engineers unfamiliar with the project.
## 8. Review Checklist
Before approval, verify that the README answers:
What is this system?
Why does it exist?
Where does it fit?
What are its main characteristics?
What software does it contain?
What security decisions are relevant?
Which documents should be consulted next?
If any answer is missing, the README requires revision.
- Definition of Done
A README is considered complete when:
all required sections are present;
architectural purpose is clearly explained;
technical specifications are accurate;
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
## •
## •
## •
## •
## •
## •
## •
## 6

software is justified;
related documentation is referenced;
no implementation procedures are included;
the document has been reviewed and approved by the Technical Lead.
The README becomes the permanent overview document for the infrastructure component throughout its
lifecycle.
## •
## •
## •
## •
## 7