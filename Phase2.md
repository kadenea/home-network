# Phase 2

In this phase of my home network project, I update the network configurations and add in my second Cisco 2911 router and a 48 port Cisco Catalyst 3650 (even though this is a layer 3 switch, IP routing will not be enabled for the sake of this lab). The new topology and configuration will add redundancy and load-balancing for traffic being passed through each network.

## Initial Planning

To start, I knew I wanted to work with HSRP. I had an extra Cisco 2911 router laying around unused and my other router was just sitting as a Router-on-a-Stick from Phase 1. I also had not had much experience with HSRP and wanted to test it out.

I then began brainstorming the topology I wanted to use. I have not yet connected my network to the internet as our router sits in my parents room and there is no way to connect it currently without either moving my entire network to their room, or running a 100 foot cable through the house. However, I knew I wanted to access the external internet at some point in the near future. Right now, I have a Raspberry Pi 5 sitting unused in my room but my goal for the next part of this project is to set up a PiHole DNS sinkhole as well as PiVPN to allow me to SSH into my networking devices remotely. Given this, I wanted to set up my users and servers on two separate VLANs. This will help improve security, enforce access control, QoS/traffic engineering, and reduce broadcast traffic.

##Implementation

I settled on a multi-group HSRP architecture. This involves the switches being fully meshed with the routers and each other, providing maximum redundancy with little extra cost. I will have one HSRP group for each VLAN on the routers. R1 will act as the gateway for the users (VLAN 10) and R2 will act as the gateway for the servers (VLAN 20). This separates the traffic from each VLAN so each router gets utilized and traffic is load balances across each to maximize performance. 

<img width="405" height="347" alt="image" src="https://github.com/user-attachments/assets/1cdc3385-92c5-46fc-851d-b27f3427e3cc" />

Also, in order to avoid the physical port limitations of the traditional Router-on-a-Stick topology, I configured Bridge Virtual Interfaces (BVIs) on the routers to bundle subinterfaces into unified Layer 3 logical domains. I also wanted to align each switch Also, given that each VLAN is assigned to different physical gateways an

<img width="1286" height="167" alt="Screenshot 2026-06-16 184336" src="https://github.com/user-attachments/assets/535ce30d-ba6d-4b29-9a73-8b916cde0f15" />
