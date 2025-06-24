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
4. Find a failed login attempt by filtering through log data
5. Create a dashboard that shows a timeline of failed login attempts
6. Create a security rule that triggers when there are 5 failed login attempts within 5 minutes

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

Now to access the dashboard you would go to the IP of my wazuh server and login using the login info that my command line gave me. But first you might need to bypass the browser warning if you don't have SSL certificates set up. Examples below:

![12_wazuh_security_warning](https://github.com/user-attachments/assets/dce9f997-74ee-40e3-b0c9-8ce46565588e)

![13_wazuh_login_page](https://github.com/user-attachments/assets/2c07b7d7-6398-4ddd-aa35-54be5a45d230)

After you get past the login page you are presented with the Wazuh homepage that we will be exploring. We will start by adding a new agent to monitor and we will start by clicking the part highlighted in the picture.

![14_wazuh_home_page](https://github.com/user-attachments/assets/7930df64-7054-4183-bffa-38703fd2614f)

### Step 4: Adding an Agent

To make the most of the Wazuh server we need an agent to be able to actually send it logs that we can analyze. For this lab I set up a windows VM. Wazuh makes it very easy to download the agent from the command line which is what I did. The only thing you have to make sure of is that you replace the 10.0.0.99 with the IP of your server and that should conenct the agent to the server and automatically forward logs from your device.

![21_windows-10-wazuh-download-command](https://github.com/user-attachments/assets/56284894-76f9-4a6c-a097-5b1cc13b173f)

Once the agent is running on the new windows VM we should be able to go back to our Wazuh webpage and click on our agents tab in the top right and see that our new windows VM is connected to our server.

![23_wazuh_agent_connected](https://github.com/user-attachments/assets/6db1fb19-3115-4cae-9288-4d339d61b146)

### Step 5: Exploring the Dashboard

From the home page we want to see all of the options that Wazuh has to offer and while we won't visit all of them in-depth in this tutorial I will briefly touch on what each section is used for. To see all of what Wazuh has to offer we can click on the hamburger menu bar in the top left and it opens to this.

![24_wazuh_dropdown_menu](https://github.com/user-attachments/assets/2b09d143-7166-4cda-b2c7-4b33b3b490c9)

- The "Home" tab is where we have our main dashboard that we previously looked at and that's pretty much the only option there is under that tab.
- The "Explore" Tab is where we will be spending most of our time in this lab and it is where we are able to analyze the logs that we collect and look for evidence of malicious activity. We are also able to make custom dashboards, reports, and alerts in this section.
- The "Endpoint Security" tab is where we are able to set up any EDR rules that we want and perform file integrity monitoring and malware detection.
- 



