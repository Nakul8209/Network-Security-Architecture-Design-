# Network Security Architecture - Step by Step Configuration Commands

## Initial Setup Commands

### Core Router Configuration

Router> enable Router# configure terminal Router(config)# hostname CoreRouter CoreRouter(config)# interface GigabitEthernet0/0 CoreRouter(config-if)# ip address 192.168.1.1 255.255.255.0 CoreRouter(config-if)# no shutdown CoreRouter(config-if)# exit CoreRouter(config)# line vty 0 4 CoreRouter(config-line)# password cisco123 CoreRouter(config-line)# login CoreRouter(config-line)# transport input telnet CoreRouter(config-line)# exit


### Core Switch Configuration


Switch> enable Switch# configure terminal Switch(config)# hostname CoreSwitch CoreSwitch(config)# ip routing CoreSwitch(config)# interface fastethernet 0/1 CoreSwitch(config-if)# no switchport CoreSwitch(config-if)# ip address 192.168.1.2 255.255.255.0 CoreSwitch(config-if)# no shutdown CoreSwitch(config-if)# exit



### VLAN Creation


CoreSwitch(config)# vlan 10 CoreSwitch(config-vlan)# name Administration CoreSwitch(config-vlan)# exit CoreSwitch(config)# vlan 20 CoreSwitch(config-vlan)# name Sales CoreSwitch(config-vlan)# exit CoreSwitch(config)# vlan 30 CoreSwitch(config-vlan)# name IT CoreSwitch(config-vlan)# exit CoreSwitch(config)# vlan 40 CoreSwitch(config-vlan)# name Finance CoreSwitch(config-vlan)# exit CoreSwitch(config)# vlan 99 CoreSwitch(config-vlan)# name Management CoreSwitch(config-vlan)# exit


### VLAN Interfaces (SVIs)

CoreSwitch(config)# interface vlan 10 CoreSwitch(config-if)# ip address 192.168.10.1 255.255.255.0 CoreSwitch(config-if)# no shutdown CoreSwitch(config)# interface vlan 20 CoreSwitch(config-if)# ip address 192.168.20.1 255.255.255.0 CoreSwitch(config-if)# no shutdown CoreSwitch(config)# interface vlan 30 CoreSwitch(config-if)# ip address 192.168.30.1 255.255.255.0 CoreSwitch(config-if)# no shutdown CoreSwitch(config)# interface vlan 40 CoreSwitch(config-if)# ip address 192.168.40.1 255.255.255.0 CoreSwitch(config-if)# no shutdown CoreSwitch(config)# interface vlan 99 CoreSwitch(config-if)# ip address 192.168.99.1 255.255.255.0 CoreSwitch(config-if)# no shutdown


### Trunk Port Configuration


CoreSwitch(config)# interface range fastethernet 0/2-5 CoreSwitch(config-if-range)# switchport trunk encapsulation dot1q CoreSwitch(config-if-range)# switchport mode trunk CoreSwitch(config-if-range)# switchport trunk allowed vlan 10,20,30,40,99


### Access Control Lists


CoreSwitch(config)# ip access-list extended ADMIN_ACL CoreSwitch(config-ext-nacl)# permit ip 192.168.10.0 0.0.0.255 any CoreSwitch(config-ext-nacl)# deny ip any 192.168.40.0 0.0.0.255 CoreSwitch(config-ext-nacl)# permit icmp any any CoreSwitch(config-ext-nacl)# exit
CoreSwitch(config)# ip access-list extended FINANCE_ACL CoreSwitch(config-ext-nacl)# permit ip 192.168.40.0 0.0.0.255 192.168.99.0 0.0.0.255 CoreSwitch(config-ext-nacl)# deny ip any any CoreSwitch(config-ext-nacl)# exit
CoreSwitch(config)# interface vlan 10 CoreSwitch(config-if)# ip access-group ADMIN_ACL in CoreSwitch(config)# interface vlan 40 CoreSwitch(config-if)# ip access-group FINANCE_ACL in


## Access Switch Configurations

### Administration Switch


Switch(config)# hostname AdminSwitch AdminSwitch(config)# vlan 10 AdminSwitch(config-vlan)# name Administration AdminSwitch(config-vlan)# exit AdminSwitch(config)# interface fastethernet 0/24 AdminSwitch(config-if)# switchport mode trunk AdminSwitch(config)# interface range fastethernet 0/1-4 AdminSwitch(config-if-range)# switchport mode access AdminSwitch(config-if-range)# switchport access vlan 10



### Sales Switch


Switch(config)# hostname SalesSwitch SalesSwitch(config)# vlan 20 SalesSwitch(config-vlan)# name Sales SalesSwitch(config-vlan)# exit SalesSwitch(config)# interface fastethernet 0/24 SalesSwitch(config-if)# switchport mode trunk SalesSwitch(config)# interface range fastethernet 0/1-4 SalesSwitch(config-if-range)# switchport mode access SalesSwitch(config-if-range)# switchport access vlan 20


### IT Switch


Switch(config)# hostname ITSwitch ITSwitch(config)# vlan 30 ITSwitch(config-vlan)# name IT ITSwitch(config-vlan)# exit ITSwitch(config)# interface fastethernet 0/24 ITSwitch(config-if)# switchport mode trunk ITSwitch(config)# interface range fastethernet 0/1-4 ITSwitch(config-if-range)# switchport mode access ITSwitch(config-if-range)# switchport access vlan 30


### Finance Switch


Switch(config)# hostname FinanceSwitch FinanceSwitch(config)# vlan 40 FinanceSwitch(config-vlan)# name Finance FinanceSwitch(config-vlan)# exit FinanceSwitch(config)# interface fastethernet 0/24 FinanceSwitch(config-if)# switchport mode trunk FinanceSwitch(config)# interface range fastethernet 0/1-4 FinanceSwitch(config-if-range)# switchport mode access FinanceSwitch(config-if-range)# switchport access vlan 40


## Verification Commands

### Basic Verification


show vlan brief show ip interface brief show access-lists show ip route show interfaces trunk



### Testing Commands


ping 192.168.10.1    # Test gateway connectivity ping 192.168.20.10   # Test inter-VLAN communication telnet 192.168.1.1   # Test management access


