# 🏰 Lab 02: Secure Campus LAN Design

**Status:** Completed  ✅
**Focus:** SRWE (Switching, Routing, and Wireless Essentials)

### 🎯 Objective
To design and implement a redundant, segmented and secure Layer 2/3 campus network. This lab focuses on **High Availability (HA)** using EtherChannel and **Defense-in-Depth** security.

### 🛠️ Key Technologies Implemented
* **VLAN Segmentation:** Isolated Management, Operations, and Guest traffic.
* **Inter-VLAN Routing (ROAS):** Layer 3 communication via ISR 4331 Router-on-a-Stick.
* **LACP EtherChannel:** Bundled links (IEEE 802.3ad) for 2x bandwidth and redundancy.
* **Port Security:** "Sticky" MAC addresses to prevent unauthorized access.
* **VLAN Hopping Mitigation:** All unused ports assigned to "Blackhole VLAN 666" and shut down.
* **Tools:** Cisco Packet Tracer

---

### 📊 VLAN Architecture

| VLAN ID | Name | Subnet | Security Level |
| :--- | :--- | :--- | :--- |
| **10** | MGMT | `10.1.10.0/24` | **High** (Admins Only) |
| **20** | CORP | `10.1.20.0/24` | **Medium** (Employees) |
| **30** | GUEST | `10.1.30.0/24` | **Low** (Internet Only) |
| **999** | NATIVE | N/A | **Infrastructure** (Trunks Only) |
| **666** | BLACKHOLE | N/A | **Restricted** (Unused Ports) |

---

### 🔧 Key Configurations

#### **1. LACP EtherChannel (Core Switch S1)**
*Configures redundant 2Gbps uplink to Access Switches.*
```cisco
interface Port-channel1
 description TRUNK-TO-WEST
 switchport mode trunk
 switchport trunk native vlan 999
!
interface range FastEthernet0/1 - 2
 channel-group 1 mode active
```


#### **2. Router-on-a-Stick (Gateway R1)**
*Enables Inter-VLAN routing using 802.1Q encapsulation.*
```cisco
interface GigabitEthernet0/0/1.20
 description GATEWAY_CORP
 encapsulation dot1Q 20
 ip address 10.1.20.1 255.255.255.0
```

#### **3. Port Security (Access Switch S2)**
*Locks the port to the specific device MAC address to prevent unauthorized access.*
```cisco
interface FastEthernet0/10
 switchport mode access
 switchport port-security
 switchport port-security mac-address sticky
 switchport port-security violation shutdown
```

