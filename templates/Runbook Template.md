## **Runbook Template** 

## **Instructions** 

This template shall be used for every Engineering Task requiring installation, configuration, maintenance, or recovery procedures. 

Replace all placeholder text enclosed in `< >` 

. 

Remove instructional notes before final publication. 

Follow **STD-RUNBOOK-001 (Runbook Standard)** when completing this document. 

## **Runbook — <System Name>** 

**Engineering Task:** <INF-001 / NET-004 / OPS-001> 

**Version:** 1.0 

**Status:** Draft | Approved | Superseded 

**Last Updated:** YYYY-MM-DD 

## **1. Purpose** 

Briefly describe the purpose of this Runbook. 

Explain what infrastructure component it covers. 

## **2. Scope** 

Define exactly what this Runbook applies to. 

Examples: 

- Initial installation 

- Complete rebuild 

- Operational maintenance 

1 

- Recovery after failure 

## **3. Prerequisites** 

List all requirements before beginning. 

Examples: 

- Ubuntu 26.04 LTS ISO • VirtualBox 7.x • Internet connectivity • Administrative privileges 

- Existing infrastructure dependencies 

## **4. Infrastructure Context** 

Briefly describe where this component fits within the Atlas infrastructure. 

Include: 

- current architecture; • target architecture; • dependencies. 

Reference the README and Architecture Diagram where appropriate. 

## **5. System Specifications** 

## **Virtual Machine** 

|Property|Value|
|---|---|
|VM Name|<vm-name>|
|Hostname|<hostname>|
|Operating System|<Operating System>|
|Version|<Version>|
|Firmware|BIOS / UEFI|



2 

|Property|Value|
|---|---|
|vCPU|<Number>|
|Memory|<Amount>|
|Disk|<Amount>|
|Video Memory|<Amount>|
|Storage Controller|SATA / NVMe|
|Virtualization Platform|VirtualBox|



## **Network Configuration** 

## **Day-One Configuration** 

|Setting|Value|
|---|---|
|Adapter|<NAT / NAT Network / Internal Network>|
|Address Assignment|DHCP / Static|
|Expected Network|<Description>|



## **Target Configuration** 

|Setting|Value|
|---|---|
|Network|<Management LAN / Server LAN / Client LAN>|
|IP Address|<IP Address>|
|Gateway|<Gateway>|
|DNS|<DNS Server>|



## **6. Installation Procedure** 

Describe the installation chronologically. 

Typical sections include: 

## **Create Virtual Machine** 

- VM name 

3 

- Guest operating system 

- Hardware allocation 

## **Attach Installation Media** 

Document the ISO image and boot settings. 

## **Operating System Installation** 

Include significant installation choices. 

Examples: 

- language; 

- keyboard; 

- storage layout; 

- LVM; 

- encryption; 

- hostname; 

- user account; 

- package selection. 

## **Initial Boot** 

Describe the first successful boot and login. 

## **7. Initial Configuration** 

Document post-installation configuration. 

Typical tasks: 

- update packages; 

- verify hostname; 

- configure networking; 

- verify time synchronization; 

- remove unnecessary services; 

- configure repositories. 

4 

## **8. Software Installation** 

Document all intentionally installed software. 

|Software|Installation Method|Purpose|
|---|---|---|
|<Package>|apt / App Center / Manual|<Purpose>|



Avoid documenting default operating system packages. 

## **9. Configuration Changes** 

Document all significant configuration changes. 

Examples: 

• Netplan • systemd • SSH • firewall • DNS • package repositories 

Reference modified configuration files where appropriate. 

## **10. Validation Steps** 

Describe how each major implementation step is verified. 

Example format: 

|Validation|Command / Method|Expected Result|
|---|---|---|
|Hostname|hostnamectl|Correct hostname displayed|
|Network|ip addr|Correct interface confguration|
|Connectivity|ping|Successful replies|
|Services|systemctl status|Active (running)|



Detailed evidence belongs in the Verification Notes. 

5 

## **11. Snapshot Strategy** 

Document all VirtualBox snapshots created during the task. 

|Snapshot|Purpose|
|---|---|
|<Name>|<Reason>|



Only create snapshots at stable recovery points. 

## **12. Recovery Procedure** 

Describe how to recover from common failures. 

Examples: 

- restore VirtualBox snapshot; 

- recreate VM; • reinstall software; • restore configuration from Git. 

## **13. Operational Notes** 

Record operational considerations. 

Examples: 

- regular updates; 

- maintenance schedule; • backup requirements; • monitoring requirements. 

## **14. Known Limitations** 

Document temporary limitations or unfinished work. 

Examples: 

- temporary NAT networking; 

6 

- pending migration; • future hardening tasks. 

## **15. References** 

Reference related documentation. 

- README • Verification Notes 

- Architecture Diagram • ADR 

- Engineering Task • Lessons Learned 

## **16. Change History** 

|**tory**|||
|---|---|---|
|Version|Date|Description|
|1.0|YYYY-MM-DD|Initial version|



## **Approval** 

|Role|Name|Date|
|---|---|---|
|Infrastructure Engineer|<Name>|YYYY-MM-DD|
|Technical Lead|<Name>|YYYY-MM-DD|



7 

