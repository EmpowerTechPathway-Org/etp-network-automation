# Zero-Trust Network Model for Enterprise Segmentation

## Definition of Zero-Trust in Networking

Zero-Trust is a security model based on the principle of:

> "Never trust, always verify."

Key concepts:

- No device, user, or system is trusted by default
- Every access request must be authenticated and authorized
- Access is granted based on identity, device posture, and policy
- Continuous verification is required

Zero-Trust assumes breaches can occur both externally and internally.

---

## Why Perimeter Security is Insufficient

Traditional perimeter-based security assumes internal networks are trusted.

This model fails because:

- Attackers can bypass perimeter defenses via phishing or compromised credentials
- Insider threats exist within trusted networks
- Malware can spread laterally once inside
- Cloud services extend beyond traditional network boundaries

Zero-Trust eliminates implicit trust inside the network.

---

## Role of VLAN Segmentation

VLANs provide logical separation of network traffic.

Benefits:

- Isolates user groups and systems
- Limits broadcast domains
- Reduces lateral movement opportunities
- Creates defined security zones

Example VLAN segmentation:

- VLAN 10 – Users
- VLAN 20 – Servers
- VLAN 30 – Management
- VLAN 40 – Guest
- VLAN 50 – Critical Systems

VLANs form the foundation for policy enforcement.

---

## Role of Firewalls

Firewalls enforce security policies between network segments.

Functions:

- Inspect traffic between VLANs
- Allow or deny traffic based on rules
- Prevent unauthorized lateral movement
- Monitor traffic patterns

Types:

- Edge Firewall – protects external boundary
- Internal Segmentation Firewall (ISFW) – protects internal zones

---

## Role of Identity-Aware Access

Access decisions are based on identity, not just IP address.

Identity factors include:

- User authentication (Active Directory, MFA)
- Device compliance status
- User role and permissions
- Device certificate validation

Benefits:

- Prevents unauthorized device access
- Limits access based on least privilege
- Provides accountability

---

## Microsegmentation Concept

Microsegmentation divides the network into smaller security zones.

Benefits:

- Limits attacker movement
- Protects critical workloads
- Provides granular access control

Example:

- Database servers only accept traffic from application servers
- Management systems accessible only by admin VLAN

---

## Logging and Inspection Requirements

Visibility is critical in Zero-Trust.

Required logging systems:

- Firewall logs
- Authentication logs
- IDS/IPS alerts
- NAC logs
- Network flow logs

Benefits:

- Detect malicious activity
- Enable incident response
- Provide forensic analysis

Logs should be centralized in a SIEM.


---

## Summary

Zero-Trust improves enterprise security by:

- Eliminating implicit trust
- Enforcing identity-based access
- Using VLAN segmentation and firewalls
- Implementing microsegmentation
- Providing continuous monitoring and logging
---

## Zero-Trust Architecture Diagram
```text
                        [ Untrusted / External ]
                                  |
                           +--------------+
                           | Identity &   | (MFA, Device Health)
                           | Access Proxy |
                           +------+-------+
                                  |
                                  v
+-------------------------------------------------------------------+
|                  ZERO-TRUST ENFORCEMENT BOUNDARY                  |
|                      (Next-Gen Firewall)                          |
+----+----------------------------+----------------------------+----+
     |                            |                            |
     v                            v                            v
[ VLAN 10 ]                  [ VLAN 20 ]                  [ VLAN 30 ]
 HR Users                    App Servers                  Dev Workloads
     |                            |                            |
  +--+--+                      +--+--+                      +--+--+
  | Host| (Microsegmentation)  | Host|                      | Host|
  +-----+                      +-----+                      +-----+
