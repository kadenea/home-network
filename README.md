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

And the IP interface configuration:

<img width="823" height="517" alt="Screenshot 2025-10-19 124211" src="https://github.com/user-attachments/assets/ffb48e0e-df4f-4637-98f3-da9a2f648d04" />

I then assigned the IP address and subnet mask on my laptop, configured the trunk port on the switch to f0/1, and began configuration of subinterfaces g0/0.10 and g0/0.20 on the router using "encapsulation dot1q" to allow the for the VLANs to share the same physical interface.

<img width="809" height="373" alt="Screenshot 2025-10-19 124442" src="https://github.com/user-attachments/assets/58fa7085-83cb-4e78-b39b-0cd91cc88ca6" />

<img width="804" height="153" alt="Screenshot 2025-10-19 125018" src="https://github.com/user-attachments/assets/f2ef08c4-219e-4ae6-9926-d5a85b6c6030" />

After this I attempted to ping the subinterface g0/0.10 from the laptop unsuccessufully. I compared the running configuration on both the switch and router to my working packet tracer and found that both configuration were the same according to the addressing table and all neccessary interface were labeled as "UP". So I then checked the configuration on my laptop and found that I had not configured a default gateway. So I assigned it to the g0/0.10 interface on the router and was able to recieve a reply back.

<img width="620" height="941" alt="Screenshot 2025-10-19 141806" src="https://github.com/user-attachments/assets/d556c3a4-a6d5-4afb-8803-74e69334b666" />

<img width="1475" height="526" alt="Screenshot 2025-10-19 130024" src="https://github.com/user-attachments/assets/5c58843a-84d0-483d-81dd-cf49fcfaaa1f" />

After this I was then able to ping through the network to VLAN 20 on the switch and has successfully configured both VLANs along with inter-VLAN routing using subinterfaces on the router.

<img width="1476" height="753" alt="Screenshot 2025-10-19 130846" src="https://github.com/user-attachments/assets/2c614a29-f469-4f1e-84ee-d752e28ef2dc" />

This is what the physical network looked like after completion: 

![IMG_2954](https://github.com/user-attachments/assets/3d0a1def-889e-49b3-9834-c79052267d4d)

### Final Thoughts

Looking back after completing this first step in this project, I belive the process went very smoothly. Planning and testing everything beforehand definitely helped this greatly. The actually implementation felt very easy after I had already run through it before. Other than the speed bump with the default gateway which I had corrected reltively quickly, there were almost no other issues. One of the biggest difficulties with this stage was the initial setup as it was pretty tedious. I had to make sure I had a console cable with a USB port, a USB-A to USB-C adapter, a RJ-45 to USB-C adapter, and the PuTTY software correctly installed. 
