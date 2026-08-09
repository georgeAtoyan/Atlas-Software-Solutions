# ADR Register

**Document ID:** ADR-REGISTER

**Version:** 1.2

**Status:** Approved

**Last Updated:** 2026-08-08

**Location (repository):** /adr/ADR-REGISTER.md

---

## 1. Purpose

The ADR Register is the **single authoritative index of all Architecture
Decision Records** in the Atlas Software Solutions Engineering Blueprint and
the **only mechanism through which ADR identifiers are allocated**.

Its purpose is to make identifier reuse impossible by procedure: no engineer
determines the next ADR number by memory, by counting files, or by inspecting
Chapter 8A. The next number is always read from, and immediately updated in,
this Register.

## 2. Numbering Policy

1. ADR identifiers use the form `ADR-NNN` (zero-padded, three digits).
2. Identifiers are **permanent** and are **never reused**, including for
   Rejected or Superseded ADRs (STD-ADR-001 §6.1).
3. Identifiers are allocated **sequentially** from this Register at the
   moment an ADR enters **Proposed** status.
4. Allocating an identifier and adding its row to this Register happen in the
   **same commit** as the creation of the ADR document.
5. Status changes (Proposed → Accepted, Accepted → Superseded, etc.) must be
   reflected in this Register in the same commit as the change to the ADR.
6. The identifiers "ADR-0" and "ADR-000" were never allocated, do not exist,
   and must never be allocated.
7. In any discrepancy between this Register and any other document, **this
   Register prevails** for identifier allocation and status.

## 3. Next Available Identifier

> ## **ADR-025**

(Update this value in the same commit that allocates it.)

## 4. Register

| ADR | Title | Status | Date | Compliance | Supersedes / Superseded By |
|---|---|---|---|---|---|
| ADR-001 | Segmented Network Architecture | Accepted | (foundation) | Grandfathered (pre-STD-ADR-001) | — |
| ADR-002 | Dedicated Router Virtual Machine | Accepted | (foundation) | Grandfathered | — |
| ADR-003 | Internal DNS Namespace | Accepted | (foundation) | Grandfathered | — |
| ADR-004 | Server Naming Convention | Accepted | (foundation) | Grandfathered | — |
| ADR-005 | Static Address Planning | **Superseded** | (foundation) | Grandfathered | Superseded by ADR-021 |
| ADR-006 | Service Isolation | Accepted | (foundation) | Grandfathered | — |
| ADR-007 | Operating System Strategy | Accepted | (foundation) | Grandfathered | — |
| ADR-008 | Incremental Infrastructure Growth | Accepted | (foundation) | Grandfathered | — |
| ADR-009 | Identity Management Strategy | Accepted | (foundation) | Grandfathered | — |
| ADR-010 | Certificate Strategy | Accepted | (foundation) | Grandfathered | — |
| ADR-011 | Repository Strategy | Accepted | (foundation) | Grandfathered | — |
| ADR-012 | Documentation Standard | Accepted | (foundation) | Grandfathered | — |
| ADR-013 | Diagram Standard | Accepted | (foundation) | Grandfathered | — |
| ADR-014 | Backup Philosophy | Accepted | (foundation) | Grandfathered | — |
| ADR-015 | Logging Strategy | Accepted | (foundation) | Grandfathered | — |
| ADR-016 | Monitoring Strategy | Accepted | (foundation) | Grandfathered | — |
| ADR-017 | Security by Design | Accepted | (foundation) | Grandfathered | — |
| ADR-018 | Automation Philosophy | Accepted | (foundation) | Grandfathered | — |
| ADR-019 | Cloud Adoption Strategy | Accepted | (foundation) | Grandfathered | — |
| ADR-020 | Infrastructure Philosophy | Accepted | (foundation) | Grandfathered | — |
| ADR-021 | Single Authoritative IP Address Allocation Policy (Ch. 8B §8) | Accepted | 2026-07-13 | STD-ADR-001 compliant | Supersedes ADR-005 |
| ADR-022 | Canonical Engineering Lifecycle (Ch. 5 §5.2) | Accepted | 2026-07-13 | STD-ADR-001 compliant | — |
| ADR-023 | Repository Access and Commit Authority | Accepted | 2026-07-27 | STD-ADR-001 compliant | — |
| ADR-024 | VirtualBox Internal Network Naming Convention | Accepted | 2026-08-08 | STD-ADR-001 compliant | — |

ADR-001–ADR-020 reside in Chapter 8A — Foundational Architecture Decisions.
ADR-021 onward reside as individual documents in the /adr repository
directory.

## 5. Change History

| Version | Date | Description |
|---|---|---|
| 1.0 | 2026-07-13 | Initial Register: foundational ADR-001–020 recorded as grandfathered; ADR-021, ADR-022 recorded; next available identifier set to ADR-023. |
| 1.1 | 2026-07-27 | ADR-023 recorded; next available identifier set to ADR-024. |
| 1.2 | 2026-08-08 | ADR-024 recorded; next available identifier set to ADR-025. |
