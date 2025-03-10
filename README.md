# HomeShield_IDS

HomeShield is a home network security monitoring project that intergrates Suricata (NIDS) with EveBox Dashboard.

<p align="center">
  <img src="https://github.com/user-attachments/assets/d8371946-7fd3-4547-b47a-c191eaab5f96" width="256" height="256" />
  &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
  <img src="https://github.com/user-attachments/assets/8ba3728c-110f-4c13-93ff-ebb4825d8346" width="256" height="256" />
  &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
  <img src="https://github.com/user-attachments/assets/22085dc1-2afa-4f0b-bc45-6c84fd7169b2" width="256" height="256" />
</p>

# Introduction
This project enables continuous monitoring of the home network for suspicious activity within the network. The traffic is captured and stored on the system to be analyzed and displayed on the Evebox dashboard. The purpose of this project is to monitor and identify any unusual activities in order to block any malicious outgoing connections that may be putting the entire home network at risk. 

Suricata has been used as a network intrusion detection system capturing traffic from IPv4 and IPv6 addresses.
In order to elegantly present this, Evebox dashboard has been used making this similar to a SIEM system. 

Visualization and alerting has been set up so that the system administrator can observe which devices are exhibiting suspicious behaviour and proceed accordingly.

# Project Scope
HomeShield_IDS covers home network monitoring by analyzing all the packets and traffic being transmitted as well as alerting the system administrator of any suspicious activities as specified from the rules applied.

This project does not cover endpoint security meaning that individual devices and their systems are not being monitored of any internal activities. Additionally, firewall management is also not covered in this project as the focus is on network monitoring and alerting.

# System Architecture
This is a high level network diagram showing how Suricata is configured inside the network to monitor and protect devices.

<p align="center">
<img src="/Assets/SuricataDiagram2.png" width="200" height="200" />
</p>

Here is another diagram representing the data flow Suricata to Evebox.

<p align="center">
<img src="" width="200" height="200" />
</p>

# Technologies Used

# Installation & Setup

# Network Monitoring & Detection

# Visualization

# Testing & Validation

# Future Improvements

# Conclusion

# References

