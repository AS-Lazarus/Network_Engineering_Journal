# 📡 Network Engineering Lab Log

## Lab 01: IPv4/IPv6 Dual Stack & Device Hardening
**Date:** Feb 5, 2026
**Status:** ✅ Success

### 🎯 Objective
To configure a dual-stack network (IPv4/IPv6) with inter-subnet communication while securing the network devices against unauthorized access.


### 📊 IP Addressing Plan (VLSM)
**Base Network:** `172.16.0.0/24`

| Subnet | Description | CIDR | Network Address | Gateway (R1) | Host Range | Broadcast |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| **A** | Left LAN (100 Hosts) | `/25` | `172.16.0.0` | `172.16.0.1` | `.2` - `.126` | `.127` |
| **B** | Right LAN (50 Hosts) | `/26` | `172.16.0.128` | `172.16.0.129` | `.130` - `.190` | `.191` |

**IPv6 Configuration:**
* **Global Prefix:** `2001:db8:acad::/48`
* **Subnet A:** `2001:db8:acad:A::/64`
* **Subnet B:** `2001:db8:acad:B::/64`

### 🛠️ Key Technologies Used
* **Subnetting:** VLSM implementation for /25 and /26 blocks.
* **Routing:** IPv6 Unicast Routing & Link-Local interactions.
* **Security:** SSH implementation (RSA 1024-bit) and VTY line protection.
* **Tools:** Cisco Packet Tracer.

### 📸 Topology
![Topology Screenshot](https://github.com/user-attachments/assets/7001c16c-69c6-429e-9f25-05655e8a7b0c)

### 🚀 Implementation Highlights
* **Challenge:** The router initially dropped IPv6 packets between subnets.
* **Solution:** Diagnosed missing `ipv6 unicast-routing` command. Enabled it to restore Layer 3 forwarding.
* **Verification:** Successful pings between PC-A and PC-B across both protocol stacks.

### 📸 Verification 
![Verification Screenshot](https://github.com/AS-Lazarus/Network_Engineering_Journal/blob/main/Labs/verification.jpg)
