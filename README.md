# MAGI Infrastructure
The MAGI Infrastructure is a cybersecurity homelab project designed to provide a secure environment for learning server administration, networking, security monitoring, penetration testing, and automation.

The goal of this project is to build a small home network that can be used to learn and practice:
- Virtualization
- Network Security
- Network Segmentation
- Security Monitoring
- Penetration Testing
- Server Management

This project will use several physical computers, including three Dell OptiPlex systems, a 10ZiG thing client, and a Raspberry Pi.

As the project is being developed, this repository will document each step, including hardware setup, operating system installation, 
networking, security tools, testing, troubleshooting, and final results.

## Project Goals

The completed homelab is planned to include:
- A system for running virtual computers
- A firewall for controlling network traffic
- Separate network areas for different types of systems
- A SIEM for collecting and monitoring security logs
- A safe environment for penetration testing
- A Raspberry Pi running Pi-hole for DNS filtering

## Long-Term Goal

The long-term goal of MAGI Infrastructure is to become a largely self-monitoring and automated homelab.

Instead of requiring constant manual security checks, the environment will eventually be designed to:

- Collect security logs automatically
- Detect suspicious activity
- Generate alerts for important security events
- Notify the administrator when attention is required
- Monitor the health of servers and services
- Perform scheduled backups
- Monitor storage and system resources
- Automate selected security responses when it is safe to do so

Security automation will be added gradually after the core network, servers, monitoring, and penetration-testing environment are working correctly.

Important security actions will remain under administrator control unless they have been tested and determined to be safe to automate.

## Physical Hardware
|    Name     | |        Hardware        |  |  Purpose  |
|  MELCHIOR   | |    Dell OptiPlex       |  |    TBD    |
|  BALTHASAR  | |    Dell OptiPlex       |  |    TBD    |
|  CASPER     | |    Dell OptiPlex       |  |    TBD    |
|  DOGMA      | |    10ZiG Thin Client   |  |    TBD    |
|  TBD        | |    Raspberry Pi        |  |    TBD    |

The exact purpose of each computer will be decided after the hardware has been inspected and documented.

## Current Status
**Phase 0: Planning and Hardware Inventory**

The project is currently in the planning state. The next step is to inspect and document the available hardware before installing or removing software.

## Documentation

Documentation will be added throughout the project and will include:
- Hardware installation
- Installation procedures
- Security configuration
- Testing
- Problems encountered
- Solutions
- Final results

## Safety
All penetration testing will be performed inside the private homelab against systems specifically created and authorized for testing.

