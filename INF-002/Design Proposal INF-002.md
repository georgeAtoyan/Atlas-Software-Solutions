## **Design Proposal — rtr-edge-01** 

**Engineering Task:** INF-002 rtr-edge-02

**Status:** Approved

**Version:** 1.3

**Last Updated:** 2026-08-03

**Verified by:** Technical Lead

## 1. Objective & Problem Statement

The INF-002 creates the router VM (rtr-edge-01) that plays a crucial role as a gateway that will provide the Internet access to the nodes in the LAN segments. The router has two network adapters: NAT (access to the Internet), Management LAN. No routing, NAT, forwarding, masquerading will be established as they are out of scope of the current INF-002 task.

## 2. Proposed Solution

The router will use the latest Debian Stable 13.6.0 (stable, trixie) no dekstop, per debian.org/distrib. Referencing Infrastructure Decision Record under ADR-007:

- VM name: VirtualBox INF-001 - rtr-edge-01
- hostname: rtr-edge-01 (referencing Infrastructure Architecture chapter 9 Host Naming Standards and Infrastructure Decision Record ADR-04). 
- Resource allocation: 1Gb RAM (as it's main role is managing the network traffic), 10GB of Storage (enough space for long-term OS updates), 1 vCPU.
- Network: Two network adapters will be set - enp0s3 (NAT, access to the Internet) that would be automatically assigned with IP by VirtualBox, enp0s8 (Management LAN) - 192.168.10.0/24. The router will be assigned with static IP address (192.168.10.1) referencing 08B - Infrastructure Architecture under Section 8: Addressing Plan. The router considered as availability-critical infrastructure that plays a role of gateway providing Internet access to the whole nodes in the LAN. The network configuration on Debian Stable 13.6.0 (stable, trixie) requires using ifupdown networking system (/etc/network/interfaces) to set two network interfaces enp0s3 (NAT) and enp0s8 (Management LAN), respectively (reference 08B - Infrastructure Architecture under Section 9 Addressing Plan and Address Allocation Policy table). DNS is expected to be auto-configured via VirtualBox built-in DHCP on enp0s3.

Deferral:
1. The sshd (SSH Server) installation is postponed as there are no endpoints connected to Management LAN yet. The SSH Server installation can be included during NET-001 task.
2. Routing, NAT, forwarding, masquerading will be established during the NET-001/NET-002 task.
3. Firewall, nftables will be established during the NET-001/NET-002 task.

## 3. Security considerations

The router rtr-edge-01 is considered as availability-critical and confidentiality-tolerant that is why there is no reason to use disk encryption or LUKS as it will require to type the passphrase that might be lost or compromised that potentially put the whole infrastructure at danger as it's the only gateway that provides Internet access. AS the router is not considered as confidentiality-critical, it still should be updated and patched regularly to avoid any security issues. No direct root login must be allowed. A single admin user allowd to operate through sudo.

## 4. Alternative solutions

using VirtualBox NAT as the gateway providing Internet access for the nodes in the LAN.

**Advantage:** The simple setting that requires no prior network installation.

**Disadvantage:** Tha lack of visibility into networking.

**Reason for rejection:** Due to limited educational value (Reference 08B - Infrastructure Decision Record: ADR-002)

## 5. Success criteria

INF-002 is successfully executed when: 

a) hostname resolves to rtr-edge-01. 

b) OS is Debian Stable 13.6.0. 

c) the machine reaches the internet. 

d) the machine completes a full package update 

e) configuration survives the reboot

f) two network interfaces (enp0s3, enp0s8) are set

g*) the node correctly assigned with IP address (192.168.10.1) on enp0s8

h) no unnecessary services are enabled and listening

i) dns server is correctly configured

j) dns name resolution works correct

* no cross-segment ping or reachability checks have to be tested as there no nodes in the segment yet.

## 6. Verification plan

a) hostname resolves to rtr-edge-01 (hostname). 

b) OS is Debian Stable 13.6.0 (cat /etc/os-release, cat /etc/debian_version). 

c) the machine reaches the internet (ping 8.8.8.8 command generates successful output  - 0% packet loss). 

d) the machine completes a full package update (apt update, apt upgrade, apt list --upgradable) 

e) configuration survives the reboot.

f) verify two network interfaces (enp0s3, enp0s8) are present (ip link)

g) verify the router assigned with correct IP address (192.168.10.1) on enp0s8 (ip a show enp0s8)

h) verify no unnecessary services are listening on ports (ss -tlnp)

i) verify correct dns settings applied (cat /etc/resolv.conf)

j) verify correct dns name resolution (ping www.debian.org command generates successful output - 0% packet loss)

## 7. Documentation plan

After the Verification Phase the following documents will be produced: 

- README
- Architecture Diagram
- ADR (when applicable)
- Runbook
- Verification Notes
- Lessons Learned

## 8. Risks & rollback

During the installation process of Linux Debian Stable 13.6.0, the proposed rollback that could be implemented is to use the snapshot of current state. The interface-naming might differ from the proposed assumptions.
