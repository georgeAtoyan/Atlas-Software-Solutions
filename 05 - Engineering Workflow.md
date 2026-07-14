## **Chapter 5 — Engineering Workflow** 

## **5.1 Purpose** 

This chapter defines the standard engineering workflow used throughout the project. 

Every infrastructure change, regardless of size or complexity, follows the same structured process. 

The objective is to develop engineering discipline rather than simply complete laboratory exercises. 

Consistency is more valuable than speed. 

## **5.2 The Engineering Lifecycle**

> **Authority Note (ADR-022):** This section is the **single canonical definition of the Engineering Lifecycle** for the Atlas Software Solutions Engineering Blueprint. No other document may define, redraw, or restate the lifecycle; other documents reference this section. Simplified task-status vocabularies (e.g. the Engineering Backlog Task Tracking States) are workflow tracking models, not lifecycle definitions, and must map to these stages. Changes to this lifecycle require a new Architecture Decision Record.

Every Engineering Task, regardless of size or complexity, follows the twelve stages below, in order.

```
 1. Business Requirement
        │
        ▼
 2. Problem Analysis
        │
        ▼
 3. Infrastructure Assessment
        │
        ▼
 4. Research & Theory
        │
        ▼
 5. Architecture Discussion
        │
        ▼
 6. Design Proposal
        │
        ▼
 7. Design Review & Approval
        │
        ▼
 8. Implementation
        │
        ▼
 9. Verification
        │
        ▼
10. Documentation
        │
        ▼
11. Post-Implementation Review & Lessons Learned
        │
        ▼
12. Task Closure
```

No stage may be skipped.

### Stage Definitions

|#|Stage|Purpose|Detailed in|
|---|---|---|---|
|1|Business Requirement|The business problem that initiates the task|§5.3|
|2|Problem Analysis|Understand the problem before proposing solutions|§5.4|
|3|Infrastructure Assessment|Analyze the current environment and dependencies|§5.5|
|4|Research & Theory|Study the concepts required to solve the problem|§5.6|
|5|Architecture Discussion|Explore solution categories, assumptions, trade-offs|§5.7|
|6|Design Proposal|Produce a written engineering proposal|§5.8|
|7|Design Review & Approval|Technical Lead reviews and approves the design before implementation|§5.9|
|8|Implementation|Execute the approved design|§5.10|
|9|Verification|Prove the implementation meets the Success Criteria (STD-VERIFY-001)|§5.11|
|10|Documentation|Produce the required documentation deliverables (Chapter 11 standards)|§5.12|
|11|Post-Implementation Review & Lessons Learned|Reflect on the outcome; capture engineering knowledge (STD-LESSONS-001)|§5.13|
|12|Task Closure|Confirm exit criteria and formally close the task|§5.16|

### Naming Notes

Stage 7 is named **Design Review & Approval** (formerly "Technical Review") to distinguish it unambiguously from the post-implementation review in Stage 11. Stage 9 is named **Verification**, aligning with STD-VERIFY-001. Stage 11 explicitly includes **Lessons Learned**. Stage 12 formalizes the exit criteria of §5.16 as a lifecycle stage. The informal "Engineering Workflow Summary" at the end of this chapter is a **mnemonic only**; it is not a lifecycle definition and must never be cited as one.

## **5.3 Stage 1 — Business Requirement** 

Every engineering task begins with a business requirement. 

Examples: 

Developers need an internal Git server. 

Internal websites require HTTPS. 

User management has become difficult. 

Deployments consume too much time. 

The business requirement defines the problem. 

Technology is not discussed at this stage. 

## **5.4 Stage 2 — Problem Analysis** 

The learner must first understand the problem. 

Questions include: 

- What is happening? 

- Why is it becoming a problem? 

- Who is affected? 

- What are the operational risks? 

- What happens if nothing changes? 

No solutions should be proposed until the problem is fully understood. 

2 

## **5.5 Stage 3 — Infrastructure Assessment** 

The current environment is analyzed. 

Questions include: 

- Which systems are involved? 

- Which services already exist? 

- What dependencies must be considered? 

- Which components may be affected? 

Engineering decisions must always consider the entire infrastructure. 

## **5.6 Stage 4 — Research & Learning** 

Only after understanding the problem does formal learning begin. 

This stage includes: 

Reading the required chapters from the Linux Administration Handbook. 

Studying protocols. 

Reviewing architecture diagrams. 

Understanding terminology. 

Learning how the technology operates internally. 

Theory is always connected to an active engineering problem. 

## **5.7 Stage 5 — Architecture Discussion** 

This stage represents the mentoring process. 

The Technical Lead begins asking questions. 

Examples: 

Which categories of solutions exist? 

3 

What are the advantages of each? 

What assumptions are being made? 

What dependencies will be introduced? 

What security concerns exist? 

What would happen if this service becomes unavailable? 

The objective is reasoning—not correctness. 

Mistakes are expected. 

Discussion is encouraged. 

## **5.8 Stage 6 — Design Proposal** 

The learner prepares an engineering proposal. 

The proposal should include: 

Objective 

Problem Statement 

Requirements 

Proposed Architecture 

Alternative Solutions 

Advantages 

Disadvantages 

Risks 

Verification Plan 

Documentation Plan 

The proposal does not need to be perfect. 

4 

Its purpose is developing engineering thinking. 

## **5.9 Stage 7 — Design Review & Approval**

The Technical Lead reviews the proposal. 

Possible outcomes include: 

Approved. 

Approved with recommendations. 

Requires redesign. 

The review focuses on engineering quality rather than implementation details. 

Questions may include: 

Can this design be simplified? 

Is every component necessary? 

Does the design introduce unnecessary complexity? 

Is security considered? 

Is documentation sufficient? 

Only after approval does implementation begin. 

## **5.10 Stage 8 — Implementation** 

Implementation follows the approved design. 

The learner performs: 

Installation. 

Configuration. 

Testing. 

5 

Troubleshooting. 

Incremental verification. 

No configuration should be copied without understanding its purpose. 

Every configuration file should be explainable. 

## **5.11 Stage 9 — Verification**

Verification is mandatory. 

The learner confirms: 

The service functions correctly. 

Dependencies remain operational. 

Logs contain no unexpected errors. 

Security requirements are satisfied. 

The failure scenario has been considered. 

Verification is based on evidence—not assumptions. 

## **5.12 Stage 10 — Documentation** 

Documentation is created immediately after implementation. 

Every service should include: 

Purpose 

Architecture 

Configuration 

Network Information 

Dependencies 

6 

Verification Procedure 

Troubleshooting 

Lessons Learned 

Future Improvements 

Documentation should allow another engineer to understand the system without verbal explanation. 

## **5.13 Stage 11 — Post-Implementation Review** 

Every completed project ends with an engineering review. 

Questions include: 

Was the original problem solved? 

Was the selected solution appropriate? 

Could the implementation be simplified? 

Which new dependencies appeared? 

Which operational risks remain? 

Would this design still work if the company doubled in size? 

Reflection transforms experience into engineering knowledge. 

## **5.14 Technical Lead Workflow** 

The Technical Lead follows the same mentoring procedure throughout the project. 

1. Present the business problem. 

2. Confirm the learner understands the problem. 

3. Recommend theory only when necessary. 

4. Encourage independent analysis. 

7 

5. Challenge assumptions. 

6. Review proposed architecture. 

7. Approve implementation. 

8. Review documentation. 

9. Conduct post-implementation discussion. 

The Technical Lead should gradually reduce guidance as the learner gains experience. 

## **5.15 Learner Workflow** 

For every engineering task the learner should: 

Understand the business need. 

Analyze the current infrastructure. 

Study the required concepts. 

Design a solution. 

Discuss architecture. 

Implement carefully. 

Verify objectively. 

Document professionally. 

Review critically. 

Learning occurs through repetition of this process. 

## **5.16 Exit Criteria** 

An engineering task is considered complete only when: 

✓ The business requirement has been satisfied. 

8 

✓ The implementation works correctly. 

✓ Verification has been completed. 

✓ Documentation is complete. 

✓ The learner can explain every architectural decision. 

✓ The Technical Lead approves the implementation. 

Completion is measured by understanding—not by finishing commands. 

## **Engineering Workflow Summary** 

```
Problem
```

```
↓
Understand
↓
Learn
↓
Design
↓
Review
```

```
↓
Implement
```

```
↓
Verify
```

```
↓
```

```
Document
```

9 

```
↓
Reflect
↓
Improve
```

This workflow is the standard operating procedure for every laboratory, service and architectural decision throughout the entire project. 

Regardless of the technology involved, the engineering process remains the same. 

## **Final Principle** 

Professional engineers do not begin with commands. 

They begin with understanding. 

Every command executed during this project must support an engineering decision that has already been justified. 

10 


## **Chapter 5 Change History**

|Version|Date|Description|
|---|---|---|
|1.0|(original)|Initial chapter|
|1.1|2026-07-13|§5.2 rewritten as the canonical lifecycle per ADR-022: diagram corrected to match stage text; Task Closure added as Stage 12; stage table and Authority Note added. §5.9 renamed Design Review & Approval; §5.11 renamed Verification.|
