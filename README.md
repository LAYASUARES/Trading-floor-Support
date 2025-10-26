# Trading-floor-Support

## 🌟 Project Overview

This repository documents the logical design and implementation of a robust, redundant, and future-proof enterprise network solution for a new Trading Floor Support Center, accommodating approximately 600 staff across three floors.

The solution is implemented using a Hierarchical Network Model and leverages Cisco technologies within Packet Tracer to meet high availability, scalability, and security requirements.

## Project Goal

To design and implement a new corporate network from scratch in a new three-story building, replacing the existing infrastructure, ensuring current business needs are met, and providing redundancy at every critical layer.

## Network Scope and Structure

The new building spans three floors and houses six main logical departments/areas:

| Floor | Department/Area | Estimated Users/Devices |

| 1st Floor | Sales and Marketing / Human Resources and Logistics | 240 users 120 at each department |

| 2nd Floor | Finance and Accounts / Administration and Public Relations | 240 users 120 at each department |

| 3rd Floor | ICT Department / Server Room | 120 users inthe department and 12 devices at ServerRoom |

## 🛠️ Technical Requirements and Implementation Details

1.  Topology and Redundancy

- Model: Hierarchical Model.
- Core Redundancy: Two (2) Routers and two (2) Multilayer Switches are used to provide redundancy at the core/distribution layer.
- ISP Redundancy: Connection to at least two Internet Service Providers (ISPs), with each router connected to both ISPs.

2. IP Addressing and Subnetting
   -Base Network: The private base network is 172.16.1.0

- Subnetting: VLSM (Variable Length Subnet Masking) was applied to allocate the correct number of IP addresses for each department's unique subnetwork.
- Public IPs (ISP Links): The public IP spaces used for ISP connectivity are: 195.136.17.0/30, 195.136.17.4/30, 195.136.17.8/30, and 195.136.17.12/30.

3. Layer 2 / Layer 3 and Routing

- VLANs: Each department is isolated into a different VLAN and subnetwork.
- Inter-VLAN Routing: Configured on the Multilayer Switches (Layer 3 switches).
- Routing Protocol: OSPF (Open Shortest Path First) is used to advertise routes across all routers and multilayer switches.
- Multilayer Switches: Expected to perform both routing and switching functionalities and are assigned IP addresses.

4. Services

- DHCP: Dedicated DHCP servers located in the Server Room dynamically allocate IP addresses to all department devices.
- Static IPs: Devices within the Server Room are assigned static IP addresses.
- Wireless: Each department has a configured wireless network for user access.
- NAT: PAT (Port Address Translation) is configured using the respective outbound router interface IPv4 address, supported by necessary ACL rules.

5. Security and Access

- Remote Management: SSH is configured on all routers and Layer 3 switches for secure remote login.
- Device Hardening: Basic device settings (hostnames, console/enable passwords, banner messages, disable IP domain lookup) are configured.
- Port Security (Finance/Accounts): Port-security is implemented for the Finance and Accounts department to allow only one device per switch port, utilizing the sticky MAC address method and shutdown as the violation mode.

## Implementation and Validation

The solution was designed and implemented using Cisco Packet Tracer.

All communication paths and configured services, including inter-VLAN routing, OSPF advertisement, PAT, and DHCP services, have been tested and validated to ensure expected functionality.

### Repository Structure

- PacketTracer/: Contains the .pkt file of the final network topology.
- Documentation/: Includes the IP addressing scheme, VLAN table, and OSPF configuration summary.
- Configurations/: Includes text files with the running configuration of key devices (Routers, Multilayer Switches, DHCP Servers).
