## **Chapter 4 — Infrastructure Evolution Strategy** 

## **4.1 Purpose** 

Infrastructure is never built all at once. 

Professional environments evolve gradually as business requirements change. 

This project follows the same philosophy. 

Instead of deploying every technology from the beginning, the infrastructure grows through multiple development phases. 

Each phase introduces new engineering challenges that require new architectural decisions. 

Technology is never the objective. 

Business requirements are. 

## **4.2 Evolution Philosophy** 

The infrastructure evolves according to four simple rules. 

## **Rule 1** 

A business problem appears. 

↓ 

## **Rule 2** 

Current infrastructure is no longer sufficient. 

↓ 

## **Rule 3** 

An engineering solution is evaluated. 

↓ 

1 

## **Rule 4** 

The chosen technology is implemented. 

This sequence must never be reversed. 

The project never begins with: 

"We should install Docker." 

Instead, it begins with: 

"We need a better way to deploy applications." 

## **4.3 The Company Timeline** 

The project represents approximately two years of infrastructure growth. 

The learner experiences this journey as the company's Infrastructure Engineer. 

The company evolves through multiple operational stages. 

## **Phase 1 — Foundation** 

## **Company State** 

Atlas is a young software company. 

Approximately 25 employees. 

A single office. 

A small server room. 

No dedicated infrastructure team. 

The learner becomes the first Infrastructure Engineer. 

2 

## **Business Priorities** 

Reliable Linux servers. 

Internal networking. 

Secure remote administration. 

Internal DNS. 

Basic web services. 

System documentation. 

Backups. 

At this stage simplicity is the primary objective. 

## **Engineering Goal** 

Build stable foundations. 

Nothing should be automated before being understood. 

## **Phase 2 — Internal Services** 

## **Company Growth** 

More developers join the company. 

Internal applications begin appearing. 

Several Linux servers are now operating. 

Infrastructure slowly becomes harder to manage. 

## **New Business Problems** 

Internal websites require HTTPS. 

3 

Certificates are managed manually. 

Internal trust becomes difficult. 

Developers need additional services. 

## **Engineering Response** 

Introduce an Internal Certificate Authority. 

Implement HTTPS. 

Improve internal security. 

Create standardized certificate management. 

## **Phase 3 — Identity Management** 

## **Company Growth** 

More Linux servers. 

More developers. 

More administrators. 

Local Linux users become difficult to maintain. 

Password management becomes inconsistent. 

## **Business Problem** 

Identity management no longer scales. 

## **Engineering Response** 

Centralized authentication. 

LDAP. 

4 

Later: 

Kerberos. 

SSSD. 

PAM integration. 

## **Phase 4 — Operational Efficiency** 

## **Company Growth** 

Developers deploy applications more frequently. 

Infrastructure changes occur regularly. 

Manual administration consumes increasing amounts of time. 

## **Business Problems** 

Configuration drift. 

Repeated manual work. 

Inconsistent deployments. 

## **Engineering Response** 

Configuration management. 

Version-controlled infrastructure. 

Deployment automation. 

Engineering standards. 

5 

## **Phase 5 — Modern Infrastructure** 

## **Company Growth** 

Applications become containerized. 

Development accelerates. 

Operational complexity increases. 

## **Engineering Problems** 

Environment inconsistency. 

Application portability. 

Deployment reliability. 

## **Engineering Response** 

Containers. 

Image management. 

Container networking. 

Eventually: 

Container orchestration. 

Only if justified. 

## **4.4 Learning Model**

Every phase follows the **canonical Engineering Lifecycle defined in Chapter 5 (Engineering Workflow), Section 5.2** (ADR-022). This chapter does not define a separate workflow.

From a learning perspective, the lifecycle naturally groups into four movements:

- **Understand** — Stages 1–3: the business requirement, the problem, and the current infrastructure.
- **Learn & Design** — Stages 4–7: theory, architecture discussion, the design proposal, and its review.
- **Build & Prove** — Stages 8–9: implementation and verification.
- **Record & Reflect** — Stages 10–12: documentation, post-implementation review with lessons learned, and closure.

Learning is always driven by engineering requirements — never by chapter numbers. These groupings are a learning lens on the canonical lifecycle, not an alternative to it.

## **4.5 Introducing New Technologies** 

A technology may only be introduced when all of the following conditions are satisfied. 

## **Condition 1** 

A genuine business problem exists. 

7 

## **Condition 2** 

The learner understands why the current solution is insufficient. 

## **Condition 3** 

The learner understands the fundamentals required for the next technology. 

## **Condition 4** 

The learner can explain why the selected technology is preferable to simpler alternatives. 

If these conditions are not satisfied, the technology should not yet be introduced. 

## **4.6 Engineering Review Cycle** 

Every completed phase concludes with an engineering review. 

Questions include: 

What problem was solved? 

Why was this solution selected? 

Which alternatives were rejected? 

What limitations still exist? 

Which new operational problems appeared? 

What should improve next? 

The project continuously evaluates infrastructure rather than simply adding services. 

## **4.7 Growth Through Constraints** 

Real engineering is driven by constraints. 

Throughout the project the learner must continuously consider: 

8 

Available RAM. 

Available storage. 

Available budget. 

Time. 

Security. 

Reliability. 

Operational complexity. 

Every architectural decision must respect these limitations. 

Perfect solutions rarely exist. 

Appropriate solutions do. 

## **4.8 Technical Lead Responsibilities** 

During every phase the Technical Lead follows a consistent mentoring process. 

The Technical Lead should: 

Present the business problem. 

Ask guiding questions. 

Help analyze possible approaches. 

Discuss trade-offs. 

Encourage independent reasoning. 

Review the proposed design. 

Challenge assumptions. 

Approve the architecture. 

Support implementation. 

9 

Review documentation. 

Conduct a post-implementation review. 

The Technical Lead should avoid becoming an instruction generator. 

Its primary responsibility is developing engineering judgement. 

## **4.9 Learner Responsibilities** 

The learner is expected to: 

Understand the business requirement. 

Study the necessary theory. 

Read the recommended chapters. 

Design the proposed solution. 

Discuss alternatives. 

Implement the solution. 

Verify functionality. 

Document the implementation. 

Reflect on lessons learned. 

Engineering is an active discipline. 

Learning occurs through decision-making rather than observation. 

## **4.10 End of Project** 

The first project concludes when the learner can independently operate the infrastructure expected from a professional Junior Linux System Administrator. 

At this point the learner should possess: 

10 

Strong Linux fundamentals. 

Networking competence. 

Professional documentation skills. 

Practical troubleshooting ability. 

Infrastructure design experience. 

Confidence discussing engineering decisions during technical interviews. 

The infrastructure itself is not considered "finished." 

Like every real company, it can continue evolving. 

However, the first mission has been successfully completed. 

## **Final Principle** 

Infrastructure is not built by installing software. 

Infrastructure is built by solving business problems one engineering decision at a time. 

11 


## **Chapter 4 Change History**

|Version|Date|Description|
|---|---|---|
|1.0|(original)|Initial chapter|
|1.1|2026-07-13|§4.4 workflow diagram removed; replaced with reference to the canonical lifecycle (Chapter 5 §5.2, per ADR-022) and a learning-oriented grouping of the canonical stages.|
