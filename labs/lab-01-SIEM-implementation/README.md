# Lab 01 - SIEM Implementations

## Goals:
The goals of this lab are to 
1. learn how to install different SIEM tools that are present in common cyber security postures
2. compare and contrast the setup process and layout of these different tools
3. trigger an alert on the different tools to see the alert process of each one

## Tools Used
- Splunk SIEM
- Wazuh SIEM
- QRadar SIEM
- Windows 10 (Target Device)

## Explanation of Lab Setup
I am running all of these tools on a proxmox cluster that I have running on my homelab. The only caveats to the lab are that the SIEMs have to have access to the traffic on the network that the Windows 10 and Kali VM are on. I did this through VNETs on proxmox but you could do this by just bridging the devices on to your normal network subnet since we aren't dealing with malware in these labs. This is not a networking environment tutorial so do what is best for your own lab.

## Important Links
- Windows 10 ISO: https://www.microsoft.com/en-us/software-download/windows10ISO
- KALI ISO: https://www.kali.org/get-kali/#kali-installer-images
* The links for the individual SIEMS will be included in their lab guides *
