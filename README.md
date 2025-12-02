# Wazuh – OVA Installation Guide

[![Wazuh](https://img.shields.io/badge/Wazuh-4.8.2-blue)](https://wazuh.com/) 
[![License](https://img.shields.io/badge/License-MIT-green)](LICENSE)

This repository documents the installation and configuration of the **Wazuh OVA appliance** in a lab environment, including manager setup, dashboard access, and agent registration.

---


## Requirements



### Hardware
- CPU: 4 vCPUs  
- RAM: 8 GB  
- Disk: 50–100 GB  
- Virtualization: VMware Workstation, VirtualBox, or ESXi  

### Network
- Static IP recommended  
- Internet access for updates  
- Ports required: 1514/udp (logs), 55000/tcp (API)  

### Software
- VMware Workstation or VirtualBox  
- Access to Wazuh GitHub releases  



---

## Environment

- Wazuh virtual machine image
---



## Download OVA

Download the latest OVA from the official Wazuh GitHub release page:

```text
https://github.com/wazuh/wazuh/releases
wazuh-4.8.2.ova
```

## Deploy OVA




1. Open VMware Workstation → **File → Open** → select `wazuh-<version>.ova`  
2. Accept default hardware settings or adjust as needed  
3. Import and start the VM  
4. Wait 3–5 minutes for Wazuh Manager, Indexer, and Dashboard to initialize  



---

## First Boot & Login


<summary>Click to expand</summary>

The VM will display:

```text
Wazuh Dashboard URL: https://<IP_ADDRESS>
Username: admin
Password: admin 
```


  ### Recommended: Set Static IP


<summary>Click to expand</summary>

### Step 1: Check Current IP


```bash
ip a
```
### Step 2: Edit Netplan Configuration
```bash
sudo nano /etc/netplan/01-netcfg.yaml
```
### Step 3: Example Configuration
```bash
network:
  version: 2
  ethernets:
    ens33:
      dhcp4: no
      addresses:
        - 192.168.1.20/24
      gateway4: 192.168.1.1
      nameservers:
        addresses: [1.1.1.1, 8.8.8.8]
```
### Step 4: Apply Changes
```bash
sudo netplan apply
```
## Wazuh Dashboard – Successful Installation

Once the Wazuh OVA is deployed and agents are connected, you should see the dashboard similar to the screenshot below:

![Wazuh Dashboard](images/wazuh_dashboard.png)





