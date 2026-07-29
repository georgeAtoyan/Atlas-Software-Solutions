## **Runbook — cli-admin-01** 

**Engineering Task:** INF-001 

**Version:** 1.1 

**Status:** Approved

**Last Updated:** 2026-07-27 

**Verified By:** George

## **1. Purpose** 

The Runbook INF-001 exists so an engineer can install, rebuild, configure, and maintain this workstation consistently. 

## **2. Scope** 

- Installation
- Initial Configuration
- Software Installation
- Validation
- Recovery

## **3. Prerequisites** 

- Windows Host
- VirtualBox 7.2.12
- Internet connectivity
- Ubuntu 26.04 LTS ISO (A:\ISO\ubuntu-26.04-desktop-amd64)
- Sufficient disk space
- Administrator privileges

## **4. Infrastructure Context** 

• Current architecture: Windows Host -> VirtualBox NAT -> cli-admin-01
• Target architecture: Internet -> rtr-edge-01 -> Management LAN -> cli-admin-01

## **5. System Specifications** 

## **Virtual Machine** 

| Property | Value |
|---|---|
| VM Name | VirtualBox INF-001 - cli-admin-01 |
| Hostname | cli-admin-01 |
| Operating System | Linux Ubuntu Desktop |
| Version | 26.04 LTS |
| Firmware | UEFI |

| Property | Value |
|---|---|
| vCPU | 2 |
| Memory | 4096MB |
| Disk | 40GB |
| Video Memory | 128MB |
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
| Network | Management LAN (192.168.10.0) |
| IP Address | 192.168.10.10 |
| Gateway | 192.168.10.1 |
| DNS | srv-dns-01 |


## **6. Installation Procedure** 

### **Create Virtual Machine** 

- VirtualBox INF-001 - cli-admin-01

- Linux Ubuntu Desktop 26.04 LTS

- 2vCPU, 4096 MB RAM, 40GB Storage, 128MB Video Memory

## **Attach Installation Media** 

ubuntu-26.04-desktop-amd64 

## **Operating System Installation** 

- Minimal OS installation
- language: English
- keyboard: English(USA)
- storage layout: LVM 
- encryption: LUKS 
- hostname: cli-admin-01
- user account: george 
- OpenSSH server: installation declined

## **Initial Boot** 

- The VM rebooted successfully.
- Ubuntu reached the graphical login screen.
- The created user logged in successfully.
- The GNOME desktop loaded without errors.

## **7. Initial Configuration** 

- update packages: sudo apt update 
- verify hostname: hostname
- remove unnecessary services: CUPS 
- install packages:
	- dpkg -l git (not installed), sudo apt install git, git -v
 	- dpkg -l openssh-client (not installed), sudo apt install openssh-client, ssh -V 

## **8. Software Installation** 

|Software|Installation Method|Purpose|
|---|---|---|
| VS Code | App Center | Editing configurations and Markdown documentation | 
| draw.io web-based | no installation | To keep the minimal number of packages installed | 

## **9. Configuration Changes** 

### Remove unnecessary services: CUPS
- sudo systemctl stop cups.service cups.socket
- sudo systemctl disable cups.service cups.socket
- sudo systemctl stop cups-browsed.service
- sudo systemctl disable cups-browsed.service
- ss -tlnp (to verify no open port on :631)

### Repository Access Setup:

**Generate public and private SSH keys inside ~/.ssh directory:**
- ssh-keygen -t ed25519 -C "your.email@example.com" (add passphrase protection)
- chmod 700 ~/.ssh
- chmod 600 ~/.ssh/id_ed25519 
- chmod 644 ~/.ssh/id_ed25519.pub

**Add public SSH key on GitHub:**
- Manually add the public SSH key (cli-admin-01)
- Paste the entire content of .ssh/id_ed25519.pub into the cli-admin-01 (SSH key)

**Test Git repository access:**
- ssh -T git@github.com

**Git identify configuration:**
- git config --global user.name "username"
- git config --global user.email "email"

**Clone the Infrastructure Repository:**
- git clone git@github.com:OWNER/REPO.git


## **10. Validation Steps** 

| Validation |Command / Method|Expected Result |
|---|---|---|
| Hostname | hostname | cli-admin-01 |
| OS | cat /etc/os-release | 26.04 LTS |
| Connectivity | ping -c 4 ubuntu.com | 0% packet loss |
| Connectivity | ping -c 4 8.8.8.8 | 0% packet loss |
| Software | git --version | Git version string displayed |
| Software| ssh -V | OpenSSH_10.2p1 |
| Software | code --version | VS Code version string displayed |
| Ports | ss -tlnp | NO :22 :631 ports opened |
| Encryption| lsblk | dm_crypt-0 |
| Repository access | ssh -T git@github.com | Message "You have successfully authenticated" |


## **11. Snapshot Strategy** 

| Snapshot | Purpose |
|---|---|
| 01-clean-install | Post-install before configuration |
| 02-configured-baseline-post-INF001 | Configured baseline after INF-001 hardening |


## **12. Recovery Procedure** 

1. Snapshot Recovery
If the system is unstable or the machine is broken, the snapshot recovery (02-configured-baseline-post-INF001) can be used.

2. Recovery with no usable snapshot
Rebuild a new VM following the current Runbook. Restore documentation/configuration from Git

3. LUKS Warning
- a lost LUKS passphrase is not something you troubleshoot;
- you can't bypass encryption;
- you can't recover the encrypted data;
- rebuild the workstation and restore whatever was stored in version control or backups.

## **13. Operational Notes** 

- install updates regularly
- don't install unnecessary software
- keep snapshots before major changes

## **14. Known Limitations** 

- Temporary NAT networking
- Management LAN not yet implemented

## **15. References** 

• README - INF-001
• Verification Notes - INF-001
• Lessons Learned - INF-001

## **16. Change History** 

| Version | Date | Description |
|---|---|---|
| 1.0 | 2026-07-16 | Initial version |
| 1.1 | 2026-07-27 | Added SSH key generation, GitHub authentication, repository clone, and Git identity configuration to support commiting from cli-admin-01 |

## **17. Troubleshooting**

| Symptom | Cause | Resolution |
|---|---|---|
| Installer reaches black screen after boot messages | Insufficient VirtualBox video memory | Increase Video Memory to 128 MB and reboot installer |

## **Approval** 

|Role|Name|Date|
|---|---|---|
| Infrastructure Engineer | George | 2026-07-16 |
| Technical Lead | | 2026-07-16 |
