# MAGI Methodology Plan

## Overview

MAGI Infrastructure will be developed incrementally through a series of
documented project milestones. Each major component will be researched,
implemented, tested, and reviewed before the project moves to later stages.

The project will use GitHub issues to define individual tasks and acceptance
criteria. Each substantial issue will be completed on its own branch, reviewed,
and merged into `main` after verification.

## Planned Project Phases

### 1. Scope, Research, and Architecture

Define the research question, document available hardware, assign preliminary
system roles, evaluate major technology choices, and create the initial network
and segmentation design.

### 2. Core Network and Firewall

Deploy the firewall and managed network infrastructure, implement network
segments, configure traffic-control rules, and verify connectivity and
isolation.

### 3. Virtualization and Infrastructure Services

Deploy the virtualization environment and core infrastructure services required
by MAGI.

### 4. Security Monitoring and SIEM

Deploy centralized security monitoring, connect MAGI systems, collect logs, and
verify that controlled events can be detected and reviewed.

### 5. Penetration Testing, Detection, and Automation

Create an isolated testing environment, perform controlled security tests,
evaluate detections, and introduce selected monitoring or administrative
automation.

### 6. Evaluation and Final Research

Repeat key tests, collect final results, document limitations, analyze findings,
and complete the research paper and project demonstration.

## Testing Approach

Tests will be designed with a defined purpose, expected result, procedure, and
observed result.

Where possible, testing will be repeatable so that results can be reproduced
from the documented MAGI configuration.

Examples may include:

- Testing permitted and blocked communication between network segments.
- Confirming that security events reach the monitoring platform.
- Comparing expected alerts with observed alerts.
- Testing remote administrative access.
- Checking whether automated monitoring identifies unavailable systems or
  services.

## Evidence

Project evidence may include:

- Configuration documentation
- Network diagrams
- Screenshots
- Command output
- Log entries
- Monitoring alerts
- Test results
- Scripts
- Git commits and tags

Results used in the research paper must be reproduced and verified before they
are reported as project findings.

## Agent-Assisted Work

AI and coding agents may assist with research organization, documentation,
scripts, configuration examples, troubleshooting, and other project work.

Substantial agent-assisted project contributions will be reviewed before
acceptance and recorded in `AGENT-LOG.md` when appropriate.

The project owner remains responsible for technical decisions, verification,
interpretation of results, and final conclusions.