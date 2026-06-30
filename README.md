# 🌐 Enterprise Multi-Company Network Design using Cisco Packet Tracer

![Cisco](https://img.shields.io/badge/Cisco-Packet%20Tracer-blue)
![Routing](https://img.shields.io/badge/Routing-BGP%20%7C%20RIPv2-green)
![Networking](https://img.shields.io/badge/Networking-VLANs%20%7C%20VLSM-orange)
![Status](https://img.shields.io/badge/Status-Completed-success)
![License](https://img.shields.io/badge/License-Educational-lightgrey)

A complete enterprise-scale network simulation developed in **Cisco Packet Tracer** that demonstrates advanced IPv4 addressing, CIDR, VLSM subnetting, VLAN implementation, Router-on-a-Stick, DHCP, DNS, HTTP services, dynamic routing with RIP Version 2, external routing using BGP, and route redistribution between routing domains.

The project simulates four independent organizations connected through WAN serial links while maintaining autonomous internal networks and allowing secure communication between organizations.

---

# Table of Contents

- Project Overview
- Objectives
- Key Features
- Network Architecture
- Technologies Used
- Project Topology
- Company Overview
- Addressing Scheme
- VLAN Design
- Routing Architecture
- Services
- Hardware Used
- Project Structure
- Configuration Summary
- Verification
- Scalability
- Future Improvements
- Author

---

# Project Overview

Modern enterprise environments rarely consist of a single local network. Large organizations commonly operate multiple offices, departments, branches, and autonomous business units that require secure communication while maintaining administrative independence.

This project demonstrates how such an environment can be implemented using Cisco Packet Tracer.

The simulated infrastructure consists of four independent companies:

- **JTECH**
- **UCOM**
- **TNet**
- **NSys**

Each organization owns its own IP address block, routing domain, and local network design.

The project combines several networking concepts into one complete implementation, including:

- IPv4 Address Planning
- CIDR
- Variable Length Subnet Masking (VLSM)
- VLAN Segmentation
- Router-on-a-Stick
- DHCP
- DNS
- HTTP
- RIP Version 2
- Border Gateway Protocol (BGP)
- Route Redistribution
- DHCP Relay
- WAN Serial Connections

Unlike many Packet Tracer projects that demonstrate only one networking concept, this implementation integrates multiple enterprise technologies into one interconnected infrastructure.

---

# Objectives

The project was designed to satisfy the following objectives:

- Design an enterprise-scale network connecting multiple independent organizations.
- Maximize IP address utilization through CIDR and VLSM.
- Minimize hardware requirements without sacrificing scalability.
- Isolate departments using VLAN technology.
- Implement both static and dynamic IP addressing.
- Deploy centralized network services including DHCP, DNS, and HTTP.
- Configure dynamic routing between branches using RIP Version 2.
- Configure inter-company communication using Border Gateway Protocol (BGP).
- Demonstrate route redistribution between different routing protocols.
- Validate complete end-to-end connectivity using Packet Tracer simulation.

---

# Key Features

## Network Design

- Four interconnected enterprise networks
- Five enterprise routers
- Eleven Layer-2 switches
- Thirty end devices
- Two centralized servers
- Four WAN serial links
- Multiple LAN segments
- Hierarchical topology

---

## IPv4 Addressing

- CIDR-based address allocation
- Variable Length Subnet Masking (VLSM)
- Efficient subnet utilization
- Independent address blocks for every company
- Dedicated WAN addressing using /30 subnets

---

## VLAN Implementation

- Department isolation
- Broadcast domain separation
- Router-on-a-Stick implementation
- IEEE 802.1Q tagging
- Trunk and access ports

---

## Routing

### Internal Routing

- RIP Version 2
- Dynamic route learning
- Branch-to-branch communication

### External Routing

- Border Gateway Protocol (BGP)
- Autonomous Systems
- Route advertisement
- Inter-company communication

---

## Network Services

- DHCP Server
- DNS Server
- HTTP Server
- DHCP Relay Agent
- Static Addressing
- Dynamic Address Allocation

---

# Technologies Used

| Category | Technology |
|-----------|------------|
| Simulation | Cisco Packet Tracer |
| Addressing | IPv4 |
| Subnetting | CIDR |
| Address Optimization | VLSM |
| Switching | VLAN |
| VLAN Standard | IEEE 802.1Q |
| Inter-VLAN Routing | Router-on-a-Stick |
| Dynamic Routing | RIP Version 2 |
| Exterior Routing | BGP |
| Services | DHCP |
| Services | DNS |
| Services | HTTP |
| WAN | Serial DCE/DTE |

---

# Network Architecture

The project simulates four independent organizations connected through a central enterprise WAN.

```
                    +----------------+
                    |     JTECH      |
                    |     AS100      |
                    +-------+--------+
                            |
                            |
                       Serial WAN
                            |
                            |
+---------+            +-----+-----+             +---------+
|  UCOM   |------------| NSys-B1   |-------------|  TNet   |
|  AS200  |            |  AS400    |             |  AS300  |
+---------+            +-----+-----+             +---------+
                            |
                     RIP Internal Routing
                            |
                     Serial WAN Link
                            |
                    +-------+--------+
                    |   NSys-B2      |
                    +----------------+
```

The design intentionally separates internal organizational routing from external inter-company routing.

- Internal communication inside NSys is handled by RIP Version 2.
- External communication between companies is handled exclusively through BGP.

This closely resembles real enterprise environments where organizations use Interior Gateway Protocols (IGPs) internally while using Exterior Gateway Protocols (EGPs) for communication with other autonomous systems.

---

# Company Overview

## 1. JTECH

JTECH consists of five independent rooms.

Each room is placed inside its own VLAN and subnet.

Because one router interface cannot directly connect five different broadcast domains, Router-on-a-Stick is implemented using IEEE 802.1Q trunking.

### Components

- 1 Cisco 2911 Router
- 1 Cisco 2960 Switch
- 5 VLANs
- 5 PCs
- 5 Subnets

### Technologies

- Router-on-a-Stick
- VLANs
- 802.1Q Trunking
- RIP
- BGP

---

## 2. UCOM

UCOM contains three independent rooms.

Each room connects directly to a dedicated GigabitEthernet interface on the router.

Because sufficient physical interfaces are available, VLAN implementation is unnecessary.

### Components

- 1 Cisco 2911 Router
- 3 Cisco 2960 Switches
- 9 PCs
- 3 Independent LANs

### Technologies

- Static LAN Routing
- RIP
- BGP

---

## 3. TNet

TNet contains two separate departments.

Each department connects directly to its own router interface.

The assigned address block is completely utilized using two /27 subnets, resulting in perfect IP utilization with zero address waste.

### Components

- 1 Cisco 2911 Router
- 2 Cisco 2960 Switches
- 8 PCs

### Technologies

- Static Interface Routing
- RIP
- BGP

---

## 4. NSys

NSys represents the largest organization in the project.

Unlike the other companies, NSys operates from two geographically separated branches.

Branch communication is performed using RIP Version 2, while external communication uses BGP through Branch 1.

Branch 1 functions as the backbone of the entire project.

It performs four critical responsibilities simultaneously:

- Border Gateway Router
- RIP Hub
- DHCP Relay Agent
- Route Redistribution Router

This makes NSys-B1 the most sophisticated router in the network.

# Detailed Network Design

The network has been designed using a hierarchical architecture in which each company operates as an independent administrative domain while maintaining connectivity with every other organization through WAN serial links.

Each organization has been allocated its own IPv4 address block using CIDR notation. These address blocks are further subnetted using Variable Length Subnet Masking (VLSM) according to the number of hosts required in each department.

This design minimizes IP address wastage while allowing significant room for future expansion.

The overall network consists of:

| Component | Quantity |
|-----------|----------|
| Companies | 4 |
| Routers | 5 |
| Switches | 11 |
| PCs | 30 |
| Servers | 2 |
| WAN Links | 4 |
| VLANs | 5 |
| DHCP Pools | 2 |
| DNS Zones | 2 |
| HTTP Servers | 1 |

---

# Company Network Design

## JTECH

JTECH represents a medium-sized company divided into five individual rooms.

Each room functions as its own broadcast domain and therefore requires an independent subnet.

Instead of using five physical router interfaces, the network implements **Router-on-a-Stick**, allowing one GigabitEthernet interface to carry traffic for all VLANs simultaneously through IEEE 802.1Q tagging.

### JTECH Infrastructure

| Device | Quantity |
|---------|---------|
| Cisco 2911 Router | 1 |
| Cisco 2960 Switch | 1 |
| PCs | 5 |
| VLANs | 5 |

### VLAN Allocation

| VLAN | Department | Subnet |
|------|------------|---------|
| VLAN 10 | Room 1 | 100.186.96.0/28 |
| VLAN 20 | Room 2 | 100.186.96.16/28 |
| VLAN 30 | Room 3 | 100.186.96.32/28 |
| VLAN 40 | Room 4 | 100.186.96.48/28 |
| VLAN 50 | Room 5 | 100.186.96.64/28 |

### Key Characteristics

- Router-on-a-Stick
- 802.1Q Trunking
- Five Broadcast Domains
- Five Independent Subnets
- Dynamic Routing via BGP

---

## UCOM

UCOM consists of three separate rooms.

Unlike JTECH, enough physical router interfaces are available to connect each room directly to the router.

Consequently, VLAN implementation is unnecessary.

Each room operates as an independent LAN connected directly to a dedicated GigabitEthernet interface.

### UCOM Infrastructure

| Device | Quantity |
|---------|---------|
| Cisco 2911 Router | 1 |
| Cisco 2960 Switches | 3 |
| PCs | 9 |

### Subnets

| Room | Network |
|-------|----------|
| Room 1 | 35.152.0.0/28 |
| Room 2 | 35.152.0.16/28 |
| Room 3 | 35.152.0.32/28 |

### Key Characteristics

- Dedicated Router Interfaces
- Independent LANs
- Static Interface Configuration
- BGP External Routing

---

## TNet

TNet contains two departments.

Each department connects directly to a separate GigabitEthernet interface.

The assigned address block is divided perfectly into two /27 networks.

This results in **100% IP utilization**, making TNet the most efficient network in the project.

### Infrastructure

| Device | Quantity |
|---------|---------|
| Cisco 2911 Router | 1 |
| Cisco 2960 Switches | 2 |
| PCs | 8 |

### Subnets

| Department | Network |
|------------|----------|
| Department 1 | 200.98.169.64/27 |
| Department 2 | 200.98.169.96/27 |

### Key Characteristics

- Direct LAN Interfaces
- No VLANs Required
- Perfect VLSM Utilization
- External Connectivity via BGP

---

## NSys

NSys is the most sophisticated organization within the project.

Instead of operating from a single location, NSys consists of two geographically separated branches connected through a dedicated serial WAN link.

Branch 1 acts as the backbone router for the entire infrastructure.

It performs multiple enterprise-level functions simultaneously.

### Branch 1 Responsibilities

- BGP Border Router
- RIP Hub
- DHCP Relay Agent
- Route Redistribution
- Server Gateway

### Branch 2 Responsibilities

- Internal Branch Routing
- DHCP Relay
- RIP Participation

### Infrastructure

| Device | Quantity |
|---------|---------|
| Routers | 2 |
| Switches | 5 |
| PCs | 8 |
| Servers | 2 |

---

# IPv4 Addressing Plan

The project uses globally unique address blocks for each organization.

| Company | Assigned Block |
|----------|----------------|
| JTECH | 100.186.96.0/19 |
| UCOM | 35.152.0.0/15 |
| TNet | 200.98.169.64/26 |
| NSys | 10.10.0.0/16 |
| WAN | 10.0.0.0/24 |

Each company exclusively owns its assigned block.

No address overlap exists anywhere in the topology.

---

# Variable Length Subnet Masking (VLSM)

Instead of assigning equal-sized networks, VLSM was used to allocate address space based upon actual host requirements.

Benefits include:

- Reduced IP wastage
- Better scalability
- Easier route summarization
- Simplified administration
- Efficient network utilization

Examples include:

- /28 networks for small departments
- /27 networks for larger LANs
- /24 networks for NSys departments
- /30 networks for point-to-point WAN links

---

# WAN Addressing

Point-to-point serial links require only two usable IP addresses.

Therefore, every WAN connection uses a /30 subnet.

| Connection | Network |
|------------|----------|
| NSys-B1 ↔ JTECH | 10.0.0.0/30 |
| NSys-B1 ↔ UCOM | 10.0.0.4/30 |
| NSys-B1 ↔ TNet | 10.0.0.8/30 |
| NSys-B1 ↔ NSys-B2 | 10.0.0.12/30 |

Using /30 addressing ensures that only four IP addresses exist within each WAN subnet:

- Network Address
- Router A
- Router B
- Broadcast Address

This is considered best practice for point-to-point links.

---

# VLAN Design

Only JTECH requires VLAN implementation.

Since five departments share one physical switch and one router interface, VLANs isolate traffic while maintaining logical separation.

| VLAN | Purpose |
|------|---------|
| 10 | Room 1 |
| 20 | Room 2 |
| 30 | Room 3 |
| 40 | Room 4 |
| 50 | Room 5 |

The switch connects to the router through a trunk link carrying tagged traffic for every VLAN.

Each PC connects to an access port belonging to its assigned VLAN.

---

# Router-on-a-Stick

JTECH implements Router-on-a-Stick to overcome physical interface limitations.

Instead of requiring one router interface per subnet, multiple logical subinterfaces are created on a single GigabitEthernet interface.

Each subinterface:

- Belongs to a unique VLAN
- Has its own IP address
- Acts as the default gateway
- Uses IEEE 802.1Q encapsulation

This significantly reduces hardware requirements while maintaining complete Layer-3 functionality.

---

# Hardware Inventory

## Routers

- Cisco 2911 × 5

## Switches

- Cisco 2960 × 11

## End Devices

- Desktop PCs × 30

## Servers

- DHCP / HTTP Server × 1
- DNS Server × 1

---

# Device Roles

| Device | Role |
|----------|------|
| R-JTECH | Router-on-a-Stick Router |
| SW-JTECH | VLAN Switch |
| R-UCOM | Company Router |
| R-TNET | Company Router |
| R-NSys-B1 | Border Router |
| R-NSys-B2 | Branch Router |
| SVR-DHCP-HTTP | DHCP & HTTP Services |
| SVR-DNS | DNS Resolution |

---
