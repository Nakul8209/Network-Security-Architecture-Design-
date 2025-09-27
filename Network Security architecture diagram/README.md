# Network Security Architecture Design

## 🎯 Project Overview

A comprehensive network security project implementing a secure multi-department corporate network architecture using Cisco Packet Tracer. This project demonstrates enterprise-level network design with VLAN segmentation, role-based access controls, and inter-VLAN routing.

![Network Topology](images/topology_overview.png)

## 🏢 **Project Scope**

**Designed for**: 4-department corporate office
- **Administration Department** (VLAN 10) - 192.168.10.0/24
- **Sales Department** (VLAN 20) - 192.168.20.0/24  
- **IT Department** (VLAN 30) - 192.168.30.0/24
- **Finance Department** (VLAN 40) - 192.168.40.0/24

## 🔧 **Technologies Implemented**

### Network Infrastructure
- **VLANs**: Departmental network segmentation
- **Inter-VLAN Routing**: Layer 3 switching with SVIs
- **Trunk Links**: 802.1Q VLAN tagging
- **Access Control Lists**: Role-based traffic filtering

### Security Features  
- **Network Segmentation**: Departmental isolation
- **Access Control Policies**: Extended ACLs restricting inter-department access
- **Secure Management Access**: Password-protected device access

### Hardware Used
- **1x Router 2901**: Core routing and gateway
- **1x Switch 3560**: Layer 3 core switch with inter-VLAN routing
- **4x Switch 2960**: Access layer switches for end devices
- **16x End Devices**: PCs and printers distributed across departments

## 📊 **Key Features**

✅ **Multi-Department Network Architecture**  
✅ **VLAN-Based Network Segmentation**  
✅ **Role-Based Access Control Implementation**  
✅ **Inter-VLAN Communication Control**  
✅ **Enterprise-Level Security Policies**  
✅ **Scalable Network Design**

## 🛠️ **Installation & Usage**

### Prerequisites
- Cisco Packet Tracer (version 7.3.0 or later)
- Basic understanding of networking concepts

### Running the Project
1. **Download** the `network_security_project.pkt` file
2. **Open** with Cisco Packet Tracer
3. **Explore** the network topology and configurations
4. **Test** network connectivity and security policies

## 🧪 **Testing & Verification**

### Network Connectivity Tests

Inter-VLAN Communication (Should Work)
ping 192.168.20.10  # Admin to Sales ping 192.168.30.10  # Admin to IT
Blocked Communication (Should Fail)
ping 192.168.40.10  # Admin to Finance (Blocked by ACL)


### Verification Commands

VLAN Configuration
show vlan brief
IP Interface Status
show ip interface brief
Access Control Lists
show access-lists
Routing Table
show ip route


## 📈 **Network Architecture**

### VLAN Design
| VLAN ID | Department | Network | Gateway |
|---------|------------|---------|---------|
| 10 | Administration | 192.168.10.0/24 | 192.168.10.1 |
| 20 | Sales | 192.168.20.0/24 | 192.168.20.1 |
| 30 | IT | 192.168.30.0/24 | 192.168.30.1 |
| 40 | Finance | 192.168.40.0/24 | 192.168.40.1 |

### Security Policies
- **Finance Department**: Restricted access to other departments
- **Admin Department**: Cannot access Finance resources
- **IT Department**: Full network access for management
- **Sales Department**: Standard inter-department communication

## 🔍 **Project Highlights**

This project demonstrates:
- **Enterprise Network Design** principles
- **Network Security** implementation
- **VLAN Segmentation** best practices  
- **Access Control** policy enforcement
- **Scalable Architecture** for growing organizations

## 📝 **Documentation**

- [Configuration Commands](docs/Configuration_Commands.md) - Complete CLI command reference
- [Network Diagram](docs/Network_Topology_Diagram.png) - Visual network layout
- [Testing Results](docs/Testing_Results.png) - Verification screenshots

## 👨‍💻 **About**

**Project Type**: Network Security Architecture  
**Technology**: Cisco Packet Tracer  
**Complexity**: Intermediate to Advanced  
**Focus**: Enterprise Network Security & VLAN Implementation

## 🤝 **Contributing**

Feel free to fork this repository and submit pull requests for improvements or additional features.

## 📄 **License**

This project is open source and available under the [MIT License](LICENSE).

---

**⭐ If you found this project helpful, please give it a star!**

