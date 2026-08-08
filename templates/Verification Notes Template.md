

## Verification Notes Template
## Instructions
This template shall be used to document the verification of every completed Engineering
## Task.
Replace all placeholder text enclosed in < >.
Remove instructional notes before final publication.
Follow STD-VERIFY-001 (Verification Standard) when completing this document.
Verification Notes — <System Name>
Engineering Task: <INF-001 / NET-004 / OPS-001>
## Version: 1.0
## Status: Draft | Approved
Verification Date: YYYY-MM-DD
Verified By: <Infrastructure Engineer>
Reviewed By: <Technical Lead>
## 1. Verification Summary
Provide a brief description of what is being verified.
## Include:
engineering task;
infrastructure component;
verification objective.
## •
## •
## •
## 1

## 2. Success Criteria
List every approved Success Criterion.
IDSuccess CriterionStatus
SC-01<Criterion>Pass / Fail
SC-02<Criterion>Pass / Fail
SC-03<Criterion>Pass / Fail
No Success Criterion should remain unverified.
## 3. Verification Procedure
Document how each Success Criterion was verified.
Success CriterionVerification MethodExpected Result
SC-01<Command / Test><Expected Result>
SC-02<Command / Test><Expected Result>
## 4. Verification Evidence
Provide objective evidence.
For each verification include:
Verification 1 — <Title>
## Objective
<What is being verified?>
## Command / Method
## <command>
## 2

## Observed Result
<terminal output>
## Conclusion
## Pass / Fail
Brief explanation.
Verification 2 — <Title>
## Objective
<Description>
## Command / Method
## <command>
## Observed Result
<terminal output>
## Conclusion
## Pass / Fail
(Add additional verification sections as required.)
## 5. Functional Testing
Document practical operational tests.
## Examples:
system boots successfully;
network connectivity;
## •
## •
## 3

internet access;
service communication;
DNS resolution;
SSH connectivity;
package installation;
application functionality.
TestExpected ResultActual ResultStatus
<Test><Expected><Observed>Pass / Fail
## 6. Reboot Validation
Perform a complete reboot.
Repeat all critical verification steps.
VerificationResult After Reboot
HostnamePass / Fail
NetworkPass / Fail
ServicesPass / Fail
ConnectivityPass / Fail
Security ConfigurationPass / Fail
Document any differences observed after reboot.
## 7. Deviations
Describe any deviations from expected behavior.
For each deviation include:
DeviationImpactResolutionStatus
<Issue>Low / Medium / High<Resolution>Open / Closed
If no deviations exist, state:
No deviations were identified during verification.
## •
## •
## •
## •
## •
## •
## 4

## 8. Verification Summary
Summarize the overall outcome.
Example topics:
implementation completeness;
outstanding issues;
readiness for production (or next Engineering Task).
## 9. Acceptance Decision
Select one:
## ✅ Passed
⚠ Passed with Observations
## ❌ Failed
Provide a short justification.
## 10. Related Documentation
Reference associated engineering documentation.
## README
## Runbook
## Architecture Diagram
## ADR
## Lessons Learned
## Engineering Task
## 11. Change History
VersionDateDescription
1.0YYYY-MM-DDInitial version
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

## Approval
RoleNameDate
Infrastructure Engineer<Name>YYYY-MM-DD
Technical Lead<Name>YYYY-MM-DD
## 6