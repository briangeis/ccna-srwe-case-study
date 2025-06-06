# **ccna-srwe-case-study**

This project uses GNS3 and Cisco Packet Tracer to create a network based
on a case study assigned as the final practical skills assessment for my
CCNA: Switching, Routing, and Wireless Essentials course.
The case study was designed to test skills gained throughout the course and
required that I build and configure a complex network on physical equipment.

## Table of Contents

* [Network Topology](#network-topology)
* [Skills Demonstrated](#skills-demonstrated)
* [Software and Devices Used](#software-and-devices-used)
* [Addressing Table](#addressing-table)
* [Router Configuration](#router-configuration)
* [Switch Configuration](#switch-configuration)
* [Linux Host Configuration](#linux-host-configuration)
* [Deliverables](#deliverables)
* [License](#license)
* [References](#references)

## Network Topology

![Network Topology Diagram](topology.png)

## Skills Demonstrated

* Cisco router and switch configuration
* Inter-VLAN routing configuration
* Hot Standby Router Protocol (HSRP) configuration
* Dynamic Host Configuration Protocol (DHCP) pools and scopes
* IPv4 floating static, default, and host routes
* VLAN and switchport VLAN membership configuration
* EtherChannel configuration
* Static trunking and Dynamic Trunking Protocol (DTP)
* Spanning Tree Protocol (STP) configuration
* Switch security, port security, PortFast, and BPDU Guard
* Dynamic ARP Inspection (DAI) and trusted ports

## Software and Devices Used

### GNS3 Simulation

* GNS3 Server v3.0.5
* GNS3 GUI v3.0.5
* Cisco IOSv Router Appliance (x4)
* Cisco IOSvL2 Switch Appliance (x4)
* Alpine Linux Docker Appliance (x5)
* Cloud Appliance

### Cisco Packet Tracer Simulation

* Cisco Packet Tracer v8.2.2
* Cisco 2901 Router (x4)
* Cisco 2960 Switch (x4)
* Packet Tracer Simulated PC (x5)

## Addressing Table

<table>
  <tr>
    <th>Device</th>
    <th>GNS3 Interface</th>
    <th>PT Interface</th>
    <th>IP Address</th>
    <th>Subnet Mask</th>
  </tr>
  <tr>
    <td>ISP</td>
    <td>G0/3</td>
    <td>S0/0/0</td>
    <td>200.1.1.1</td>
    <td>255.255.255.252</td>
  </tr>
  <tr>
    <td rowspan="3">EDGE</td>
    <td>G0/3</td>
    <td>S0/0/0</td>
    <td>200.1.1.2</td>
    <td>255.255.255.252</td>
  </tr>
  <tr>
    <td>G0/0</td>
    <td>G0/0</td>
    <td>192.168.2.1</td>
    <td>255.255.255.252</td>
  </tr>
  <tr>
    <td>G0/1</td>
    <td>G0/1</td>
    <td>192.168.1.1</td>
    <td>255.255.255.252</td>
  </tr>
  <tr>
    <td rowspan="3">R1</td>
    <td>G0/0.10</td>
    <td>G0/0.10</td>
    <td>192.168.10.1</td>
    <td>255.255.255.0</td>
  </tr>
  <tr>
    <td>G0/1</td>
    <td>G0/1</td>
    <td>192.168.1.2</td>
    <td>255.255.255.252</td>
  </tr>
  <tr>
    <td>G0/3</td>
    <td>S0/0/1</td>
    <td>192.168.3.2</td>
    <td>255.255.255.252</td>
  </tr>
  <tr>
    <td rowspan="7">R2</td>
    <td>G0/1</td>
    <td>G0/1</td>
    <td>192.168.2.2</td>
    <td>255.255.255.252</td>
  </tr>
  <tr>
    <td>G0/0.10</td>
    <td>G0/0.10</td>
    <td>192.168.10.2</td>
    <td>255.255.255.0</td>
  </tr>
  <tr>
    <td>G0/0.32</td>
    <td>G0/0.32</td>
    <td>192.168.32.1</td>
    <td>255.255.255.0</td>
  </tr>
  <tr>
    <td>G0/0.36</td>
    <td>G0/0.36</td>
    <td>192.168.36.1</td>
    <td>255.255.255.0</td>
  </tr>
  <tr>
    <td>G0/0.40</td>
    <td>G0/0.40</td>
    <td>192.168.40.1</td>
    <td>255.255.255.0</td>
  </tr>
  <tr>
    <td>G0/0.60</td>
    <td>G0/0.60</td>
    <td>192.168.60.1</td>
    <td>255.255.255.0</td>
  </tr>
  <tr>
    <td>G0/3</td>
    <td>S0/0/0</td>
    <td>192.168.3.1</td>
    <td>255.255.255.252</td>
  </tr>
  <tr>
    <td>HSRP</td>
    <td colspan="2">Virtual Gateway (VLAN 10)</td>
    <td>192.168.10.3</td>
    <td>255.255.255.0</td>
  </tr>
  <tr>
    <td>R1-LAN-SW-FL1</td>
    <td colspan="2">Switched Virtual Interface (SVI)</td>
    <td>192.168.10.4</td>
    <td>255.255.255.0</td>
  </tr>
  <tr>
    <td>R2-LAN-SW-MAIN</td>
    <td colspan="2">Switched Virtual Interface (SVI)</td>
    <td>192.168.60.4</td>
    <td>255.255.255.0</td>
  </tr>
  <tr>
    <td>R2-LAN-SW-FL1</td>
    <td colspan="2">Switched Virtual Interface (SVI)</td>
    <td>192.168.60.5</td>
    <td>255.255.255.0</td>
  </tr>
  <tr>
    <td>R2-LAN-SW-FL2</td>
    <td colspan="2">Switched Virtual Interface (SVI)</td>
    <td>192.168.60.6</td>
    <td>255.255.255.0</td>
  </tr>
  <tr>
    <td>Admin-PC</td>
    <td colspan="2">eth0 Network Interface</td>
    <td>192.168.10.10</td>
    <td>255.255.255.0</td>
  </tr>
  <tr>
    <td>Accounting-PC</td>
    <td colspan="2">eth0 Network Interface</td>
    <td colspan="2">DHCP Pool R2-VLAN-32</td>
  </tr>
  <tr>
    <td>Marketing-PC</td>
    <td colspan="2">eth0 Network Interface</td>
    <td colspan="2">DHCP Pool R2-VLAN-36</td>
  </tr>
  <tr>
    <td>Logistics-PC</td>
    <td colspan="2">eth0 Network Interface</td>
    <td colspan="2">DHCP Pool R2-VLAN-40</td>
  </tr>
  <tr>
    <td>Management-PC</td>
    <td colspan="2">eth0 Network Interface</td>
    <td colspan="2">DHCP Pool R2-VLAN-60</td>
  </tr>
</table>

## Router Configuration

### Basic Router Configuration

* Set header MOTD message with this project info
* Set encrypted console/privileged EXEC passwords (cisco123)
* Configured remote access to the VTY lines
* Configured interface addressing per Addressing Table
* Activated used interfaces only

### Extended Router Configuration

* Configured inter-VLAN routing on R2 for all R2 switches
* Configured HSRP for VLAN 10 only with priority and preempt given to R1
* Configured EDGE router as DHCP server
* Created DHCP pool for each VLAN

#### EDGE Routes

* Default route set to 200.1.1.1
* Static route for 192.168.10.0/24 set to 192.168.1.2
* Floating static route for 192.168.10.0/24 set to 192.168.2.2 with AD 10
* Static route for 192.168.32.0/19 set to 192.168.2.2
* Floating static route for 192.168.32.0/19 set to 192.168.1.2 with AD 10

#### R1 Routes

* Default route set to 192.168.1.1
* Floating default route set to 192.168.3.1 with AD 10
* Summarized static route to R2 VLANs

#### R2 Routes

* Default route set to 192.168.2.1
* Floating default set to 192.168.3.2 with AD 10
* Summarized static route to R1 VLAN

## Switch Configuration

### Basic Switch Configuration

* Set header MOTD message with this project info
* Set encrypted console/privileged EXEC passwords (cisco123)
* Configured remote access to the switch SVI (SSH only)
* Configured interface addressing per Addressing Table
* Implemented best practices for all unused switchports
* Activated used interfaces only

### Extended Switch Configuration

<details open>

<summary>VLAN Information</summary>

| VLAN | Name       | IP Network   | Subnet Mask   |
| ---- | ---------- | ------------ | ------------- |
| 10   | Admin      | 192.168.10.0 | 255.255.255.0 |
| 32   | Accounting | 192.168.32.0 | 255.255.255.0 |
| 36   | Marketing  | 192.168.36.0 | 255.255.255.0 |
| 40   | Logistics  | 192.168.40.0 | 255.255.255.0 |
| 60   | Management | 192.168.60.0 | 255.255.255.0 |

</details>

<details>

<summary>VLAN Port Assignment</summary>

<table>
  <tr>
    <th>Device</th>
    <th>VLAN</th>
    <th>VLAN Name</th>
    <th>GNS3 Ports</th>
    <th>PacketTracer Ports</th>
  </tr>
  <tr>
    <td rowspan="4">R2-LAN-MAIN-SW</td>
    <td>32</td>
    <td>Accounting</td>
    <td>G0/0-1</td>
    <td>F0/1-5</td>
  </tr>
  <tr>
    <td>36</td>
    <td>Marketing</td>
    <td>G0/2-3</td>
    <td>F0/6-10</td>
  </tr>
  <tr>
    <td>40</td>
    <td>Logistics</td>
    <td>G1/0-1</td>
    <td>F0/11-15</td>
  </tr>
  <tr>
    <td>60</td>
    <td>Management Native</td>
    <td>G1/2-3</td>
    <td>F0/16-19</td>
  </tr>
  <tr>
    <td rowspan="3">R2-LAN-SW-FL1</td>
    <td>36</td>
    <td>Marketing</td>
    <td>G0/2-3</td>
    <td>F0/7-10</td>
  </tr>
  <tr>
    <td>40</td>
    <td>Logistics</td>
    <td>G1/0-1</td>
    <td>F0/11-15</td>
  </tr>
  <tr>
    <td>60</td>
    <td>Management Native</td>
    <td>G1/2-3</td>
    <td>F0/16-19</td>
  </tr>
  <tr>
    <td rowspan="4">R2-LAN-SW-FL2</td>
    <td>32</td>
    <td>Accounting</td>
    <td>G0/0-1</td>
    <td>F0/1-5</td>
  </tr>
  <tr>
    <td>36</td>
    <td>Marketing</td>
    <td>G0/2-3</td>
    <td>F0/6-10</td>
  </tr>
  <tr>
    <td>40</td>
    <td>Logistics</td>
    <td>G1/0-1</td>
    <td>F0/11-15</td>
  </tr>
  <tr>
    <td>60</td>
    <td>Management Native</td>
    <td>G1/2-3</td>
    <td>F0/19</td>
  </tr>
</table>

</details>

<details>

<summary>EtherChannel Port Assignment</summary>

<table>
  <tr>
    <th>Channel Group</th>
    <th>Devices in Group</th>
    <th>GNS3 Ports</th>
    <th>PacketTracer Ports</th>
  </tr>
  <tr>
    <td rowspan="2">Port Channel 1</td>
    <td>R2-LAN-MAIN-SW</td>
    <td>G3/2, G3/3</td>
    <td>F0/23, F0/24</td>
  </tr>
  <tr>
    <td>R2-LAN-SW-FL1</td>
    <td>G3/2, G3/3</td>
    <td>F0/23, F0/24</td>
  </tr>
  <tr>
    <td rowspan="2">Port Channel 2</td>
    <td>R2-LAN-MAIN-SW</td>
    <td>G3/0, G3/1</td>
    <td>F0/21, F0/22</td>
  </tr>
  <tr>
    <td>R2-LAN-SW-FL2</td>
    <td>G3/0, G3/1</td>
    <td>F0/21, F0/22</td>
  </tr>
  <tr>
    <td rowspan="2">Port Channel 3</td>
    <td>R2-LAN-SW-FL1</td>
    <td>G3/0, G3/1</td>
    <td>F0/21, F0/22</td>
  </tr>
  <tr>
    <td>R2-LAN-SW-FL2</td>
    <td>G3/2, G3/3</td>
    <td>F0/23, F0/24</td>
  </tr>
</table>

</details>

#### EtherChannel Configuration

* Created EtherChannels using Cisco LACP protocol
* Configured the port channel interfaces as static trunks
* Configured R2-LAN-MAIN-SW with static trunk to R2
* Set Management VLAN as the native VLAN on all switches
* Disabled DTP negotiation

#### STP Configuration

* Set R1-LAN-SW-FL1 as root for VLAN 10
* Set R2-LAN-SW-MAIN as the root for all other VLANs

#### Switch Security Configuration

* Enabled PortFast and BPDU Guard on active ports
* Set port security on active ports as follows:
  - Accept a maximum of 4 MAC addresses
  - On violation, drop frames, log it, and send alert
  - Aging time of 10 minutes
  - Sticky MAC address learning
* Activated Dynamic ARP Inspection (DAI) globally
* Configure links to routers as trusted

## Linux Host Configuration

Set host names:
```
echo "HOSTNAME" > /etc/hostname
hostname -F /etc/hostname
```

Configured `/etc/network/interfaces` for DHCP hosts:
```
auto eth0
iface eth0 inet dhcp
```

Configured `/etc/network/interfaces` for `Admin-PC`:
```
auto eth0
iface eth0 inet static
address 192.168.10.10
netmask 255.255.255.0
gateway 192.168.10.3
```

Configured `/etc/resolv.conf` for `Admin-PC`:
```
nameserver 8.8.8.8
```

## Deliverables

### Original Case Study Deliverables

* Provide configurations from all Cisco devices
* Demonstrate connectivity from all endpoint hosts
* Demonstrate the floating static default route is working:
  - Send an extended ping from Marketing-PC to a remote site
  - Break the link between R2 and EDGE
  - The extended ping should continue with minimal dropped packets
* Demonstrate HSRP functionality:
  - Run a traceroute from Admin-PC to the ISP router
  - Break the link between R1 and R1-LAN-SW-FL1
  - Rerun the traceroute and confirm the path uses R2

### GNS3 Deliverables

* Configurations for all devices:
  [/gns3-configs/](/gns3-configs/)
* Connectivity tests from all hosts:
  [/deliverables/gns3-host-tests](/deliverables/gns3-host-tests.txt)
* Floating static default route test:
  [/deliverables/gns3-route-test](/deliverables/gns3-route-test.txt)
* HSRP functionality test:
  [/deliverables/gns3-hsrp-test](/deliverables/gns3-hsrp-test.txt)

### Packet Tracer Deliverables

* Configurations for all devices:
  [/pt-configs/](/pt-configs/)
* Connectivity tests from all hosts:
  [/deliverables/pt-host-tests](/deliverables/pt-host-tests.txt)
* Floating static default route test:
  [/deliverables/pt-route-test](/deliverables/pt-route-test.txt)
* HSRP functionality test:
  [/deliverables/pt-hsrp-test](/deliverables/pt-hsrp-test.txt)

## License

GNU General Public License v3.0

## References

[GNS3 Homepage](https://www.gns3.com/)

[Cisco Packet Tracer](https://www.netacad.com/cisco-packet-tracer)

[Alpine Linux](https://www.alpinelinux.org/)
