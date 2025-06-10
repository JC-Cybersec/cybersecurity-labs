# Lab 01-b Wazuh SIEM Implementation

## Important Links
- Wazuh Core Components Installation Guide: https://documentation.wazuh.com/current/quickstart.html
- Wazuh Agent Installation Guide: https://documentation.wazuh.com/current/installation-guide/wazuh-agent/index.html
- Ubuntu Server 22.04: https://releases.ubuntu.com/jammy/

## Objectives:
The objectives for this sublab are to:
1. Download and setup the Wazuh Core Components (Indexer, Server, Dashboard) on Ubuntu Server 22.04
2. Download and stup the Wazuh Agent on our Windows Device
3. Explore the Wazuh UI
4. Trigger an alert on the dashboard from our Windows 10 Agent

## Guide
### Step 1: Installing Ubuntu Server
The first thing that needs to happen for Wazuh to be implemented on our network is that we need a computer to handle all of the data processing and retrieving. Wazuh handles all of this with three different components; Wazuh Indexer, Wazuh Serrver, and Wazuh Dashboard. All of these components can be downloaded and ran separately, but for ease of implementation we are going to run all three of these on the same VM. Wazuh offers several OS options but I chose to install in on Ubuntu Server 22.04 because it is more lightweight than the other options and is nowhere near EOL. I also gave it the minimum specs solely because it will not be indexing a ton of endpoints simultaneously. You can see the picture below for the reference of what options are available. 

![1_Wazuh_Install_Guide](https://github.com/user-attachments/assets/b6f03aee-df0a-4064-b29a-2fa6870dfce7)

After deciding what specs to give my server I needed to actually create the VM. Proxmox makes this fairly simple but you can do this in any VM environment as long as you have the compute power. Next I had to find the Ubuntu Server ISO to download which is linked at the top. Below is a screenshot of what the landing page looks like. MAKE SURE TO INSTALL THE SERVER VERSION AND NOT DESKTOP. 

![2_Ubuntu_Install_Page](https://github.com/user-attachments/assets/da6db5a0-d518-4dba-a8ef-b494e46cff18)

Once your VM OS and hardware is setup the actual setup process is straightforward. One of the steps to not mess up is choosing your network settings. I just chose DHCP so I knew the IP was available and then set it to static afterwards but you can static the IP straight from this menu. I chose 10.0.0.99 for my server IP but this will vary based on your lab setup. 

![6_Ubuntu-network-setup](https://github.com/user-attachments/assets/13c47a42-6915-4984-b461-d7ca3302812c)

Now that you have completed your setup and login you should be ready to move onto installing Wazuh. Here is what your initial login should look like.

![8_Ubuntu-login-screen](https://github.com/user-attachments/assets/773327bb-83c1-4e36-b96a-cff5fd0cb170)

### Step 2: Installing Wazuh on the Server
I chose to SSH into my server from this point but the process would be the same on the normal command line. Once you are at your command line the Wazuh installation guide has a command that you can paste to your command line and begin your download immediately. This is what it looked like on my server. 

![10_Wazuh-download](https://github.com/user-attachments/assets/d2551a78-db21-4d3c-b591-22f31149d845)

Once the command is complete you should get a notice that it is installed and the user and password that will be used to access the web interface.

![11_wazuh_installation_complete](https://github.com/user-attachments/assets/85bc5735-91ae-4946-ac45-55df36a048ef)

In this case I would use the IP 10.0.0.99 instead of 'wazuh-dashboard-ip'

### Step 3: Accessing the Dashboard
