---
title: "Introduction to Network Traffic Analysis"
date: 2026-02-24 8:00:00 +0300
categories: [Network Security, Forensics, Cybersecurity]
tags: [wireshark, tcpdump, nmap, pcap, nta]
---

**Network Traffic Analysis** (NTA) is the difference between guessing what happened on a network and knowing it. In this lab, I moved beyond connectivity testing to forensic packet inspection.  


**The NTA Lifecycle**  
I followed a structured four-stage workflow:  
**1.Ingestion:** Capturing raw data using tcpdump.  
**2.Analysis:** Using Wireshark to follow TCP streams.  
**3.Detection:** Identifying anomalies like port scans and malformed packets.  
**4.Response:** Developing a baseline of "normal" traffic to flag future threats.


**Hands-on Highlights**  

**_Command Line Proficiency_**  
I utilized **Berkeley Packet Filters (BPF)** to narrow down traffic. For example, filtering for specific IP addresses or ports directly in the terminal:  
      -  _tcpdump -r capture.pcap 'port 80 and host 192.168.1.5'_  



_**Decrypting RDP Connections**_  
A significant portion of the lab involved analyzing _**Remote Desktop Protocol (RDP)**_ handshakes. I practiced identifying the security layers used during the initial negotiation.  

_**Reflection**_  
This module transformed my approach from observing connectivity to interrogating the underlying data. I learned that clear-text protocols (like HTTP or Telnet) are a goldmine for attackers, as passwords can be extracted from a simple packet capture.  


_**Troubleshooting**_  
During the lab, I encountered a crashing Ubuntu VM (ARM64). I utilized terminal auditing tools like find and ls -F to recover my directory structure and successfully resume the analysis.  

_**Status: Completed as part of CyberShujaa Week 2.**_

