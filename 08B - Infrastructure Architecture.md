## **Chapter 8B — Infrastructure Architecture** 

## **1. Executive Summary** 

This document defines the initial infrastructure architecture for Atlas Software Solutions. 

It serves as the authoritative technical reference for all infrastructure-related Engineering Tasks throughout the project. 

The architecture is intentionally designed to resemble a small but professionally managed software company. 

The infrastructure is expected to evolve over time. Every architectural change must be documented through a new Architecture Decision Record (ADR). 

This document describes the initial state of Quarter 1 while providing a foundation for future expansion. 

## **2. Architecture Objectives** 

The infrastructure shall: 

- provide a realistic enterprise learning environment; 

- support progressive business growth; 

- prioritize simplicity over unnecessary complexity; 

- encourage deep understanding of Linux and networking; 

- be fully documented; 

- remain maintainable; 

- evolve incrementally through engineering decisions. 

The objective is not to simulate a large enterprise, but to build and operate a professional infrastructure appropriate for a growing software company. 

## **3. Design Principles** 

All architectural decisions follow these principles: 

**Business-Driven** 

Technology exists to solve business problems. 

**Incremental Growth** 

Infrastructure evolves as company requirements change. 

**Simplicity** 

The simplest correct solution is preferred. 

**Isolation** 

Each major infrastructure service runs on its own virtual machine. 

**Documentation** 

Every implementation is documented. 

**Security by Design** 

Security considerations are integrated from the beginning. 

**Operational Visibility** 

Infrastructure should be observable, understandable and easy to troubleshoot. 

**Reproducibility** 

Every service must be rebuildable using documented procedures. 

## **4. Physical Laboratory Environment** 

The infrastructure operates entirely inside VirtualBox. 

Host Operating System: Windows 11 
Hypervisor: Oracle VirtualBox 

Primary Administrative Tools:

- PowerShell 
- SSH 
- Git 
- Visual Studio Code 
- draw.io 
- Markdown 

Future cloud expansion will use AWS. 

## **5. Infrastructure Evolution** 

The infrastructure is developed in stages. 

Quarter 1 

Core Linux infrastructure 

↓ 

Quarter 2 

Identity Management 

↓ 

Quarter 3 

Automation 

↓ 

Quarter 4 

Container Platform 

↓ 

Quarter 5 

Cloud Integration 

Each phase builds upon the previous one. 

No phase introduces technology without a business requirement. 

## **6. Network Architecture** 

The infrastructure is divided into logical security zones. 

```
                    Internet
                        │
                [ VirtualBox NAT ]
                        │
                  rtr-edge-01
                  (Debian Router)
                        │
        ┌───────────────┼───────────────┐
        │               │               │
   Management LAN   Server LAN     Client LAN
   192.168.10.0     192.168.20.0   192.168.30.0
        │               │               │
  Admin systems     Infrastructure   User systems
```

Future phases will introduce: 

- DMZ 

- VPN Network 

- Cloud Network 

- Monitoring Network 

without redesigning the existing architecture. 

## **7. Network Segments** 

## **Management LAN** 

Purpose: Infrastructure administration. 

Examples: 

- Administrative workstation. 
- Future jump host. 
- Management interfaces. 

Only administrators operate within this network. 

## **Server LAN** 

Purpose: Internal infrastructure services. 

Examples: 

- DNS 
- Certificate Authority 
- LDAP 
- Git 
- Monitoring 
- Application services 

Direct user access is not permitted.  

## **Client LAN** 

Purpose: Developer and employee workstations. 

Used to validate production-like behavior from a client perspective. 

## **Future DMZ** 

Public-facing services. 

Will be introduced only when required. 

## **8. Addressing Plan** 

> **Authority Note (ADR-021):** This section is the **single authoritative IP Address Allocation Policy** for the Atlas Software Solutions infrastructure. It supersedes the ranges formerly defined in ADR-005. The allocation table below must not be reproduced in any other document; other documents shall reference this section. Changes to this policy require a new Architecture Decision Record.

The infrastructure uses private IPv4 addressing. 

## **Management Network** 

192.168.10.0/24 

Gateway 

192.168.10.1 

## **Server Network** 

192.168.20.0/24 

Gateway 

192.168.20.1 

## **Client Network** 

192.168.30.0/24 

Gateway 

192.168.30.1 

## **Address Allocation Policy** 

|Range|Purpose|
|---|---|
|.1|Default Gateway|
|.2-.9|Reserved|
|.10-.29|Core Infrastructure|
|.30-.59|Platform Services|
|.60-.99|Applications|
|.100-.149|Clients|
|.150-.199|Temporary Systems|
|.200-.254|Future Expansion|



IP addresses are assigned statically unless a future Engineering Task introduces DHCP. 

**Note on management workstations:** administrative workstations on the Management LAN (e.g. cli-admin-01 at 192.168.10.10) are allocated from the Core Infrastructure range. Although they carry the cli- naming prefix, they are management-plane infrastructure, not end-user client systems.

**Related decisions:** ADR-021 (establishes this section as the sole allocation authority); ADR-005 (superseded — historical record only); ADR-001 (Segmented Network Architecture).

## **9. Host Naming Standards** 

Every infrastructure component follows predictable naming. 

Servers: srv-role-number 

Examples: 

- srv-dns-01 
- srv-ca-01 
- srv-web-01 
- srv-git-01 
- srv-monitor-01 

Routers 
- rtr-edge-01 

Clients 
- cli-admin-01 
- cli-dev-01 

Future Kubernetes nodes 
- k8s-master-01 
- k8s-worker-01 

Consistency is mandatory. 

## **10. DNS Architecture** 

Internal DNS Zone: atlas.lab 

Examples 

- srv-dns-01.atlas.lab 
- srv-web-01.atlas.lab 
- srv-ca-01.atlas.lab 

Reverse DNS will be implemented after forward DNS is operational. 

## **11. Server Inventory** 

Quarter 1 begins with a minimal infrastructure. 

|Host|Purpose|Planned OS|
|---|---|---|
|rtr-edge-01|Router / NAT|Debian Stable|
|srv-dns-01|DNS Server|Debian Stable|


|Host|Purpose|Planned OS|
|---|---|---|
|cli-admin-01|Administrator Workstation|Ubuntu Desktop|

Additional servers appear only when justified by business requirements. 

Examples include: 

- srv-ca-01
- srv-ldap-01
- srv-git-01
- srv-monitor-01
- srv-ci-01 

## **12. Operating System Strategy** 

Both Debian Stable and Ubuntu Server LTS are intentionally used. 

Debian Stable hosts foundational infrastructure services. 

Ubuntu Server LTS hosts application-oriented services. 

Ubuntu Desktop serves as the primary administrative workstation. 

The objective is to gain operational experience across both environments while reinforcing that Linux administration principles remain consistent. 

## **13. Security Architecture** 

Security is integrated into every Engineering Task. 

Core principles include: 

- Least Privilege 
- SSH Key Authentication 
- Host Firewalls 
- Service Isolation 
- Certificate-Based Encryption 
- Principle of Minimal Exposure 

Services should only expose the ports required for operation. 

## **14. Documentation Standards** 

Every infrastructure component requires: 

- Architecture Diagram 
- README 
- Configuration Notes 
- Verification Procedure 
- Operational Notes 
- Troubleshooting Guide 
- Runbook 
- Lessons Learned 

No service is considered complete until documentation is finished. 

## **15. Infrastructure Repository** 

Infrastructure is managed through Git. 

The primary repository contains: 

/architecture 

/adr 

/docs /engineering-tasks 

/runbooks 

/diagrams 

/scripts 

/templates 

Future repositories may contain application code or automation projects, but the Infrastructure Repository remains the single source of truth for infrastructure documentation. 

## **16. Operational Philosophy** 

Infrastructure should be: 

- Predictable 
- Observable 
- Recoverable 
- Documented 
- Maintainable 

Every Engineering Task must improve at least one of these qualities. 

## **17. Resource Management** 

The complete infrastructure represents the company's logical environment rather than the number of simultaneously running virtual machines. 

Engineering Tasks are designed so that only the systems relevant to the current objective need to be powered on. 

This approach reflects practical home-lab constraints while preserving a realistic enterprise architecture. 

Virtual machines remain available for future phases without requiring all systems to run continuously. 

## **18. Future Expansion** 

The architecture is intentionally prepared for future additions, including: 

- Internal PKI 
- LDAP 
- SSSD 
- PAM 
- Git Platform 
- Monitoring Stack 
- Container Platform 
- Configuration Management 
- CI/CD 
- VPN 
- Cloud Connectivity 
- Disaster Recovery 
- Monitoring Network 
- DMZ 
- Hybrid Cloud 

No future service should require redesigning the existing architecture. 

## **19. Architecture Governance** 

This document is governed by the following rules: 

1. Architectural changes require an ADR. 

2. New infrastructure components must follow naming standards. 

3. Documentation is mandatory. 

4. Security is reviewed before deployment. 

5. Every implementation must be verifiable. 

6. Simplicity is preferred over unnecessary complexity. 

7. Engineering decisions must be justified by business requirements. 

## **20. Definition of Architectural Success** 

The architecture is considered successful when it: 

- Supports business requirements. 
- Remains understandable. 
- Scales through incremental growth. 
- Can be rebuilt from documentation. 
- Allows safe experimentation. 
- Promotes sound engineering practices. 
- Prepares the learner for professional Linux infrastructure administration. 

## **Architecture Vision** 

Atlas Software Solutions is not intended to simulate a global enterprise with thousands of servers. 

It represents a well-engineered, growing software company where every infrastructure component has a clear purpose, every architectural decision is documented, and every new technology is introduced only when justified by business needs. 

The architecture is deliberately designed to teach not only how systems are built, but why they are built that way. 

This document serves as the technical foundation upon which every future Engineering Task, Architecture Decision Record and infrastructure service will be based. 

## **Chapter 8B Change History**

|Version|Date|Description|
|---|---|---|
|1.0|(original)|Initial architecture|
|1.1|2026-07-13|§8: Authority Note added per ADR-021; management-workstation allocation note added; Related Decisions added. Allocation ranges unchanged.|
