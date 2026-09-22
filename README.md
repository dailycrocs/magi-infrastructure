# MAGI Infrastructure

**MAGI — Modular Automated Grid Infrastructure**

MAGI Infrastructure is a cybersecurity homelab project designed to provide a
secure environment for learning server administration, networking, security
monitoring, penetration testing, virtualization, and automation.

The name MAGI is inspired by the MAGI supercomputer system from *Neon Genesis
Evangelion*. For this project, MAGI also represents **Modular Automated Grid
Infrastructure**, reflecting the project's focus on expandable hardware,
automation, interconnected systems, and infrastructure services.

## Project Goals

MAGI is being developed as a hands-on environment for learning and practicing:

- Virtualization
- Network security
- Network segmentation
- Security monitoring
- Penetration testing
- Server administration
- Infrastructure automation

The completed environment is planned to include a firewall, segmented networks,
virtualized infrastructure services, centralized security monitoring, an
isolated penetration-testing environment, DNS filtering, and selected automated
administrative tasks.

## Long-Term Goal

The long-term goal of MAGI is to become a largely self-monitoring and
selectively automated homelab.

Routine monitoring, health checks, reporting, backups, and other safe
administrative tasks will gradually be automated after the core network,
servers, monitoring, and testing environments are working correctly.

Important security actions will remain under administrator control unless they
have been tested and determined to be safe to automate.

## Hardware

MAGI currently uses three Dell OptiPlex systems, a 10ZiG thin client, and a
Raspberry Pi.

Detailed hardware information and planned system roles are maintained in the
[hardware inventory](docs/hardware/inventory.md).

## Current Status

**Current milestone: Scope, Research & Architecture**

The project is currently focused on documenting the available hardware,
defining system roles, establishing the research scope, evaluating major
technology choices, and designing the initial network architecture.

Project work is tracked through GitHub milestones and issues. Each substantial
task is developed on its own branch and reviewed before being merged into
`main`.

## Repository Structure

- `docs/` — Technical documentation for the MAGI environment
- `scripts/` — Reusable scripts that become part of MAGI
- `sandbox/` — Small experiments and proof-of-concept work
- `AGENTS.md` — Instructions for coding and AI agents
- `AGENT-LOG.md` — Substantial agent-assisted project work and verification

Additional research and paper directories will be added as their corresponding
project issues are completed.

## Documentation

Current documentation:

- [Hardware Inventory](docs/hardware/inventory.md)

More technical documentation will be added as the project progresses.

## Safety

All penetration testing will be performed inside the private MAGI homelab
against systems specifically created and authorized for testing.