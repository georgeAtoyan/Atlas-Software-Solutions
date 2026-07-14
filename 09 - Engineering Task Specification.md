

Engineering Task Specification (ETS)
## Purpose
The Engineering Task Specification (ETS) defines the standard structure for every engineering activity
performed throughout the Atlas Software Solutions project.
Every task, regardless of complexity, follows this specification.
The objective is to ensure consistency, traceability and professional engineering discipline.
A task is not considered complete until every required section has been addressed.
## Engineering Task Lifecycle
Every Engineering Task follows the **canonical Engineering Lifecycle defined in Chapter 5 (Engineering Workflow), Section 5.2**. That section is the sole authoritative definition (ADR-022); this specification does not redefine it.

Skipping lifecycle stages is not permitted (Chapter 5 §5.2).

The former ETS lifecycle stage "Task Assignment" is not an engineering stage; it is the administrative transition of a task into active work, represented by the **Ready** tracking state in the Engineering Backlog.

### ETS Section-to-Lifecycle Mapping

The sections of the Engineering Task document are the written record of the lifecycle stages:

|Lifecycle Stage (Ch. 5 §5.2)|ETS Sections Produced|
|---|---|
|1. Business Requirement|§2 Business Requirement|
|2. Problem Analysis|§3 Problem Statement|
|3. Infrastructure Assessment|§4 Current Environment|
|4. Research & Theory|§7 Technical Research, §8 Required Reading|
|5. Architecture Discussion|§10 Alternative Solutions|
|6. Design Proposal|§5 Success Criteria, §6 Constraints, §9 Proposed Solution, §12 Implementation Plan, §13 Verification Plan, §14 Risk Assessment, §15 Rollback Plan|
|7. Design Review & Approval|§11 Architecture Review|
|8. Implementation|§16 Implementation Notes|
|9. Verification|§17 Verification Results (+ Verification Notes per STD-VERIFY-001)|
|10. Documentation|§18 Documentation Deliverables|
|11. Post-Implementation Review & Lessons Learned|§19 Operational Review, §20 Lessons Learned, §21 Future Improvements|
|12. Task Closure|§22 Task Closure Checklist|

Section §1 (Task Information) is administrative metadata maintained throughout the task. A task is not complete until every stage has been performed and its corresponding sections are complete.
## Task Identification
Every task receives a unique identifier.
## Examples:
## INF-001
## NET-003
## SEC-007
## OPS-011
## DOC-004
## ARC-002
## AUT-001
## INC-005
## CHG-003
## CLD-001
Identifiers remain permanent.
## Engineering Task Template
## 2

## 1. Task Information
Task ID
## Title
## Category
## Priority
## Status
## Assigned Engineer
## Technical Lead
## Estimated Duration
## Creation Date
## Completion Date
Related ADRs
## Related Engineering Tasks
## 2. Business Requirement
Describe the business need.
## Examples:
Developers require reliable internal name resolution.
System administrators require centralized authentication.
Certificates must be trusted internally.
The requirement should be written from the business perspective rather than the technical perspective.
## 3

## 3. Problem Statement
Define the current problem.
Questions include:
What is happening?
Why is it a problem?
Who is affected?
What are the operational consequences?
How urgent is the issue?
The problem must be understood before discussing solutions.
## 4. Current Environment
Describe the existing infrastructure.
## Include:
Current topology
Relevant services
## Dependencies
Known limitations
Existing risks
The objective is to understand the starting point.
## 5. Success Criteria
Clearly define what constitutes a successful implementation.
Success criteria must be measurable.
## 4

## Examples:
Internal DNS resolves successfully.
Clients authenticate correctly.
HTTPS functions without certificate warnings.
Configuration survives reboot.
Documentation is complete.
## 6. Constraints
Identify project constraints.
## Examples:
Available hardware
Available RAM
Maintenance window
Security requirements
Budget limitations
Operational complexity
Every design decision must respect these constraints.
## 7. Technical Research
Document the theory required before implementation.
## Include:
## Protocols
## Standards
## 5

## Architecture
## Terminology
Internal mechanisms
No implementation begins before the necessary concepts are understood.
## 8. Required Reading
Reference the chapters from the Linux Administration Handbook and any other approved resources that
support the task.
The purpose is to connect engineering work with foundational theory.
## 9. Proposed Solution
Describe the intended solution.
## Include:
Architecture overview
## Components
Configuration approach
Expected workflow
## Reasoning
The proposal should explain why this solution is appropriate.
## 10. Alternative Solutions
Identify alternative approaches.
For each alternative explain:
## Advantages
## 6

## Disadvantages
Reason for rejection
Engineering decisions require comparison.
## 11. Architecture Review
The Technical Lead evaluates the proposal.
Typical questions include:
Does the design solve the business problem?
Can it be simplified?
Is security sufficient?
Are unnecessary dependencies introduced?
Does it align with existing ADRs?
## Outcome:
## Approved
Approved with recommendations
Requires redesign
## 12. Implementation Plan
Implementation should be divided into logical steps.
Each step should have a clear objective.
The plan should minimize operational risk.
## 13. Verification Plan
Before implementation, define how success will be verified.
## 7

## Examples:
dig
curl
ping
systemctl
journalctl
ss
tcpdump
Automated tests
Verification should rely on observable evidence.
## 14. Risk Assessment
Identify potential risks.
## Examples:
Service outage
Configuration errors
Security exposure
DNS propagation problems
Rollback difficulties
Each risk should include a mitigation strategy.
## 15. Rollback Plan
Every significant change requires a rollback procedure.
## 8

The rollback plan should answer:
How can the previous state be restored?
What backups are required?
What verification confirms successful rollback?
Recovery planning is part of implementation planning.
## 16. Implementation Notes
## Record:
Commands executed
Configuration files modified
Unexpected observations
Problems encountered
Engineering decisions made during implementation
These notes become valuable operational knowledge.
## 17. Verification Results
Record objective evidence.
## Examples:
Command output
Screenshots (when appropriate)
Log excerpts
Network traces
Service status
## 9

The implementation is accepted only after successful verification.
## 18. Documentation Deliverables
Every completed task updates:
## README
## Runbook
## Architecture Diagram
## Configuration Documentation
ADR (if required)
## Lessons Learned
## Repository Index
Documentation is part of the deliverable.
## 19. Operational Review
Evaluate the implementation.
Questions include:
Was the original problem solved?
Were all success criteria met?
Did new risks appear?
Can the solution be simplified?
Should monitoring be added?
Should automation be considered later?
## 10

## 20. Lessons Learned
Summarize key observations.
## Include:
Technical knowledge gained
Operational improvements
Common mistakes
Unexpected behavior
Future recommendations
Lessons learned are intended to improve future Engineering Tasks.
## 21. Future Improvements
Identify opportunities for future enhancement.
## Examples:
## Automation
## Monitoring
Security improvements
Performance optimization
Documentation updates
Future Engineering Tasks may originate from this section.
## 22. Task Closure Checklist
A task may only be closed when all items below are complete.
✓ Business requirement satisfied
## 11

✓ Technical solution implemented
✓ Verification completed
✓ Risks reviewed
✓ Documentation updated
✓ Architecture reviewed
✓ ADR updated (if applicable)
✓ Lessons Learned documented
✓ Technical Lead approval obtained
## Engineering Task Categories
PrefixCategoryDescription
INFInfrastructureCore infrastructure implementation
NETNetworkingRouting, DNS, switching, addressing
SECSecurityHardening, PKI, access control
OPSOperationsBackups, monitoring, maintenance
DOCDocumentationDocumentation improvements and standards
ARCArchitectureArchitectural reviews and design changes
CHGChangePlanned infrastructure modifications
INCIncidentIncident response and troubleshooting
AUTAutomationConfiguration management and scripting
CLDCloudAWS and hybrid cloud tasks
Additional categories may be introduced as the infrastructure evolves.
## 12

## Technical Lead Responsibilities
For every Engineering Task, the Technical Lead shall:
validate the business requirement;
verify prerequisite knowledge;
review the proposed solution;
challenge assumptions;
ensure alignment with existing ADRs;
approve implementation before execution;
review documentation;
conduct the post-implementation review;
approve task closure.
The Technical Lead is responsible for the quality of the engineering process, not for writing the
implementation.
## Learner Responsibilities
For every Engineering Task, the learner shall:
understand the business requirement;
study the necessary theory;
prepare a design proposal;
implement the approved solution;
verify functionality using objective evidence;
document the implementation;
reflect on lessons learned;
seek understanding rather than completion.
## Engineering Quality Principles
Every completed task should improve one or more of the following:
## Reliability
## Security
## Maintainability
## Observability
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
## 13

## Recoverability
## Scalability
## Operational Simplicity
If none of these qualities improve, the value of the task should be questioned.
## Final Principle
An Engineering Task is not a checklist of commands.
It is a structured engineering process that begins with understanding a business problem and ends with a
documented, verified and maintainable solution.
The quality of an engineer is reflected not only in the systems they build, but in the discipline with which
they design, implement, verify and document them.
## 14

## ETS Change History

|Version|Date|Description|
|---|---|---|
|1.0|(original)|Initial specification|
|1.1|2026-07-13|Independent lifecycle definition removed; replaced with reference to the canonical lifecycle (Chapter 5 §5.2, per ADR-022) and a section-to-stage mapping. "Task Assignment" reclassified as the Ready tracking state.|
