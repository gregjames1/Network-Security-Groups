<p align="center">
<img src="https://i.imgur.com/Ua7udoS.png" alt="Traffic Examination"/>
</p>

<h1>Network Security Groups (NSGs) and Inspecting Traffic Between Azure Virtual Machines</h1>
In this tutorial, we observe various network traffic to and from Azure Virtual Machines with Wireshark as well as experiment with Network Security Groups. <br />

<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Various Command-Line Tools
- Various Network Protocols (SSH, RDH, DNS, HTTP/S, ICMP)
- Wireshark (Protocol Analyzer)

<h2>Operating Systems Used </h2>

- Windows 10 (21H2)
- Ubuntu Server 20.04

<h2>High-Level Steps</h2>

- Create resources in Azure (resource groups, VMs).
- Connect to VM and install WireShark.
- Observe and experiment network traffic (ICMP, SSH, DHCP, DNS) and inbound security rules.

<h2>Actions and Observations</h2>

<p>
<img width="765" alt="Screenshot 2023-08-06 at 6 27 17 PM" src="https://github.com/gregjames1/Network-Security-Groups/assets/129281605/3f7fa5ab-fa7c-4590-a1a3-7a11174e72f3"
"/>
<img width="792" alt="Screenshot 2023-08-06 at 6 32 03 PM" src="https://github.com/gregjames1/Network-Security-Groups/assets/129281605/63168035-e10f-4622-ab14-370cd0e6338e">


</p>
<p>
Log into your Azure account and create your resources - you will need to create a Resource Group near your location (for example: US West 3). Then create two Virtual Machines and select the resouce group that you created earlier for each of these to ensure they share the same permissions, policies, and network. Allow the first VM to create a new Vnet and Subnet. While creating the second VM, select the previously created resource group and Vnet.
</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Remote into your Windows VM using Remote Desktop (you will log in with the username and password that you set up while you were creating the VM) and install Wireshark. Follow the installation steps and open the program once finished. Run PowerShell as an Administrator and ping your second VM (Ubuntu Server) using its private IP Address. Filter for ICMP traffic in Wireshark and observe the network traffic.
</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.
</p>
<br />
