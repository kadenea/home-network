# Home Network Setup

In this project, I will be setting up a small network at my home using Cisco primarily Cisco hardware. I plan on setting up basic configurations, VLANs, IP routing, router-on-a-stick, ACLs, among other common network configurations.

## Initial Planning

Here, I will be creating my initial plan for my network. This primarily consists of creating an addressing table and configuring it in a Packet Tracer simulation to verify that it will work before implementing any changes.

### Stage 1 - VLANs and Router-on-a-Stick

This Cisco network consists of a single switch, a router configured using the router-on-a-stick method, and 2 end devices connect to the switch. The switch has two VLANs with 4 access ports assigned to each and a trunk port connecting to the router. The router is configured with sub-interfaces for each VLAN, allowing inter-VLAN communication through a single physical link. Basic configurations such as hostnames, console passwords, and service password encryption are also applied to enhance network management and security.

The network will be congigured using this routing table:

<img width="509" height="169" alt="image" src="https://github.com/user-attachments/assets/86306cf0-a471-4ab2-9f70-25d93cb2034d" />

The completed and fully functional Packet Tracer topology:

<img width="446" height="457" alt="image" src="https://github.com/user-attachments/assets/c55dbddd-5656-422d-b483-24fcedec8f80" />

## Implementation

Now that I have an addressing table and working simulation I am ready to implement this into my home network. For this I will be using my Cisco Catalyst 2960 switch, Cisco 2911 Router, and my personal laptop running Windows.

I began by physically configuring by hardware by attactching a Cat 6 ethernet cable from G0/0 on the router to F0/1 on my switch. I then attatched one from F0/9 on the switch, through an RJ-45 adapter that connected to my laptop. And finally one more cable from F0/13 to what would typically be a desktop computer that I did not have on hand this day.

After that, I configured VLANs 10 and 20 on the switch following the same addressing scheme seen in the addressing table and assigned interfaces f0/9-12 to VLAN 10 and interfaces f0/13-16 to VLAN 20.

<img width="823" height="518" alt="Screenshot 2025-10-19 123834" src="https://github.com/user-attachments/assets/67e0750a-ced7-451a-8f44-e8f3caa79ce7" />

Here is the VLAN configuration:

<img width="900" height="563" alt="image" src="https://github.com/user-attachments/assets/e835d55e-1344-4f9f-9943-d87ef274ca12" />

