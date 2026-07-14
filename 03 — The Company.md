## **Chapter 3 — The Company** 

## **3.1 Purpose** 

This project is not built around isolated laboratory exercises. 

Instead, every laboratory contributes to the growth of a fictional company. 

The learner acts as the Infrastructure Engineer responsible for designing, deploying, documenting and maintaining the company's internal infrastructure. 

Every new technology appears because the company has developed a legitimate business need. 

Nothing is introduced "just because it is the next topic." 

## **3.2 Company Overview** 

## **Company Name** 

Atlas Software Solutions 

## **Industry** 

Software Development 

Atlas develops custom web applications for external customers. 

The company builds internal business applications, customer portals, APIs and cloud-hosted services. 

Its engineering team consists primarily of Linux-based development environments. 

## **Why This Company?** 

This type of business naturally requires many of the technologies used in modern infrastructure engineering. 

1 

Examples include: 

- DNS • HTTPS 

- Linux servers 

- Git 

- CI/CD 

- Monitoring 

- Logging 

- Authentication 

- Containerization 

Every technology introduced later in this project will have a realistic business justification. 

## **3.3 Initial Company Size** 

The project begins at a very early stage of the company's growth. 

Employees: 

Approximately 25 

Departments: 

- Management • Software Development 

- QA • Infrastructure 

- Support 

The learner is the company's first Infrastructure Engineer. 

This means many systems have not yet been built. 

The infrastructure will evolve together with the business. 

## **3.4 Initial Business Requirements** 

At the beginning of the project, the company has relatively simple needs. 

Employees require: 

- reliable Linux servers; 

2 

- internal name resolution; 

- secure SSH access; 

- file sharing; 

- source code storage; 

- basic web services. 

No enterprise-scale infrastructure exists yet. 

The goal is simplicity. 

## **3.5 Infrastructure Philosophy** 

Atlas follows a conservative engineering philosophy. 

The company values: 

- reliability; 

- simplicity; 

- maintainability; 

- documentation; 

- security; 

- incremental improvement. 

The company intentionally avoids deploying technologies before they become necessary. 

## **3.6 Current Infrastructure (Project Start)** 

At the beginning of the project the infrastructure is intentionally small. 

Core components include: 

Infrastructure Network 

Linux Servers 

Primary DNS 

Secondary DNS 

Client Workstation 

Internal Web Server 

3 

Router / Internet Access 

No centralized authentication exists. 

No certificate authority exists. 

No monitoring exists. 

No automation exists. 

No CI/CD exists. 

These capabilities will be introduced gradually. 

## **3.7 Growth Strategy** 

Atlas grows slowly. 

New technologies appear only when justified by business growth. 

Examples include: 

The company launches more internal websites. 

## ↓ 

HTTPS becomes necessary. 

## ↓ 

Internal Certificate Authority is introduced. 

Developers increase from 5 to 15. 

## ↓ 

Managing local Linux accounts becomes inefficient. 

## ↓ 

LDAP is introduced. 

4 

The number of servers increases. 

## ↓ 

Manual configuration becomes repetitive. 

## ↓ 

Configuration management is introduced. 

Application deployments become frequent. 

## ↓ 

Continuous Integration becomes valuable. 

## ↓ 

CI/CD is introduced. 

Every technology must solve an existing operational problem. 

## **3.8 Engineering Culture** 

Atlas follows several engineering values. 

Problems are investigated before being fixed. 

Documentation is written alongside implementation. 

Infrastructure changes are reviewed. 

Security is considered during design. 

Automation follows understanding. 

Monitoring follows deployment. 

Knowledge is shared. 

These values influence every architectural decision throughout the project. 

5 

## **3.9 The Role of the Learner** 

The learner is not acting as a student. 

The learner is acting as Atlas Software Solutions' Infrastructure Engineer. 

Responsibilities include: 

- designing infrastructure; 

- deploying services; 

- troubleshooting incidents; 

- documenting systems; 

- improving reliability; 

- reducing operational complexity; 

- planning future growth. 

The learner is expected to think like an engineer rather than simply execute instructions. 

## **3.10 The Role of the Technical Lead** 

The Technical Lead is responsible for mentoring rather than completing tasks. 

Responsibilities include: 

- explaining engineering concepts; 

- reviewing architectural decisions; 

- asking challenging questions; 

- encouraging systematic troubleshooting; 

- introducing new technologies only when appropriate. 

The Technical Lead should avoid providing complete solutions whenever independent reasoning is possible. 

Guidance should gradually decrease as the learner gains experience. 

## **3.11 Business-Driven Learning** 

Every chapter of this blueprint begins with a business requirement. 

Example: 

- "We need secure communication." 

6 

not 

"Today we study TLS." 

Example: 

"We need centralized authentication." 

not 

"Today we study LDAP." 

The business problem defines the learning objective. 

The technology is merely the implementation. 

## **3.12 Long-Term Vision** 

The objective is not building the largest possible infrastructure. 

The objective is building an infrastructure that is: 

- understandable; 

- maintainable; 

- secure; 

- well documented; 

- professionally designed. 

By the end of the project, Atlas Software Solutions should resemble the infrastructure of a well-organized small-to-medium software company. 

Every deployed service should have a clear purpose, complete documentation and a justified architectural role. 

## **Engineering Principle** 

Infrastructure should grow for the same reason businesses grow: 

Because new problems require new solutions. 

Never because a technology is popular. 

7 

