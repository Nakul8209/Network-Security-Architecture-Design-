# Installation and Setup Guide

## Prerequisites
- Cisco Packet Tracer 7.3.0 or later
- Basic networking knowledge
- Administrative access to configure devices

## Quick Start

### 1. Download Project Files
1. Download `network_security_project.pkt` from repository
2. Save to your local directory
3. Open with Cisco Packet Tracer

### 2. Load Configuration
1. **Open Packet Tracer**
2. **File → Open** → Select `network_security_project.pkt`
3. **Wait for network to converge** (all lights turn green)

### 3. Initial Testing

From any PC, test basic connectivity
ping 192.168.10.1    # Test VLAN gateway ping 192.168.1.1     # Test router connectivity


## Manual Setup (Optional)

If you want to build from scratch, follow these steps:

### Step 1: Device Placement
1. Add Router 2901 to workspace
2. Add Switch 3560 (core)
3. Add 4x Switch 2960 (access)
4. Connect as per topology diagram

### Step 2: Basic Configuration
Refer to `/configs/` folder for complete device configurations

### Step 3: VLAN Setup
1. Create VLANs 10, 20, 30, 40, 99
2. Configure trunk links
3. Set up SVIs for inter-VLAN routing

### Step 4: Security Implementation
1. Configure Extended ACLs
2. Apply access control policies
3. Set up management access

## Verification Steps

### 1. Check VLAN Status

CoreSwitch# show vlan brief


### 2. Verify Routing

CoreSwitch# show ip route


### 3. Test Security Policies

ping 192.168.40.10  # Should fail from admin


## Troubleshooting

If network doesn't work:
1. Check physical connections
2. Verify device power status
3. Review configuration files in `/configs/`
4. Refer to `Troubleshooting_Guide.md`
