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
<img src="/Assets/SuricataDiagram2.png" width="500" height="354" />
</p>

Here is another diagram representing the data flow Suricata to Evebox.

<p align="center">
<img src="" width="200" height="200" />
</p>

# Technologies Used

# Installation & Setup
### Suricata
Firstly, Suricata needs to be installed. This can be done initially by run getting the latest version of the software and performing any necessary updates first.
```bash
sudo apt-get update && apt-get upgrade
```
Once the system is up-to-date the following need to be ran:
```bash
sudo apt-get install software-properties-common
sudo add-apt-repository ppa:oisf/suricata-stable
sudo apt update
sudo apt install suricata jq
```
The above commands add the required repositories that are required to run Suricata.

Next, the Suricata yaml file need to be configured. This is located by default in /etc/suricata/

Using Nano, the file can be edited. The variables that need to be changed are the following:
 * HOME_NET - Here the network ip address range can be set.
 * af-packet - Interface variable name must be set to the same interface name as the network the device is connected to e.g. eth0.
 * rule-files - Here the rules files need to be set, by default there is "suricata.rules" which is located or must be created in the directory: /var/lib/suricata/rules
 * pfring -  The network interface name is set to be the same as af-packet.

If there are any issues the engine will output error log on the terminal. 

Most common issues are that the suricata.rules file or /var/lib/sucirata/rules direcotry are not created.

This can be fixed by creating the directory:
```bash
sudo mkdir /var/lib/suricata/rules
cd /var/lib/suricata/rules
sudo nano suricata.rules
```

The rules can be set manually or imported from online sources. In this case the rules were created manually.

A simple rule that checks for ICMP Packets (ping) is the following:
```bash
alert icmp any any -> $HOME_NET any (msg:"ICMP Ping Detected"; classtype:network-scan; sid:100001; rev:1;)
```
In the Network Monitoring & Detection an image of all the rules used is provided.

Finally, starting the Suricata service and specifying the ethernet interface. Since the focus in only in the local network, the interface eth0 is going to be used.
```bash
sudo suricata -c /etc/suricata/suricata.yaml -i eth0
```

In order to test if Suricata and the rules used are active, the fast log file could be examined in real time as Suricata is running. This can be done by using the Tail command:
```bash
sudo tail -f /var/log/suricata/fast.log
```
This will print on a terminal the live output of the Suricata engine, if an alert is triggered, the engine will log it and the fast.log file will be populated enable the user to observe the alert and act accordingly.


### Evebox
In order to enable the Evebox Dashboard the installation of Evebox 0.20.2 took place. 

Downloading the portable server and executing the following command inside the folder to start it up.

```bash
./evebox server -D . --datastore sqlite --input /var/log/suricata/eve.json
```
The server is started and the input is set to the output log of Suricata that gets updated in real time.

# Network Monitoring & Detection
The following image shows the rules used in order to detect and notify the administrator of any suspicious activity inside the local network.
<p align="center">
<img src="/Assets/surRules.PNG" width="428" height="363" />
</p>

# Visualization

# Testing & Validation


# Future Improvements

# Conclusion

# References

