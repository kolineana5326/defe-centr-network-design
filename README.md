# National Defense Command and Operations Center Network Architecture Design

## Project Overview
This project simulates the network design for a new three-story National Defense Command and Operations Center. The goal was to build a secure, and redundant network infrastructure from scratch to support 500 personnel.

The design adheres to the **Cisco Three-Tier Hierarchical Model** to ensure scalability and high availability for critical command operations.

## Topology Details
* **Facility:** 3 Stories, 5 Departments + Data Center.
* **Users:** Approx. 500 total (100 per department).
* **Simulation Tool:** Cisco Packet Tracer.

## Technical Specifications

### 1. Network Segmentation (VLANs & Subnetting)
The base private network -`172.16.1.0`. the network is segmented into VLANs to ensure operational isolation.

| Department | Floor | VLAN ID | Subnet |
| :--- | :--- | :--- | :--- |
| Operations & Tactical Planning | 1 | 10 | 172.16.2.0/25 |
| Logistics & Supply Command | 1 | 20 | 172.16.2.128/25 |
| Finance & Military Accounts | 2 | 30 | 172.16.3.0/25 |
| Civil-Military Affairs & Public Info| 2 | 40 | 172.16.3.128/25 |
| Cyber Defense & Comm (ICT) | 3 | 50 | 172.16.4.0/25 |
| Secure Data Center | 3 | 60 | 172.16.4.128/27 |

### 2. High Availability & Redundancy
* **Core Layer:** Two Multilayer Switches (Layer 3) acting as the main routing backbone.
* **Edge Layer:** Two routers connected to dual ISPs for uninterrupted external connectivity.
* **Routing Protocol:** **OSPF** (Open Shortest Path First) is configured on all routers.


### 3. Security Measures
* **Port Security:** Implemented on the *Finance & Military Accounts* switches. Restricted to one MAC address per port with `shutdown` violation mode to prevent unauthorized device connection.
* **Management:** Secure **SSH** enabled for remote administration; Telnet is disabled.
* **NAT/PAT:** NAT Overload (PAT) is configured on the edge routers to allow private VLANs to access the internet using assigned public IP addresses.
* **Access Control:** ACLs are implemented to restrict traffic between departments and manage access to the secure Data Center.

### 4. DHCP Services
Centralized DHCP servers located in the Data Center automatically assign IP addresses to all user devices on the 1st, 2nd, and 3rd floors, while servers utilize static IP addressing.

## How to View
1.  Download [Cisco Packet Tracer](https://www.netacad.com/).
2.  Open the file `defence&op_center.pkt` within this repository.
---
---
**Developed by:** KOLINEANA
