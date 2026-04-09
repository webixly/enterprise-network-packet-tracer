# 🖧 Enterprise Netzwerk Simulation (Cisco Packet Tracer)

## 📌 Überblick

Dieses Projekt zeigt das Design und die Umsetzung eines kleinen Unternehmensnetzwerks mit Cisco Packet Tracer.
Es beinhaltet VLAN-Segmentierung, Inter-VLAN-Routing und Zugriffskontrolle, um eine realistische Netzwerkumgebung zu simulieren.

---

## 📸 Projektübersicht

![Topology](images/topology.png)

---

## 🏢 Netzwerkstruktur

Das Netzwerk ist in drei Abteilungen unterteilt:

* IT-Abteilung (VLAN 10)
* HR-Abteilung (VLAN 20)
* Sales-Abteilung (VLAN 30)

Jede Abteilung arbeitet in einem eigenen, isolierten Netzwerk.

---

## 📊 Netzwerkdetails

| VLAN | Abteilung | Netzwerk        |
| ---- | --------- | --------------- |
| 10   | IT        | 192.168.10.0/24 |
| 20   | HR        | 192.168.20.0/24 |
| 30   | Sales     | 192.168.30.0/24 |

---

## ⚙️ Funktionen

* VLAN-Segmentierung zur Netzwerkisolierung
* Inter-VLAN-Routing (Router-on-a-Stick)
* Access Control Lists (ACL) zur Zugriffskontrolle
* Strukturierte IP-Adressierung

---

## 🖼️ Netzwerktopologie

Die Topologie besteht aus:

* 1 Router
* 1 Switch
* 6 PCs (2 pro Abteilung)

Jede VLAN ist einer bestimmten Abteilung zugeordnet.

---

## 🔧 Konfigurationsübersicht

### Switch-Konfiguration

* Erstellung der VLANs (10, 20, 30)
* Zuweisung der Ports zu den Abteilungen
* Trunk-Verbindung zum Router

### Router-Konfiguration

* Subinterfaces für jede VLAN
* 802.1Q Encapsulation
* Default-Gateways für jedes Netzwerk

### ACL-Konfiguration

* HR darf nicht auf IT zugreifen
* IT hat Zugriff auf alle Netzwerke

---

## 🖥️ Beispielkonfiguration

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

## 🧪 Tests

| Test    | Ergebnis      |
| ------- | ------------- |
| IT → IT | ✅ Erfolgreich |
| IT → HR | ✅ Erfolgreich |
| HR → IT | ❌ Blockiert   |

---

## ⚠️ Herausforderungen & Lösungen

Während des Projekts sind mehrere Probleme aufgetreten:

* Inter-VLAN-Kommunikation funktionierte zuerst nicht wegen fehlender Trunk-Konfiguration
* Router-Interface war deaktiviert (`no shutdown` fehlte)
* ACL wurde zuerst falsch angewendet (falsche Richtung)

Diese Probleme haben mir geholfen, reale Netzwerkprobleme besser zu verstehen und zu lösen.

---

## 🧠 Was ich gelernt habe

* Wie VLANs den Netzwerkverkehr isolieren
* Wie Routing die Kommunikation zwischen VLANs ermöglicht
* Wie ACLs den Netzwerkzugriff steuern
* Wie man Netzwerkprobleme analysiert und behebt

---

## 📁 Projektdateien

* `enterprise-network-lab.pkt` (Packet Tracer Datei)

---

## 🚀 Zukünftige Erweiterungen

* DHCP-Server hinzufügen
* DNS implementieren
* Firewall integrieren

---
