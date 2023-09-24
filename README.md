# BGP at the Doors of Autonomous Systems (BADASS)

Badass is a simulation and configuration of networks using GNS3 with docker images.

## Table of Contents

- [Project Overview](#project-overview)
  - [Part 1: GNS3 Configuration with Docker](#part-1-gns3-configuration-with-docker)
  - [Part 2: Discovering a VXLAN](#part-2-discovering-a-vxlan)
  - [Part 3: Discovering BGP with EVPN](#part-3-discovering-bgp-with-evpn)
- [Technologies and Concepts](#technologies-and-concepts)
  - [Border Gateway Protocol (BGP)](#border-gateway-protocol-bgp)
  - [Virtual Extensible LAN (VXLAN)](#virtual-extensible-lan-vxlan)
  - [Docker](#docker)
  - [Graphical Network Simulator-3 (GNS3)](#graphical-network-simulator-3-gns3)
  - [Route Reflection](#route-reflection)
  - [MAC Address Learning](#mac-address-learning)
- [Problem Solving](#problem-solving)

## Project Overview

The BADASS project is a hands-on journey that involves three main parts:

### Part 1: GNS3 Configuration with Docker

In this initial phase, we set up the GNS3 network emulator within a virtual machine and configured Docker images to create a solid foundation for our network. We created two Docker images:

1. **Image 1**: We chose a system image (I went with Alpine) and ensured it included Busybox or an equivalent solution.

2. **Image 2**: For this image, we set up specific services, including packet routing management (using Zebra or Quagga), BGPD configuration, OSPFD configuration, an IS-IS routing engine service, and, of course, Busybox or an equivalent tool.

The ultimate goal was to have both these Docker machines working seamlessly in GNS3. We made sure that all configurations were neatly organized in a designated folder for easy access and management.

### Part 2: Discovering a VXLAN

The second part of the project was all about exploring the power of Virtual Extensible LAN (VXLAN) technology. VXLAN is a game-changer in overlay network virtualization. Here's what we did:

- Configured VXLAN with an ID (I chose ID 10).
- Set up a bridge (br0) and configured Ethernet interfaces as needed.

This part allowed us to establish communication between machines within the VXLAN, with the added bonus of automatic MAC address and route discovery.

### Part 3: Discovering BGP with EVPN

Our final mission took us deep into the world of BGP EVPN (Ethernet Virtual Private Network) without the complexities of MPLS. BGP EVPN simplifies network management within data centers, and here's what we accomplished:

- Created a data center topology with Virtual Tunnel Endpoints (VTEPs).
- Implemented Route Reflection (RR) to make routing more efficient.
- Demonstrated MAC address learning and the configuration of route types.

## Technologies and Concepts

Let's delve into the networking technologies and concepts that powered our journey through the BADASS project:

### Border Gateway Protocol (BGP)

**Border Gateway Protocol (BGP)** is a pivotal component of the Internet's routing infrastructure. It's a path vector routing protocol that operates at the internet layer (Layer 3) and plays a crucial role in directing traffic between Autonomous Systems (ASes). Key aspects of BGP in this project include:

- **AS (Autonomous System)**: An AS is a collection of IP networks and routers under the control of a single organization. BGP is used to exchange routing information between ASes.

- **Route Advertisement**: BGP is used to advertise network reachability information, which includes prefixes (IP address ranges) and associated attributes. These advertisements help routers make informed routing decisions.

### Virtual Extensible LAN (VXLAN)

**Virtual Extensible LAN (VXLAN)** is a network virtualization technology designed to address the challenges of scaling and segmenting networks in large data center environments. Key aspects of VXLAN in this project include:

- **Overlay Network**: VXLAN creates overlay networks on top of existing physical networks, allowing for the creation of logical network segments that are isolated from the underlying physical infrastructure.

- **VXLAN ID**: VXLAN segments are identified by a unique VXLAN Network Identifier (VNI), which is a 24-bit value. VNIs provide segmentation within the overlay network.

- **Encapsulation**: VXLAN encapsulates Ethernet frames within UDP packets, enabling these frames to traverse Layer 3 (IP) networks. This encapsulation is vital for extending Layer 2 connectivity across Layer 3 boundaries.

### Docker

**Docker** is a containerization platform that simplifies the packaging, distribution, and execution of applications and their dependencies. In the project, Docker was used to create and manage container images for various networking components. Key aspects of Docker in this project include:

- **Containers**: Containers are lightweight, isolated environments that package an application and its dependencies. They are used to encapsulate networking services and tools in a consistent manner
