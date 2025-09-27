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
