# Network Security Architecture Design Document

## 1. Executive Summary
This document outlines the design and implementation of a secure multi-department corporate network architecture. The solution provides network segmentation, access control, and secure inter-departmental communication for a 4-department organization.

## 2. Business Requirements
- **Objective**: Secure network architecture for corporate office
- **Departments**: Administration, Sales, IT, Finance (4 departments)
- **Security Requirements**: Department isolation, controlled access
- **Scalability**: Support for future growth

## 3. Network Design Overview

### 3.1 Topology Architecture
- **Hierarchical Design**: Core, Distribution, Access layers
- **Core Layer**: Router 2901 + Layer 3 Switch 3560
- **Access Layer**: 4x Switch 2960 (one per department)
- **End Devices**: 12 PCs + 4 Printers distributed across departments

### 3.2 VLAN Design
| VLAN ID | Department | Subnet | Purpose |
|---------|------------|---------|----------|
| 10 | Administration | 192.168.10.0/24 | Admin staff and resources |
| 20 | Sales | 192.168.20.0/24 | Sales team operations |
| 30 | IT | 192.168.30.0/24 | IT management and servers |
| 40 | Finance | 192.168.40.0/24 | Financial operations (restricted) |
| 99 | Management | 192.168.99.0/24 | Network management |

### 3.3 Security Policies
- **Finance Isolation**: Finance department restricted from other departments
- **Admin Restrictions**: Admin cannot access Finance resources
- **IT Full Access**: IT department has network management access
- **Sales Standard Access**: Normal inter-departmental communication

## 4. Implementation Details

### 4.1 Physical Connections
- Core Router (Gi0/0) ↔ Core Switch (Fa0/1)
- Core Switch ↔ Access Switches via trunk links (Fa0/2-5 to Fa0/24)
- End devices connected to access switches (Fa0/1-4)

### 4.2 VLAN Implementation
- **Trunk Configuration**: 802.1Q encapsulation between core and access switches
- **Access Ports**: End devices assigned to department VLANs
- **SVI Configuration**: Inter-VLAN routing via Switch Virtual Interfaces

### 4.3 Access Control Implementation
- **Extended ACLs**: Role-based traffic filtering
- **ADMIN_ACL**: Permits admin traffic, blocks finance access
- **FINANCE_ACL**: Restricts finance to management VLAN only

## 5. Testing and Validation

### 5.1 Connectivity Tests
- ✅ Intra-VLAN communication working
- ✅ Inter-VLAN routing functional
- ✅ Access control policies enforced

### 5.2 Security Validation
- ✅ Finance department isolation confirmed
- ✅ Unauthorized access attempts blocked
- ✅ Network segmentation effective

## 6. Future Enhancements
- RADIUS authentication integration
- Network monitoring implementation
- DMZ for web services
- Wireless network integration
