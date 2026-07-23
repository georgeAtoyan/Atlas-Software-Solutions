## **Design Proposal — cli-admin-01** 

**Engineering Task:** INF-001 cli-admin-01

**Status:** Approved

**Version:** 1.0

**Last Updated:** 2026-07-16

**Verified by:** George

## 1. Objective & Problem Statement

As there is no controlled administrative environment the current objective is to build the first administrative workstation that will become 
the primary management endpoint for Atlas Solutions Infrastructure.

## 2. Proposed Solution

The primary management endpoint will use the latest Linux Ubuntu 26.04 LTS (Intel or AMD 64-bit architecture) referencing Infrastructure Decision Record under ADR-007:

- VM name: VirtualBox INF-001 - cli-admin-01
- hostname: cli-admin-01 (referencing Infrastructure Architecture chapter 9 Host Naming Standards and Infrastructure Decision Record ADR-04). 
- Resource allocation: 4Gb RAM (as we need to take into account that future build will require additional allocation of 1Gb RAM for each headless Debian/Ubuntu servers.), 40GB of Storage (taking into account that the admin workstation will expand as the infrastructure will expand linearly), 2vCPU. 
- Network: The NAT network adapter will be set for the VirtualBox INF-001 - cli-admin-01. The built-in NAT DHCP will assign the IP address to admin-cli-01. 
During the migration to the Management LAN the admin-cli-01 will be disconnected from NAT network. We can assign static IP addresses to the infrastructure servers. The IP address of 192.168.10.10 will be applied the moment we build the router and Management LAN. The admin-cli-01 will be assigned with 192.168.10.10 IP address (reference Infrastructure Architecture Chapter 8 Addressing Plan and Address Allocation Policy). The admin workstation should have installed with SSH, Git, VS Code, draw.io for maintaining the proper initial and upcoming administrating and management of infrastructure. 

## 3. Security considerations

As the machine is the highest-value confidentiality target it should be updated and patched regularly to avoid any security issues. No direct root login must be allowed. A single admin user allowed to operate through sudo.

## 4. Alternative solutions

Administer the infrastructure using a headless Ubuntu Server VM. 

**Advantage:** The minimal resource allocation required for headless Ubuntu Server VM. 

**Disadvantage:** Operating with applications such as VS code, draw.io using cli interface would be less impractical. 

**Reason for rejection:** Administrative friction.

## 5. Success criteria

INF-001 is successfully executed when: 

a) hostname resolves to cli-admin-01. 

b) OS is Ubuntu 26.04 LTS. 

c) the machine reaches the internet. 

d) the machine completes a full package update 

e) each required tool executes and reports its version: GIT, openssh-client, VS code 

f) configuration survives the reboot.

## 6. Verification plan

a) hostname resolves to cli-admin-01. 

b) OS is Ubuntu 26.04 LTS (hostname). 

c) the machine reaches the internet (ping command generate successful output  - 0% packet loss). 

d) the machine completes a full package update (apt update, apt upgrade, apt list --upgradable) 

e) each required tool executes and reports its version (ssh -V, git --version, code --version) 

f) configuration survives the reboot.

## 7. Documentation plan

After the Verification Phase the following documents will be produced: 

- README
- Architecture Diagram
- ADR (when applicable)
- Runbook
- Verification Notes
- Lessons Learned

## 8. Risks & rollback

During the installation process of Linux Ubuntu 26.04 LTS the proposed 4Gb of RAM may not be sufficient for stable work. In that case we have to change the base memory allocation and increase it to recommended 6GB of RAM. The proposed rollback that could be implemented is to use the snapshot of the current state.
