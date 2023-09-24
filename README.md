# BGP at the Doors of Autonomous Systems (BADASS)
<img src="https://media.licdn.com/dms/image/C4E12AQHju1zPrndgsg/article-inline_image-shrink_1000_1488/0/1652626726913?e=1700092800&v=beta&t=2F_VUG5C9zuC5i5I1epYav5S6DTTQNaEqskix2fJ72Q" />

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

- **Containers**: Containers are lightweight, isolated environments that package an application and its dependencies. They are used to encapsulate networking services and tools in a consistent manner.

- **Image**: A Docker image is a snapshot of a container's file system and configuration. Images are used to create and run containers. In the project, you created and configured Docker images for specific networking tasks.

### Graphical Network Simulator-3 (GNS3)

**Graphical Network Simulator-3 (GNS3)** is a popular network emulator that allows you to create and simulate network topologies for testing and learning purposes. In this project, GNS3 served as the platform for building virtual network environments. Key aspects of GNS3 in this project include:

- **Emulation**: GNS3 emulates network devices such as routers, switches, and firewalls. It provides a realistic environment for testing network configurations.

- **Topology Design**: GNS3 allows you to design complex network topologies by connecting virtual devices and configuring their properties. It supports various operating systems and virtualization technologies.

### Route Reflection

**Route Reflection** is a BGP technique used to simplify the distribution of routing information within an Autonomous System (AS). In the project, route reflection was employed to make BGP routing more manageable. Key aspects of route reflection include:

- **BGP Route Distribution**: In large BGP networks, distributing routes to all peers can be challenging. Route reflection introduces the concept of route reflectors, which selectively reflect BGP routes to specific peers, reducing the complexity of full mesh peering.

- **Route Reflector (RR)**: A route reflector is a BGP router that reflects routes from its clients to other clients. It allows for a hierarchical BGP topology, improving scalability.

### MAC Address Learning

**MAC Address Learning** is fundamental in Ethernet-based networks, where devices use MAC addresses to communicate within a local network segment. In the project, MAC address learning was a key component of BGP EVPN. Key aspects of MAC address learning include:

- **Ethernet Frames**: Devices in an Ethernet network communicate by sending Ethernet frames. These frames include source and destination MAC addresses.

- **MAC Address Table**: Ethernet switches maintain MAC address tables that map MAC addresses to specific switch ports. When a frame arrives at a switch, it uses the MAC address table to determine where to forward the frame.

- **Dynamic MAC Learning**: In BGP EVPN, MAC addresses are learned dynamically as devices communicate. This dynamic learning allows for efficient MAC address table updates, reducing network management overhead.

These networking concepts underpin the BADASS project and play a vital role in configuring, managing, and optimizing network operations within a data center environment.

## Problem Solving

This project addressed some of the most common and complex challenges in modern data center environments:

- Configuration and management of dynamic routing protocols like BGP and OSPF.
- Establishment of overlay networks using VXLAN for network segmentation.
- Simplification of route distribution and management within an AS through BGP route reflection.
- Efficient learning and management of MAC addresses within a data center using BGP EVPN.

By successfully completing this project, we've gained valuable insights and skills in network administration and configuration.

Kudos to us for conquering the BADASS project! 🚀 Feel free to explore the code and configurations in the respective project folders (P1, P2, and P3) to see the magic happen.

If you have any questions or want to discuss network wizardry, reach out anytime! 😄🌐

