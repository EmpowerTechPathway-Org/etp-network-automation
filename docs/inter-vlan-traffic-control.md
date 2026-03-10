# Secure Inter-VLAN Traffic Control Model for Hospital Enterprise

## VLAN Definitions

Hospital environments require strict network separation.

| VLAN | Name | Purpose |
|-----|------|---------|
| VLAN 10 | User VLAN | Staff computers |
| VLAN 20 | Server VLAN | Hospital servers |
| VLAN 30 | Medical Devices VLAN | Patient equipment |
| VLAN 40 | Guest VLAN | Public WiFi |
| VLAN 50 | Management VLAN | Network admin systems |

---

## Layer 3 Routing Controls

Inter-VLAN routing must be controlled via Layer 3 devices such as:

- Layer 3 Switch
- Internal Firewall

Routing rules must enforce security policies.

Default policy:

- Deny all traffic
- Allow only required communications

---

## Firewall Enforcement Points

Firewall should be placed between VLANs.

Enforcement areas:

- Between User VLAN and Server VLAN
- Between User VLAN and Medical Devices VLAN
- Block Guest VLAN access to internal VLANs
- Protect Management VLAN

Firewall provides:

- Traffic inspection
- Policy enforcement
- Threat prevention

---

## Example ACL Logic

Example rules:

Allow users to access application servers:
ALLOW VLAN10 → VLAN20 TCP 443
ALLOW VLAN10 → VLAN20 TCP 80

Allow medical devices to communicate with medical servers:
ALLOW VLAN30 → VLAN20 TCP 104 (DICOM)

Block guest access to internal networks:
DENY VLAN40 → VLAN10
DENY VLAN40 → VLAN20
DENY VLAN40 → VLAN30
DENY VLAN40 → VLAN50

Allow admin access:
ALLOW VLAN50 → ALL

---

## Traffic Restrictions Between Zones

| Source | Destination | Allowed |
|------|-------------|---------|
| User | Server | Yes |
| User | Medical Devices | No |
| Guest | Internal Networks | No |
| Medical Devices | Servers | Yes |
| Management | All | Yes |

Principle used: Least Privilege

---

## Monitoring and Logging Points

Monitoring systems include:

- Firewall logs
- IDS/IPS sensors
- NAC authentication logs
- SIEM logging

Benefits:

- Detect unauthorized access
- Monitor device behavior
- Enable incident response

---

## Network Diagram
                  Internet 
                      |
                      | (WAN)
                      |
               +--------------+
               | Edge Firewall|
               +--------------+
                      |
                      | (LAN / Trunk)
                      |
               +--------------+
               | Core Switch  |
               +--------------+
                 /    |    \
               /      |      \
             /        |        \
    +----------+ +----------+ +-------------+
    | Access   | | Access   | | Datacenter  |
    | Switch 1 | | Switch 2 | | Switch      |
    +----------+ +----------+ +-------------+
         |            |              |
    +----------+ +----------+ +-------------+
    | Endpoints| | Wi-Fi    | | Servers     |
    | (PCs)    | | (APs)    | | (Web/DB)    |
    +----------+ +----------+ +-------------+
---

## Summary

Secure inter-VLAN traffic control ensures:

- Protection of sensitive patient data
- Isolation of medical devices
- Restricted guest access
- Controlled user access
- Full administrative visibility
