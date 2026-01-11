SSH Hardening Notes – Ubuntu Server 22.04
1. Baseline SSH State

Default SSH configuration on Ubuntu Server allows password-based authentication and does not restrict users explicitly.
This baseline is functional but exposes the service to brute-force and credential-based attacks.

2. SSH Service Validation

The SSH service was validated to ensure it was active and properly listening on the intended interface.

Validation steps:

Service status verification

Listening socket inspection

Network interface binding confirmation

This ensures SSH behavior matches the intended network design.

3. Access Control Hardening

The following access restrictions were applied:

Remote root login via SSH was fully disabled

SSH access restricted to a single non-root administrative user

Privilege escalation enforced via sudo

This approach enforces least privilege and prevents direct high-risk access paths.

4. Cryptographic Authentication (Stage 1)

SSH key-based authentication was implemented using Ed25519 keys.

Controls applied:

Secure key pair generation on the host machine

Public key deployment to the server

Passwordless SSH login validated

Secure permissions enforced on SSH authentication artifacts

Password-based authentication remains temporarily enabled at this stage to ensure safe access continuity.

5. Validation Commands

Key validations performed:

sshd -T | grep -E "permitrootlogin|allowusers"
ip a
ip route
ls -ld ~/.ssh
ls -l ~/.ssh/authorized_keys


Runtime configuration inspection was preferred over static file review to avoid false assumptions.

6. Security Impact Summary
Control	Security Impact
Root SSH disabled	Eliminates high-value attack vector
User restriction	Reduces unauthorized access risk
SSH key auth	Prevents brute-force password attacks
Secure permissions	Protects authentication integrity
Notes

Further hardening steps (password authentication disablement, brute-force protection, logging, and auditing) will be implemented in subsequent phases.
