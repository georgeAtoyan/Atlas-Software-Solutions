

PROJECT_CONTEXT.md
## Atlas Software Solutions
## Project Context
## Version: 0.1
## Status: Active Development
## Last Updated: July 2026
## Purpose
This document provides the current operational context of the Atlas Software Solutions Engineering
## Blueprint.
Unlike the Blueprint, which defines long-term engineering philosophy and standards, this document
reflects the current state of the project.
It should be updated whenever the infrastructure, architecture, backlog or engineering priorities change.
This document is intended to provide immediate context to the Technical Lead without requiring a review of
the entire Blueprint.
## Project Vision
Atlas Software Solutions is a fictional software company created as the foundation for a long-term
Infrastructure Engineering project.
The objective is to simulate the complete lifecycle of designing, implementing, operating and improving a
professional Linux-based infrastructure.
The project is designed to prepare the learner for a Junior Linux System Administrator role while building
habits expected from professional Infrastructure Engineers.
Learning is driven by engineering work rather than isolated laboratory exercises.
## 1

## Primary Learning Goal
## Current Target Role:
## Junior Linux System Administrator
## Future Career Interests:
DevOps Engineering
## Cloud Engineering
## Cybersecurity
The current project focuses exclusively on building strong Linux and infrastructure fundamentals before
introducing advanced technologies.
## Engineering Philosophy
The project follows several core principles:
Understanding before implementation.
Business requirements before technology.
Incremental infrastructure growth.
Security by design.
Documentation as part of engineering.
Architecture before implementation.
Simplicity over unnecessary complexity.
Continuous improvement.
Progress is measured by understanding rather than speed.
## Technical Lead Responsibilities
The Technical Lead is expected to:
guide engineering decisions;
review proposed solutions;
validate architectural consistency;
encourage independent reasoning;
identify knowledge gaps;
require documentation;
conduct engineering reviews;
avoid solving problems immediately;
## •
## •
## •
## •
## •
## •
## •
## •
## •
## •
## •
## •
## •
## •
## •
## •
## •
## •
## •
## 2

teach professional engineering thinking.
The Technical Lead should behave as a senior infrastructure engineer mentoring a junior team member.
## Current Infrastructure Status
## Infrastructure State:
## Planning Phase
## Current Architecture:
## Designed
## Infrastructure Deployment:
## Not Started
## Engineering Documentation:
## Established
## Engineering Standards:
## Established
## Engineering Workflow:
## Established
## Implementation Status:
Awaiting first Engineering Task.
## Current Engineering Phase
## Phase:
## Linux Foundations
## Status:
## •
## 3

Ready to Begin
## Current Priority:
Begin INF-001.
No engineering tasks have been completed yet.
## Infrastructure Overview
## Infrastructure Name:
## Atlas Software Solutions
## Primary Internal Domain:
atlas.lab
## Infrastructure Type:
Small software company
## Primary Platform:
Oracle VirtualBox
## Host Operating System:
## Windows 11
## Future Cloud Platform:
## AWS
## Primary Administration:
## SSH
PowerShell
## Visual Studio Code
## Git
## 4

## Markdown
## Current Architecture Decisions
The following architectural decisions have been approved.
## Network Architecture:
Multiple network segments.
## Internal Domain:
atlas.lab
## Documentation Language:
## English.
## Documentation Format:
## Markdown.
## Infrastructure Documentation:
Git repository.
## Operating Systems:
Debian Stable for core infrastructure.
Ubuntu Server LTS for application services.
Ubuntu Desktop for administrative workstation.
## Monitoring Stack:
## Prometheus + Grafana.
## Cloud Strategy:
## Hybrid Infrastructure.
## Architecture Evolution:
## 5

## Incremental.
These decisions are documented in the Foundational Architecture Decisions, ADR-001–ADR-020 (Chapter 8A). The authoritative index of all ADRs is the ADR Register (ADR-REGISTER.md).
## Infrastructure Standards
Current standards include:
## Engineering Principles
## Engineering Workflow
Engineering Task Specification (ETS)
## Infrastructure Architecture
## Architecture Decision Records (Foundational: Chapter 8A; Standard: STD-ADR-001; Index: ADR Register)
## Engineering Backlog
All future Engineering Tasks must comply with these documents.
## Current Repository Structure
The Engineering Blueprint repository currently contains:
## Engineering Handbook
## Architecture
## Engineering Standards
## Engineering Roadmap
## Engineering Tasks
## Runbooks
## Templates
The Engineering Tasks directory is currently empty.
## 6

## Current Engineering Backlog
## Next Engineering Task:
## INF-001
## Build Administrative Workstation
## Status:
## Ready
Subsequent tasks include:
## INF-002
## Deploy Debian Router
## NET-001
## Configure Internal Networks
## NET-002
Routing & NAT
## NET-003
## Packet Flow Validation
## NET-004
Primary DNS
Engineering Tasks should be completed according to dependency order.
## Documentation Status
## Completed Documents:
## Vision & Learning Philosophy•
## 7

## Engineering Principles
## The Company
## Infrastructure Evolution Strategy
## Engineering Workflow
## Technical Lead Operating Manual
## The Infrastructure Engineer
Foundational Architecture Decisions (ADR-001–ADR-020, Chapter 8A)
## Infrastructure Architecture
## Engineering Task Specification
## Engineering Backlog
## Planned Documents:
## Repository Standards
## Runbook Standards
ADR Template
## Incident Management
## Disaster Recovery
## Monitoring Standards
These documents will be created when required by future Engineering Tasks.
## Current Technical Constraints
## Host Hardware:
Intel Core i5-11300H
## 16 GB RAM
Approximately 200 GB free storage
Virtual Machines are created as needed.
Normally, no more than three or four virtual machines are expected to run simultaneously.
Engineering Tasks should respect these practical hardware constraints while preserving realistic
infrastructure architecture.
## •
## •
## •
## •
## •
## •
## •
## •
## •
## •
## •
## •
## •
## •
## •
## •
## 8

## Learning Approach
The learner prefers:
deep understanding over rapid progress;
architecture before implementation;
practical engineering over memorization;
professional documentation;
realistic business scenarios;
incremental infrastructure growth.
A topic should not be considered complete until the learner understands not only how it works but also why
it exists and when it should be used.
## Technical Lead Guidelines
## Always:
follow the Engineering Blueprint;
review architecture before implementation;
verify conceptual understanding;
encourage reasoning;
request documentation;
promote engineering discipline.
## Never:
skip prerequisite knowledge;
provide unnecessary complexity;
introduce technologies prematurely;
optimize for speed instead of understanding.
## Current Objectives
## Immediate Objectives:
Begin Engineering Task INF-001.
Build the administrative workstation.
Establish the first operational infrastructure environment.
## •
## •
## •
## •
## •
## •
## •
## •
## •
## •
## •
## •
## •
## •
## •
## •
## 1.
## 2.
## 3.
## 9

Begin practical Linux administration.
Long-Term Objective:
Design, build and operate a professional Linux infrastructure that demonstrates the technical and
engineering competencies expected from a Junior Linux System Administrator.
## Operational Status
## Blueprint:
## Established
## Architecture:
## Approved
## Engineering Standards:
## Approved
## Backlog:
## Established
## Technical Lead Guidance:
## Established
## Infrastructure:
## Not Yet Built
## Current Project Status:
Ready to Begin Engineering Work.
## 4.
## 10

## Change History

|Version|Date|Description|
|---|---|---|
|0.1|July 2026|Initial version|
|0.2|2026-07-13|ADR references corrected per AUD-C-04 ("ADR-000"/"Infrastructure Decision Record" retired). Targeted correction only; broader content staleness (AUD-M-01) remains open under DOC-010.|
