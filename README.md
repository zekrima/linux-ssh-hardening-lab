# linux-ssh-hardening-lab
Ubuntu Server 22.04 – Secure SSH &amp; Network Baseline (VirtualBox Lab)

🔐 Linux Server Hardening Project

Ubuntu Server 22.04 – Secure SSH & Network Baseline (VirtualBox Lab)

📌 Project Overview

This project demonstrates a step-by-step Linux server hardening implementation using Ubuntu Server 22.04 deployed on Oracle VirtualBox.
The focus of this phase is establishing a secure network baseline and implementing SSH access hardening following industry best practices.

The lab is designed to simulate real-world server security scenarios commonly encountered in SOC, Cloud Security, and Linux Administration roles.

🎯 Objectives

Build a secure Ubuntu Server lab environment

Apply proper network segmentation and access control

Harden SSH access to reduce attack surface

Implement cryptographic-based authentication (SSH Key)

Prepare a foundation for further security controls (Fail2ban, logging, auditing)

🧱 Environment Details
Component	Configuration
Host OS	Linux Desktop
Hypervisor	Oracle VirtualBox
Guest OS	Ubuntu Server 22.04 LTS
VM Network	NAT + Host-Only Adapter
Access Method	SSH
🧩 Project Phases
🔹 Phase 1 – Network Baseline & Secure Connectivity
Implemented Controls:

Dual network interface configuration:

Adapter 1 (NAT): Outbound internet access (updates, packages)

Adapter 2 (Host-Only): Secure management access

Static IP configuration for management interface

Single management IP enforced (duplicate IP removed)

SSH access bound to management network only

Outcome:

Server isolated from external LAN

Controlled access path for administration

Clear separation between outbound traffic and management access

🔹 Phase 2 – SSH Access Hardening
Implemented Controls:

SSH service validation and listening verification

Root login via SSH fully disabled

SSH access restricted using AllowUsers

Administrative access enforced via sudo

Configuration validated using runtime SSH inspection (sshd -T)

Key Security Decisions:

Root account remains disabled for remote access

Only authorized non-root user can initiate SSH sessions

🔹 Phase 3 – SSH Cryptography Hardening (Stage 1)
Implemented Controls:

SSH key-based authentication using Ed25519

Secure key pair generation on host machine

Public key deployed to server (authorized_keys)

Passwordless SSH login validated

File and directory permissions enforced:

~/.ssh → 700

authorized_keys → 600

Security Rationale:

Eliminates password exposure during authentication

Prevents brute-force and credential-stuffing attacks

Aligns with production-grade SSH security standards

🔍 Validation & Verification

Network configuration verified using:

ip a

ip route

SSH runtime configuration verified using:

sshd -T

File permission integrity verified on authentication artifacts

🛡️ Security Principles Applied

Least privilege

Secure defaults

Attack surface reduction

Defense-in-depth (foundation stage)

🚀 Next Planned Improvements

(To be implemented in next phase)

Disable SSH password authentication completely

Fail2ban for brute-force protection

Centralized logging & SSH event analysis

Auditd integration

CIS Benchmark alignment
