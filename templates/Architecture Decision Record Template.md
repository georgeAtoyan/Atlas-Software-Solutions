

Architecture Decision Record (ADR) Template
## Instructions
This template shall be used for every significant architectural decision within the Atlas
## Software Solutions Engineering Blueprint.
Replace all placeholder text enclosed in < >.
Remove instructional notes before final publication.
Follow STD-ADR-001 (Architecture Decision Record Standard) when completing this
document.
Obtain the ADR identifier from the ADR Register (ADR-REGISTER.md) and update the Register in the same commit. Do not choose a number manually.
ADR-<XXX> — <Decision Title>
## Status: Proposed | Accepted | Superseded | Deprecated | Rejected
Date: YYYY-MM-DD
Author: <Infrastructure Engineer>
Reviewer: <Technical Lead>
## 1. Context
## Background
Describe the engineering or business context that led to this decision.
## Explain:
What problem exists?
Why must a decision be made now?
Which Engineering Task or project phase introduced this requirement?
This section should describe the situation—not the solution.
## •
## •
## •
## 1

## 2. Problem Statement
Clearly define the architectural problem.
A good problem statement should answer:
What engineering challenge are we solving?
What constraints exist?
What risks are involved?
## 3. Decision
State the approved architectural decision clearly and unambiguously.
Avoid implementation details.
The decision should be understandable in isolation.
## 4. Alternatives Considered
Describe the realistic alternatives evaluated before making the decision.
For each alternative include:
Alternative A — <Name>
## Advantages
<Advantage>
<Advantage>
## Disadvantages
<Disadvantage>
<Disadvantage>
Reason for Rejection
Explain why this alternative was not selected.
## •
## •
## •
## •
## •
## •
## •
## 2

Alternative B — <Name>
## Advantages
<Advantage>
## Disadvantages
<Disadvantage>
Reason for Rejection
<Explanation>
(Add additional alternatives as required.)
## 5. Rationale
Explain why the selected decision best satisfies the engineering objectives.
## Reference:
## Engineering Principles;
business requirements;
infrastructure constraints;
scalability;
maintainability;
operational simplicity.
This section is the heart of the ADR.
Future engineers should understand why this decision was made.
## 6. Consequences
Describe the expected consequences of this decision.
Include both positive and negative effects.
## Positive Consequences
<Benefit>
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

<Benefit>
## Negative Consequences
<Trade-off>
<Trade-off>
## Operational Impact
Describe how the decision affects day-to-day operations.
## Future Impact
Describe how the decision influences future Engineering Tasks or infrastructure growth.
## 7. Risks
Identify the risks associated with this decision.
For each risk include:
RiskImpactMitigation
<Risk>Low / Medium / High<Mitigation>
## 8. Implementation Notes
(Optional)
Provide implementation guidance if necessary.
Do not duplicate Runbook procedures.
Reference the appropriate Engineering Task where possible.
## 9. Related Documents
List all relevant documentation.
## •
## •
## •
## 4

## Examples:
## Engineering Task
## README
## Runbook
## Verification Notes
## Architecture Diagram
Related ADRs
## Infrastructure Architecture
## Engineering Principles
## 10. Review History
VersionDateDescription
1.0YYYY-MM-DDInitial decision
## 11. Supersession
If this ADR replaces or is replaced by another ADR, document it here.
## Supersedes
## ADR-<XXX>
or
## None
## Superseded By
## ADR-<YYY>
or
## N/A
## •
## •
## •
## •
## •
## •
## •
## •
## 5

## 12. Approval
RoleNameDate
Infrastructure Engineer<Name>YYYY-MM-DD
Technical Lead<Name>YYYY-MM-DD
ADR Summary
FieldValue
## ADR IDADR-<XXX>
Decision<Short Decision Title>
Status<Status>
## Primary Area
## Networking / Security / Infrastructure / Virtualization / Documentation /
## Monitoring / Automation / Cloud
## Related Engineering
## Task
## <INF-001 / NET-004 / OPS-001>
Review DateYYYY-MM-DD
## 6

## Template Change History

|Version|Date|Description|
|---|---|---|
|1.0|(original)|Initial template|
|1.1|2026-07-13|Instruction added: identifier allocation via ADR Register (AUD-C-04).|
