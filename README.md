# Home Network Setup

In this project, I will be setting up a small network at my home using Cisco primarily Cisco hardware. I plan on setting up basic configurations, VLANs, IP routing, router-on-a-stick, ACLs, among other common network configurations.

## Initial Planning

Here, I will be creating my initial plan for my network. This primarily consists of creating an addressing table and configuring it in a packet tracer simulation to verify that it will work before implementing any changes.

### Stage 1 - VLANs and Router-on-a-Stick

This Cisco network consists of a single switch, a router configured using the router-on-a-stick method, and 2 end devices connect to the switch. The switch has two VLANs with 4 access ports assigned to each and a trunk port connecting to the router. The router is configured with sub-interfaces for each VLAN, allowing inter-VLAN communication through a single physical link. Basic configurations such as hostnames, console passwords, and service password encryption are also applied to enhance network management and security.

The network will be congigured using this routing table:
<img width="509" height="169" alt="image" src="https://github.com/user-attachments/assets/86306cf0-a471-4ab2-9f70-25d93cb2034d" />
