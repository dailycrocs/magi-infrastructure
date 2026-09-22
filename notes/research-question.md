# MAGI Research Question

## Working Research Question

How can a modular cybersecurity homelab be designed to combine network
segmentation, virtualization, centralized security monitoring, secure remote
administration, and selective automation while remaining manageable by a
single administrator?

## Project Purpose

MAGI Infrastructure is intended to provide a hands-on cybersecurity environment
for learning and testing server administration, networking, virtualization,
security monitoring, penetration testing, and infrastructure automation.

Rather than building a collection of unrelated systems, MAGI will be designed
as an interconnected environment in which networking, infrastructure services,
monitoring, testing, and automation work together.

## Research Objectives

The project will investigate how a small homelab can:

1. Separate systems into logical network segments based on purpose and trust.
2. Host infrastructure and security services through virtualization.
3. Collect and review security information from multiple systems centrally.
4. Provide secure remote administration of the environment.
5. Maintain an isolated environment for controlled penetration testing.
6. Automate selected monitoring and administrative tasks without removing
   administrator control from sensitive security decisions.

## Evaluation Areas

MAGI will be evaluated using repeatable tests in several areas:

### Network Segmentation

Verify whether systems in separate MAGI network segments can communicate only
when permitted by the firewall and network design.

### Security Monitoring

Generate controlled events and determine whether the centralized monitoring
platform receives and identifies the expected activity.

### Remote Administration

Verify that MAGI can be securely administered remotely without unnecessarily
exposing management interfaces.

### Automation

Evaluate whether selected repetitive monitoring or administrative tasks can be
performed automatically while still providing useful information to the
administrator.

### Reproducibility

Document configurations, tests, and results so that important project behavior
can be reproduced and explained from the repository.

## Scope

MAGI focuses on the design and evaluation of a small cybersecurity homelab.

The project is not intended to reproduce a full enterprise environment or to
automate every administrative or security decision. Automation will be added
selectively after the underlying services have been tested and shown to operate
correctly.

All penetration testing will be performed only against systems created and
authorized for use inside the private MAGI environment.

## Status

This research question is a working version and may be refined as the
architecture and implementation develop.