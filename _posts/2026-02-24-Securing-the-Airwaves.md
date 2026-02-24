---
title: "Packet Tracer WLAN Configuration"
date: 2026-02-24 7:00:00 +0300
categories: [Network Security, Labs]
tags: [Cisco, WPA2, WLC, Packet-Tracer, Cybersecurity]
---

In this lab, I simulated the deployment of a secure **Wireless Local Area Network (WLAN)** for a **SOHO** (Small Office/Home Office) environment. The goal was to ensure internal hosts could securely access a web server on the WAN while maintaining data integrity.  

##**Core Objectives**
- Configure a home router to obtain WAN addressing via DHCP.  
- Deploy a Wireless LAN Controller (WLC) to manage access points.
- Secure the WLAN using WPA2-PSK (AES) encryption.
- Verify end-to-end connectivity between wireless hosts and an external server.

##**Technical Implementation**  
**WLC & AP Configuration**  
Working with the WLC (192.168.100.254), I defined the SSIDs and mapped them to the appropriate VLANs. A critical step was ensuring the APs could join the controller and broadcast the secure SSID.  


##**Security Hardening**  
I moved away from default settings, implementing:  
- WPA2-Personal (AES): To prevent unauthorized eavesdropping.
- Admin Hardening: Changed default credentials on the router and WLC.


##**Key Takeaway**
Wireless networks are often the weakest link in an organization's perimeter. This lab reinforced the importance of the WLC-based architecture in enterprise environments, where centralized security policies are much easier to manage than individual standalone routers.

**_Status: Completed as part of CyberShujaa Week 4._**
