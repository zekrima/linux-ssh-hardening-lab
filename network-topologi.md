Network Topology – Secure Linux Lab
1. Overview

This lab uses a dual-network interface design to separate management access from outbound connectivity, following common security practices in on-premise and cloud environments.

The topology is intentionally designed to reduce attack surface while maintaining operational access for administration.

2. Network Interfaces
Interface	VirtualBox Adapter	Purpose
enp0s3	NAT	Outbound internet access (updates, packages)
enp0s8	Host-Only Adapter	Secure management access from host
3. IP Addressing
Interface	Type	IP Address	Notes
enp0s3	DHCP	10.0.2.15/24	NAT-assigned, no inbound access
enp0s8	Static	192.168.56.102/24	Management interface

Only one management IP is configured to avoid ambiguity and reduce misconfiguration risks.

4. Access Flow

SSH Access Path:

Host Machine
   |
   | (SSH – TCP/22)
   |
Host-Only Network (192.168.56.0/24)
   |
   |
Ubuntu Server (192.168.56.102)


SSH access is restricted to the host-only network

No inbound access is exposed via NAT

Internet access is outbound-only

5. Security Considerations

No bridge networking is used to avoid exposing the VM directly to the physical LAN

NAT interface does not accept inbound connections

Management access is isolated to a trusted host network

Network segmentation supports the principle of least exposure

6. Future Improvements

Firewall rules to restrict SSH source IP

Network-based monitoring and logging

Simulation of attacker traffic for detection testing
