# **ccna-srwe-case-study**

This project uses GNS3 and Cisco Packet Tracer to create a network based
on a case study assigned as the final practical skills assessment for my
CCNA: Switching, Routing, and Wireless Essentials course.
The case study was designed to test skills gained throughout the course and
required that I build and configure a complex network on physical equipment.

## Network Topology

![Network Topology Diagram](topology.png)

## Skills Demonstrated

* Cisco router and switch configuration
* VLAN and switchport VLAN membership configuration
* EtherChannel configuration
* Static trunking and Dynamic Trunking Protocol (DTP)
* Inter-VLAN routing (router-on-a-stick) configuration
* IPv4 floating static, default, and host routes
* Hot Standby Router Protocol (HSRP) configuration
* Dynamic Host Configuration Protocol (DHCP) pools and scopes
* Switch security, including port security, Dynamic ARP Inspection (DAI),
  PortFast, and BPDU Guard

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
    <td colspan="2">Virtual Gateway for R1 and R2</td>
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
    <td colspan="2">DHCP</td>
  </tr>
  <tr>
    <td>Marketing-PC</td>
    <td colspan="2">eth0 Network Interface</td>
    <td colspan="2">DHCP</td>
  </tr>
  <tr>
    <td>Logistics-PC</td>
    <td colspan="2">eth0 Network Interface</td>
    <td colspan="2">DHCP</td>
  </tr>
  <tr>
    <td>Management-PC</td>
    <td colspan="2">eth0 Network Interface</td>
    <td colspan="2">DHCP</td>
  </tr>
</table>


## License

GNU General Public License v3.0
