# 📡 Network Engineering Lab Log

## Lab 01: IPv4/IPv6 Dual Stack & Device Hardening
**Date:** Feb 5, 2026
**Status:** ✅ Success

### 🎯 Objective
To configure a dual-stack network (IPv4/IPv6) with inter-subnet communication while securing the network devices against unauthorized access.

### 🛠️ Key Technologies Used
* **Subnetting:** VLSM implementation for /25 and /26 blocks.
* **Routing:** IPv6 Unicast Routing & Link-Local interactions.
* **Security:** SSH implementation (RSA 1024-bit) and VTY line protection.
* **Tools:** Cisco Packet Tracer.

### 📸 Topology
![Topology Screenshot](Link_to_your_image.png)
*(Note: After you upload the image, you can click "Raw" on the image file to get the link to paste here)*

### 🚀 Implementation Highlights
* **Challenge:** The router initially dropped IPv6 packets between subnets.
* **Solution:** Diagnosed missing `ipv6 unicast-routing` command. Enabled it to restore Layer 3 forwarding.
* **Verification:** Successful pings between PC-A and PC-B across both protocol stacks.
