# MAGI Research Question and Project Scope

## Working Research Question

How can a modular cybersecurity homelab be designed and evaluated to combine
network segmentation, virtualization, centralized security monitoring, secure
remote administration, isolated security testing, and selective automation
while remaining manageable by a single administrator?

## Project Purpose

MAGI Infrastructure is a cybersecurity homelab designed to provide a practical
environment for learning and evaluating server administration, networking,
virtualization, security monitoring, penetration testing, and infrastructure
automation.

Rather than treating these technologies as unrelated systems, MAGI will
integrate them into a single modular environment in which infrastructure,
security controls, monitoring, and testing can interact with one another.

The project will focus not only on building the environment, but also on
documenting the design decisions, testing whether the intended security controls
work, and evaluating whether the environment can remain practical for one
administrator to operate.

## Research Objectives

The primary objectives of MAGI are to:

1. Design a modular infrastructure that can be expanded as additional systems
   and services are introduced.

2. Separate systems and services into logical network segments based on their
   purpose and level of trust.

3. Use virtualization to host infrastructure and security services while
   maintaining appropriate separation between them.

4. Centralize security monitoring so activity from multiple MAGI systems can be
   collected, reviewed, and evaluated from one location.

5. Provide secure remote administration of MAGI systems without requiring
   direct physical access to each machine.

6. Create an isolated environment where authorized penetration-testing activity
   can be performed without exposing unrelated systems.

7. Automate selected monitoring and administrative tasks where automation can
   reduce repetitive work without removing necessary administrator control.

8. Document the environment, configuration decisions, tests, and results well
   enough that the design and evaluation process can be reproduced and reviewed.

## Project Scope

MAGI will focus on a small cybersecurity homelab operated by a single
administrator.

The project may include:

- Firewall and gateway services
- Managed switching and network segmentation
- VLANs and access-control rules
- Virtualization
- Infrastructure services
- DNS filtering
- Centralized security monitoring and SIEM
- Secure remote administration
- An isolated penetration-testing environment
- Monitoring and administrative scripts
- Notifications and selected automation
- Repeatable security and connectivity tests

Specific products, hardware roles, addressing schemes, and implementation
details will be selected through later project issues.

## Project Boundaries

MAGI is not intended to:

- Reproduce a full enterprise production network.
- Provide public penetration-testing infrastructure.
- Test systems that are not owned by or specifically authorized for the MAGI
  environment.
- Automate every administrative or security decision.
- Remove human review from security-sensitive actions.
- Guarantee protection against every possible attack or failure.
- Require every available MAGI system or technology to be used if it does not
  contribute to the research objectives.

All penetration testing and controlled security activity will remain inside the
authorized MAGI environment.

## Evaluation Areas

The final MAGI environment will be evaluated at a high level in the following
areas:

### Network Segmentation

Verify that intended network segments can communicate where permitted and are
restricted where communication should not occur.

### Security Monitoring

Generate controlled security-relevant activity and determine whether the
monitoring environment records and exposes the expected events.

### Remote Administration

Verify that authorized systems can be administered remotely through the intended
management methods while maintaining appropriate access restrictions.

### Security Testing

Perform controlled tests from the isolated penetration-testing environment and
document the behavior of the relevant security controls and monitoring systems.

### Automation

Evaluate whether selected automated tasks operate consistently and whether they
reduce repetitive administrative work without taking inappropriate control away
from the administrator.

### Reproducibility

Document the architecture, configurations, procedures, and results so that
important tests and project decisions can be reviewed and repeated.

## Current Status

This document defines the working research question, objectives, scope, and
boundaries for MAGI Infrastructure.

The specific architecture, hardware roles, products, IP addressing, VLAN design,
and implementation details will be determined through later project issues.