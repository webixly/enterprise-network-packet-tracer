# 🖧 Enterprise Network Simulation (Cisco Packet Tracer)

## 📌 Overview

This project demonstrates the design and implementation of a small enterprise network using Cisco Packet Tracer.
It includes VLAN segmentation, inter-VLAN routing, and access control to simulate a real-world network environment.

---

## 📸 Project Preview

![Topology](images/topology.png)

---

## 🏢 Network Structure

The network is divided into three departments:

* IT Department (VLAN 10)
* HR Department (VLAN 20)
* Sales Department (VLAN 30)

Each department operates in its own isolated network.

---

## 📊 Network Details

| VLAN | Department | Network         |
| ---- | ---------- | --------------- |
| 10   | IT         | 192.168.10.0/24 |
| 20   | HR         | 192.168.20.0/24 |
| 30   | Sales      | 192.168.30.0/24 |

---

## ⚙️ Features

* VLAN segmentation for network isolation
* Inter-VLAN routing using Router-on-a-Stick
* Access Control Lists (ACL) for traffic filtering
* Structured IP addressing scheme

---

## 🖼️ Network Topology

The topology includes:

* 1 Router
* 1 Switch
* 6 PCs (2 per department)

Each VLAN is mapped to a specific department and subnet.

---

## 🔧 Configuration Summary

### Switch Configuration

* VLAN creation (10, 20, 30)
* Port assignment per department
* Trunk configuration to router

### Router Configuration

* Subinterfaces for each VLAN
* 802.1Q encapsulation
* Default gateways for each network

### ACL Configuration

* HR department is restricted from accessing IT resources
* IT department has full access

---

## 🖥️ Example Configuration Snippets

### Switch (VLAN & Trunk)

```bash
vlan 10
vlan 20
vlan 30

interface fa0/7
switchport mode trunk
```

### Router (Subinterfaces)

```bash
interface g0/0/0.10
encapsulation dot1Q 10
ip address 192.168.10.1 255.255.255.0

interface g0/0/0.20
encapsulation dot1Q 20
ip address 192.168.20.1 255.255.255.0
```

### ACL

```bash
access-list 100 deny ip 192.168.20.0 0.0.0.255 192.168.10.0 0.0.0.255
access-list 100 permit ip any any
```

---

## 🧪 Testing

| Test    | Result    |
| ------- | --------- |
| IT → IT | ✅ Success |
| IT → HR | ✅ Success |
| HR → IT | ❌ Blocked |

---

## ⚠️ Challenges & Troubleshooting

During this project, several issues were encountered:

* Inter-VLAN communication initially failed due to missing trunk configuration
* Router interface was down because `no shutdown` was not applied
* ACL was first applied in the wrong direction, causing unexpected traffic blocking

These issues helped me understand how to troubleshoot real-world networking problems.

---

## 🧠 What I Learned

* How VLANs isolate network traffic
* How routers enable communication between VLANs
* How ACLs enforce network security policies
* How to debug network configuration issues

---

## 📁 Project Files

* `enterprise-network-lab.pkt` (Packet Tracer file)

---

## 🚀 Future Improvements

* Add DHCP server
* Implement DNS
* Add firewall simulation

---
