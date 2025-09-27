# Network Troubleshooting Guide

## Common Issues and Solutions

### 1. VLAN Communication Issues

**Problem**: Devices in same VLAN cannot communicate
**Symptoms**: Ping timeouts within department
**Solutions**:
- Verify VLAN assignment: `show vlan brief`
- Check access port configuration
- Confirm trunk links are up

### 2. Inter-VLAN Routing Problems

**Problem**: Devices cannot communicate across VLANs
**Symptoms**: Cannot ping other departments
**Solutions**:
- Verify SVI configuration: `show ip interface brief`
- Check routing table: `show ip route`
- Confirm `ip routing` enabled on core switch

### 3. Access Control List Issues

**Problem**: Traffic blocked unexpectedly
**Symptoms**: Authorized traffic fails
**Solutions**:
- Review ACL configuration: `show access-lists`
- Check ACL application: `show ip interface`
- Verify permit/deny order in ACL

### 4. Trunk Link Problems

**Problem**: VLANs not passing across trunk
**Symptoms**: Intermittent connectivity
**Solutions**:
- Check trunk status: `show interfaces trunk`
- Verify allowed VLANs on trunk
- Confirm encapsulation type (dot1q)

## Verification Commands

### Basic Connectivity

ping ip-address           # Test connectivity traceroute ip-address     # Trace packet path


### VLAN Troubleshooting


show vlan brief            # VLAN summary show vlan id number      # Specific VLAN details show interfaces trunk      # Trunk port status


### Routing Troubleshooting


show ip route             # Routing table show ip interface brief   # Interface status show cdp neighbors        # Adjacent devices

