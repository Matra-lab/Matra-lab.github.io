---
layout: page
title: Lab Challenges
icon: fas fa-flask
order: 5
---

**Challenge:** The verification on both the switches was not quite a success as I utilized the  show port-security _interface f0/6_ & show port-security _interface f0/18  commands_ to obtain the addresses.  
**_Fix:_** Later on after all the configurations was done I enabled DHCP on PC-A which was on static and the address finally loaded 🎉.  
**Persistent issue:** The  show port-security interface address is the only portion of the code that persisted and never changed because even after all configurations were complete, the address was still null/ blunk.  



**Running config script on Switch 2 to get IP address on PC-B**  
**-Challenge:** If you load the running-config script on S2, PC-B on port 18 never gets an IP address via DHCP?  
When the running configuration is reloaded, any sticky MAC addresses that were saved could already occupy the maximum number of allowed MAC addresses (2 in this case).violation mode “protect” silently drops excess frames, preventing DHCP packets from the legitimate PC-B MAC from reaching the server.Because the port is not shutdown and no violation counter incremental is obvious, PC-B appears connected but never receives a DHCP lease.  
**Solution:** This was the solution I found but i didn't apply it on the lab;  
-_Configure switchport port-security aging type inactivity and aging time (e.g., 2 minutes) on the port to age out inactive saved sticky MAC addresses, allowing new legitimate MACs to be learned._



**Ping Cmd Misconfigurations**  
**Challenge:** PC-B's initial static IP configuration was mismatched with the network parameters, likely involving an incorrect IP address, subnet mask, or default gateway. This permitted local connectivity (successful pings to 192.168.1.1, the local router interface) but blocked access to external IPs like 209.165.200.226, causing request timeouts due to improper routing or address resolution.  
**Solution:** Switching to DHCP from static resolved this by dynamically obtaining valid settings from the DHCP server, including the correct IP, subnet, gateway, and DNS, thereby enabling end-to-end connectivity and successful pings.  


**Mitigating Man-in-the-Middle Attacks (DHCP Snooping)**   
To defend against “rogue DHCP Server” attacks, DHCP Snooping was implemented. This feature treats all access ports as “untrusted” by default.  
I used two methods to mitigate this:  
_1.Trust Anchors:_ The uplink to R1 (via S1) was explicitly configured as a trusted port, allowing legitimate DHCP offers to reach clients.  
_2.Rate Limiting:_ Access ports were limited to 5 DHCP packets per second to prevent DHCP starvation attacks which attempt to exhaust the router’s IP address pool.    

! S2 DHCP Snooping Implementation
ip dhcp snooping
ip dhcp snooping vlan 10
interface f0/1
 ip dhcp snooping trust
interface f0/18
 ip dhcp snooping limit rate 5 

 
