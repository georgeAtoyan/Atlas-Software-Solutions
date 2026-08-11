## **Runbook — rtr-edge-01** 

**Engineering Task:** INF-002 

**Version:** 1.1 

**Status:** Approved

**Last Updated:** 2026-08-11 

**Author:** George

## **1. Purpose** 

The Runbook INF-002 exists so the Debian router can work as a default gateway providing Internet access.

## **2. Scope** 

- Installation
- Initial Configuration
- Validation
- Recovery

## **3. Prerequisites** 

- Windows Host
- VirtualBox 7.2.12
- Internet connectivity
- Debian Stable 13.6 (A:\ISO\debian-13.6.0-amd64-netinst.iso)
- Sufficient disk space

## **4. Infrastructure Context** 

• Current architecture: Internet -> rtr-edge-01 -> Management LAN
• Target architecture: Internet -> rtr-edge-01 -> Management LAN / Server LAN / Client LAN

## **5. System Specifications** 

## **Virtual Machine** 

| Property | Value |
|---|---|
| VM Name | rtr-edge-01 |
| Hostname | rtr-edge-01 |
| Operating System | Debian Stable |
| Version | 13.6 |
| Firmware | BIOS |

| Property | Value |
|---|---|
| vCPU | 1 |
| Memory | 1024MB |
| Disk | 10GB |
| Video Memory | 16MB |
| Storage Controller | SATA |
| Virtualization Platform | VirtualBox |

## **Network Configuration** 

## **Day-One Configuration** 

| Setting | Value |
|---|---|
| Adapter | NAT |
| Address Assignment | 10.0.2.15/24 |
| Expected Network | NAT subnet 10.0.2.0/24, DHCP-assigned | 

## **Target Configuration** 

| Setting | Value |
|---|---|
| Network | Management LAN (192.168.10.0/24) |
| IP Address | 192.168.10.1 |

## **6. Installation Procedure** 

### **Create Virtual Machine** 

- rtr-edge-01

- Debian Stable 13.6

- 1vCPU, 1024 MB RAM, 10GB Storage, 16MB Video Memory

- Adapter 1 = NAT, Adapter 2 = Internal Network (mgmt-lan)

## **Attach Installation Media** 

debian-13.6.0-amd64-netinst.iso

## **Operating System Installation** 

- Minimal OS installation
- language: English
- keyboard: English(USA)
- storage layout: LVM 
- encryption: none
- layout decision: one partition 
- hostname: rtr-edge-01
- user account: george 
- OpenSSH server: installation declined
- Web server: installation declined
- Dekstop: installation declined
- Standard system utilities: kept

## **Initial Boot** 

- The VM rebooted successfully.
- Debian reached CLI login screen.
- The created user logged in successfully.
- The system loaded without errors.

## **7. Initial Configuration** 

- update packages: sudo apt update 
- verify hostname: hostname
- verify interface names: ip -br addr
- edit /etc/network/interfaces: add stanza (auto enp0s8 / iface enp0s8 inet static / address 192.168.10.1/24)
- enable network interface (sudo ifup enp0s8)

## **8. Software Installation** 

No addiional software installed; base system only. 

## **9. Configuration Changes** 

- ss -tlnp (to verify no open port are listening)
- ip -br addr (to verify enp0s8 is UP and assigned with 192.168.10.1/24)

## **10. Validation Steps** 

| Validation |Command / Method|Expected Result |
|---|---|---|
| Hostname | hostname | rtr-edge-01 |
| OS | cat /etc/debian_version | 13.6 |
| Connectivity | ping -c 4 debian.org | 0% packet loss |
| Connectivity | ping -c 4 8.8.8.8 | 0% packet loss |
| Ports | ss -tlnp | NO ports opened |
| Encryption| lsblk | root LV + swap LV, no encryption |
| Network Interface | ip link | enp0s3, enp0s8 |
| DNS | cat /etc/resolv.conf | observed 192.168.0.1, supplied via NAT DHCP |

## **11. Snapshot Strategy** 

| Snapshot | Purpose |
|---|---|
| INF-002-complete-verified | Configured baseline |

## **12. Recovery Procedure** 

1. Snapshot Recovery
If the system is unstable or the machine is broken, the snapshot recovery (INF-002-complete-verified) can be used.
2. Recovery with no usable snapshot
Rebuild a new VM following the current Runbook. Restore documentation/configuration from Git

## **13. Operational Notes** 

- install updates regularly
- don't install unnecessary software
- keep snapshots before major changes

## **14. Known Limitations** 

- No routing, NAT, forwarding, firewall, nftables

## **15. References** 

- README - INF-002
- Verification Notes - INF-002
- Lessons Learned - INF-002

## **16. Change History** 

| Version | Date | Description |
|---|---|---|
| 1.0 | 2026-08-11 | Initial version |
| 1.1 | 2026-08-11 | Expanded &7 network procedure, corrected DNS/encryption validation rows, separated adapter attachment from addressing, added limitations |

## **Approval** 

|Role|Name|Date|
|---|---|---|
| Infrastructure Engineer | George | 2026-08-11 |
| Technical Lead | | 2026-08-11 |
