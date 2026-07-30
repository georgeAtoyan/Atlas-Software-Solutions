## **Chapter 2 — Engineering Principles** 

## **2.1 Purpose** 

Engineering principles define how every technical decision is made throughout this project. 

These principles are independent of any specific technology. 

Whether configuring DNS, LDAP, Docker or Kubernetes, the same engineering mindset applies. 

When facing uncertainty, always return to these principles before making a decision. 

## **Principle 1 — Understand Before Implementing** 

Never deploy a service simply because a tutorial says so. 

Before installing any software, answer these questions: 

- What problem does it solve? 

- Why is this problem important? 

- How does the service solve it? 

- What would happen without it? 

Only after understanding the problem should implementation begin. 

Implementation without understanding creates administrators who memorize commands but cannot solve problems. 

## **Principle 2 — Build Only What Is Needed** 

Infrastructure grows because business requirements grow. 

Services should never be installed "just in case." 

Every component must have a clear purpose. 

Examples: 

Correct: 

- The company now has multiple servers. 
- User management has become difficult. 
- Introduce LDAP. 

Incorrect: 

- Install LDAP because every infrastructure should have one. 

Every technology must solve an existing problem. 

## **Principle 3 — Simplicity Before Complexity** 

The simplest solution that satisfies current requirements is usually the best solution. 

Avoid introducing unnecessary: 

- servers; 
- services; 
- dependencies; 
- automation; 
- abstraction. 

Complexity should only appear when simpler solutions are no longer sufficient. 

## **Principle 4 — Master Fundamentals Before Automation** 

Automation multiplies existing processes. 

If the manual process is poorly understood, automation only reproduces mistakes faster. 

Before introducing automation, be able to perform the task manually. 

Examples include: 

- creating users; 
- configuring DNS; 
- issuing certificates; 
- deploying services; 
- troubleshooting failures. 

Automation is introduced only after the underlying process is understood. 

## **Principle 5 — Documentation Is Part of the System** 

A service without documentation is an incomplete implementation. 

Documentation must answer questions that another engineer would ask: 

- What does this service do? 
- Why does it exist? 
- How is it configured? 
- How is it verified? 
- How is it restored? 
- How is it troubleshooted? 

The implementation is not finished until the documentation is complete. 

## **Principle 6 — Every Decision Requires Justification** 

No architectural decision should rely on habit or popularity. 

Every major choice must answer: 

Why this solution? 

Why not another one? 

What trade-offs were accepted? 

Examples: 

Why BIND instead of dnsmasq? 

Why Nginx instead of Apache? 

Why local storage instead of NFS? 

Engineering is the process of making informed trade-offs. 

3 

## **Principle 7 — Security Is Built In** 

Security is not an additional project completed later. 

Every service must be designed with security in mind from the beginning. 

Examples include: 

- least privilege; 

- secure authentication; 

- encrypted communication; 

- controlled access; 

- proper permissions; 

- audit logging. 

Security is considered during design—not after deployment. 

## **Principle 8 — Every Service Becomes Someone Else's Dependency** 

No service exists in isolation. 

Every new component eventually becomes part of a larger system. 

Examples: 

DNS supports LDAP. 

LDAP supports authentication. 

Certificates support HTTPS. 

Monitoring supports operations. 

Before deploying any service, understand: 

Who depends on this? 

What breaks if it fails? 

4 

## **Principle 9 — Troubleshooting Is a Core Skill** 

Knowing how to install software is not enough. 

Every engineer must know how to investigate failures. 

Troubleshooting follows a structured process: 

Observe. 

Collect evidence. 

Form hypotheses. 

Test hypotheses. 

Confirm root cause. 

Apply the smallest effective fix. 

Guessing is not troubleshooting. 

## **Principle 10 — Verify Everything** 

Never assume a configuration works. 

Every implementation requires verification. 

Examples: 

After configuring DNS: 

Perform queries. 

Check authoritative answers. 

Inspect logs. 

Validate zone transfers. 

Every completed laboratory ends with objective verification. 

5 

## **Principle 11 — Reproducibility Matters** 

Any engineer should be able to recreate the infrastructure using the documentation. 

Configurations should be: 

- repeatable; 

- predictable; 

- documented; 

- version controlled. 

Reproducibility is one of the foundations of professional infrastructure engineering. 

## **Principle 12 — Learn Through Failure** 

Mistakes are expected. 

Every failure should answer three questions: 

What happened? 

Why did it happen? 

How can it be prevented? 

Failures become permanent knowledge only after root cause analysis. 

## **Principle 13 — Think in Systems, Not Servers** 

Infrastructure is not a collection of individual machines. 

It is a system of interconnected components. 

Every change should be evaluated from the perspective of the whole environment. 

Questions to ask: 

Does this affect networking? 

Authentication? 

6 

Certificates? 

Monitoring? 

Backups? 

Security? 

Never optimize one server while ignoring the system. 

## **Principle 14 — Solve the Root Cause** 

Temporary fixes are acceptable only during incidents. 

Permanent work always targets the underlying cause. 

Symptoms may disappear temporarily. 

Root causes must disappear permanently. 

## **Principle 15 — Never Stop Asking "Why?"** 

Curiosity is one of the most valuable engineering skills. 

For every technology introduced during this project, continuously ask: 

Why does it exist? 

Why was it designed this way? 

Why is this configuration recommended? 

Why is one approach better than another? 

Engineering begins where memorization ends. 

## **Engineering Contract** 

Throughout this project the following commitments apply. 

7 

The learner commits to: 

- prioritizing understanding over speed; 

- documenting all work; 

- questioning assumptions; 

- practicing deliberately; • accepting mistakes as part of learning. 

The technical mentor commits to: 

- explaining concepts before implementation; 

- challenging architectural decisions constructively; 

- encouraging independent reasoning; 

- avoiding unnecessary complexity; 

- introducing technologies only when they become justified. 

These commitments define how the project will be conducted. 

## **Final Principle** 

Technology changes. 

Engineering principles remain. 

A good engineer can learn a new tool. 

A good engineer cannot compensate for weak fundamentals. 

Therefore, this project is built around principles first, technologies second. 

8 

