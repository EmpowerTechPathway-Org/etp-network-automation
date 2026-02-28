# Network Security Enforcement Points Model

## Overview

Enterprise networks require multiple inspection and enforcement layers.

Security must be applied at:

- Network edge
- Internal network segments
- Device access layer
- Traffic monitoring layer
- Logging and analytics layer

---

## Edge Firewall

Location:

Between Internet and enterprise network

Functions:

- Blocks unauthorized external traffic
- Performs NAT
- Filters inbound and outbound traffic
- Prevents external attacks

Inspects:

- Incoming internet traffic
- Outgoing enterprise traffic

---

## Internal Segmentation Firewall (ISFW)

Location:

Between internal VLANs and critical resources

Functions:

- Controls lateral movement
- Protects sensitive systems
- Enforces Zero-Trust policies

Example protections:

- User VLAN cannot access database directly
- Only application servers access database

---

## Network Access Control (NAC)

Location:

Access layer (switch level)

Functions:

- Authenticates devices before network access
- Verifies device compliance
- Assigns VLAN based on identity

Prevents:

- Unauthorized device access
- Rogue devices

---

## IDS/IPS (Intrusion Detection / Prevention)

Location:

Strategic inspection points in network

Functions:

- Detect malicious traffic
- Identify attacks
- Block threats automatically (IPS)

Monitors:

- Internal traffic
- External traffic
- Suspicious patterns

---

## Logging Systems

Collect logs from:

- Firewalls
- NAC
- Servers
- Network devices
- IDS/IPS

Functions:

- Record security events
- Provide audit trails
- Enable investigation

---

## SIEM Integration

SIEM provides centralized analysis.

Functions:

- Collect logs from all devices
- Correlate events
- Detect threats
- Generate alerts

Examples of events detected:

- Unauthorized access attempts
- Malware activity
- Suspicious login patterns

---

## Traffic Inspection Flow

Traffic is inspected at multiple layers:

1. Edge Firewall – External traffic inspection
2. NAC – Device authentication
3. Internal Firewall – Lateral traffic inspection
4. IDS/IPS – Threat detection
5. SIEM – Event correlation and alerting

---

## Architecture Diagram
<img width="508" height="490" alt="image" src="https://github.com/user-attachments/assets/b70fbd00-807a-433f-9338-802f6f157558" />


              
All logs forwarded to:
[SIEM System] Security Information Event Manger


---

## Summary

Security enforcement points ensure:

- Protection from external threats
- Prevention of lateral movement
- Device authentication
- Continuous monitoring
- Centralized threat detection

This layered model provides full enterprise security visibility.
  
