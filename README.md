# 🚀 CCNA Lab 5 – Enterprise Network Design (Multi-Floor Architecture)

## 📌 Overview

This lab demonstrates the design and implementation of a full enterprise network across multiple floors using a hierarchical architecture (Core, Distribution, Access layers).

It integrates VLAN segmentation, inter-VLAN routing using SVI, dynamic routing using OSPF, centralized services (DHCP, Web, Email), and secure access mechanisms like SSH.

---

## 🧠 Problem Statement

In an enterprise environment:

* Multiple departments exist across different floors
* Network must be scalable and easy to manage
* Services should be centralized
* Secure access is required

Challenges:

* Managing large network ❌
* Ensuring communication between departments ❌
* Maintaining scalability and performance ❌

Solution:

* Hierarchical network design
* VLAN segmentation
* Dynamic routing (OSPF)
* Centralized services

---

## 🎯 Objective

* Design a hierarchical network (Core, Distribution, Access)
* Create VLANs for multiple departments
* Implement inter-VLAN routing using SVI
* Configure OSPF for dynamic routing
* Deploy centralized servers (DHCP, HTTP, Email)
* Enable SSH for secure device access
* Provide wireless connectivity

---

## 🌐 Network Design

### 🔹 Layers

* **Core Layer** → High-speed routing between floors
* **Distribution Layer** → VLAN routing and policy control
* **Access Layer** → End device connectivity

---

### 🔹 VLAN Allocation (Example)

| VLAN | Department | Network        |
| ---- | ---------- | -------------- |
| 10   | IT         | 192.168.1.0/24 |
| 20   | Admin      | 192.168.2.0/24 |
| 30   | HR         | 192.168.3.0/24 |
| 40   | Finance    | 192.168.4.0/24 |
| 50   | Sales      | 192.168.5.0/24 |
| 60   | Reception  | 192.168.6.0/24 |
| 70   | Store      | 192.168.7.0/24 |
| 80   | Logistics  | 192.168.8.0/24 |

---

### 🔹 Server Network

| Service | IP Address    |
| ------- | ------------- |
| DHCP    | 192.168.100.2 |
| Web     | 192.168.100.3 |
| Email   | 192.168.100.4 |

---

## ⚙️ How It Works (Concept Explanation)

### 🔹 VLAN Segmentation

* Separates departments logically
* Reduces broadcast traffic

### 🔹 SVI (Layer 3 Switching)

* Each VLAN has a gateway on the switch
* Enables fast inter-VLAN routing

### 🔹 OSPF

* Dynamic routing protocol
* Automatically shares routes across floors

### 🔹 DHCP

* Centralized IP address assignment

### 🔹 SSH

* Secure remote access to devices

### 🔹 Hierarchical Design

* Improves scalability, performance, and troubleshooting

---

## 💻 Configuration Commands

---

### 🔹 Enable Layer 3 Routing

```id="l1a2b3"
conf t
ip routing
```

---

### 🔹 VLAN Creation

```id="l4c5d6"
vlan 10
vlan 20
vlan 30
vlan 40
vlan 50
vlan 60
vlan 70
vlan 80
```

---

### 🔹 SVI Configuration

```id="l7e8f9"
interface vlan 10
ip address 192.168.1.1 255.255.255.0
no shutdown

interface vlan 20
ip address 192.168.2.1 255.255.255.0
no shutdown
```

(Repeat for all VLANs)

---

### 🔹 Access Port Assignment

```id="l0g1h2"
interface range fa0/1 - 10
switchport mode access
switchport access vlan 10
```

---

### 🔹 Trunk Configuration

```id="l3i4j5"
interface fa0/24
switchport mode trunk
```

---

### 🔹 OSPF Configuration

```id="l6k7l8"
router ospf 1
network 192.168.0.0 0.0.255.255 area 0
```

---

### 🔹 DHCP Configuration

```id="l9m0n1"
ip dhcp pool IT
network 192.168.1.0 255.255.255.0
default-router 192.168.1.1
```

---

### 🔹 SSH Configuration

```id="l2o3p4"
hostname CORE
ip domain-name enterprise.local
username admin secret Cisco@123

crypto key generate rsa
1024

ip ssh version 2

line vty 0 4
login local
transport input ssh
```

---

## 🔍 Verification Commands

```id="l5q6r7"
show vlan brief
show interfaces trunk
show ip interface brief
show ip route
show ip ospf neighbor
show ip dhcp binding
show ip ssh
```

---

## 📊 Result

✅ VLANs working across all floors
✅ Inter-VLAN communication enabled via SVI
✅ OSPF routing between layers working
✅ Devices receiving IP automatically
✅ Centralized services accessible
✅ Secure SSH access working

---

## ⚠️ Issues Faced & Solution

### ❌ Issue:

* Routing between floors failed

### 🔍 Cause:

* OSPF not properly configured

### ✅ Fix:

* Corrected network statements

---

### ❌ Issue:

* Devices not getting IP

### 🔍 Cause:

* DHCP pool misconfiguration

### ✅ Fix:

* Verified network and gateway

---

## 💡 Key Learnings

* Importance of hierarchical network design
* How SVI improves performance over ROAS
* Benefits of dynamic routing
* Role of centralized services in enterprise networks
* Importance of secure access

---

## 🎯 Real-World Use Case

* Corporate office networks
* Data centers
* Multi-floor enterprise buildings

---

## 🚀 Conclusion

This lab represents a complete enterprise-level network design integrating segmentation, routing, and services. It provides hands-on experience with real-world networking concepts required for a network engineer role.
