# Lab 02 - IDS/IPS Implementation

## Important Links
- Suricata Installation Guide: https://docs.suricata.io/en/latest/quickstart.html
- Zeek Installation Guide: https://docs.zeek.org/en/master/install.html 

## Goals

- Deploy Suricata and/or Zeek as network-based intrusion detection systems (NIDS)
- Generate known attack traffic to trigger alerts
- Understand how packet inspection contributes to Blue Team visibility

## Dependencies

This lab is built upon the VMs from the previous lab. The only real dependency is a Kali device to trigger alerts on the IDS/IPS VMs.

---

## Tools Used

| Tool      | Purpose                               |
|-----------|----------------------------------------|
| Suricata  | Real-time network IDS/IPS engine       |
| Zeek      | Passive network traffic analyzer       |
| Kali VM   | Attack simulator (e.g., Nmap, Hydra)   |
| ELK/Splunk/QRadar | Log aggregation & alert correlation |
| Filebeat  | Log shipper (optional for SIEM ingest) |

---



