<p align="center">
<img src="https://i.imgur.com/Ua7udoS.png" alt="Traffic Examination"/>
</p>

<h1>Network Security Groups (NSGs) and Inspecting Traffic Between Azure Virtual Machines</h1>
In this tutorial, we observe various network traffic to and from Azure Virtual Machines with WireShark as well as experiment with Network Security Groups. <br />

<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- PowerShell
- Command Prompt
- Various Network Protocols (SSH, RDH, DNS, HTTP/S, ICMP)
- WireShark (Protocol Analyzer)

<h2>Operating Systems Used </h2>

- Windows 10 (21H2)
- Ubuntu Server 20.04

<h2>High-Level Steps</h2>

- Create resources in Azure (resource groups, VMs).
- Connect to Windows VM and install WireShark.
- Observe and experiment with ICMP traffic
- Observe SSH traffic
- Observe DNS traffic

<h2>Actions and Observations</h2>

<p>
<img width="765" alt="Screenshot 2023-08-06 at 6 27 17 PM" src="https://github.com/gregjames1/Network-Security-Groups/assets/129281605/3f7fa5ab-fa7c-4590-a1a3-7a11174e72f3"
"/>
<img width="792" alt="Screenshot 2023-08-06 at 6 32 03 PM" src="https://github.com/gregjames1/Network-Security-Groups/assets/129281605/63168035-e10f-4622-ab14-370cd0e6338e">
</p>
<p>
Login to your Azure account and create resources - you will need to create a Resource Group near your location (for example: US West 3). Create two Virtual Machines (VM-1: Windows 10; VM-2: Ubuntu Server) and select the Resouce Group that was created earlier for each of these to ensure they share the same permissions, policies, and network. Allow the first VM to create a new Vnet and Subnet. While creating the second VM, select the previously created Resource Group and Vnet.
</p>
<br />

<p>
<img width="1762" alt="Screenshot 2023-08-06 at 6 54 54 PM" src="https://github.com/gregjames1/Network-Security-Groups/assets/129281605/dcd7e70c-af1e-4c9d-b5bc-500502cd8a56">
</p>
<p>
Login to VM-1 using Remote Desktop using the credentials set up while creating the VM and install WireShark. Follow the installation steps and open the program once finished. Run PowerShell as an Administrator and ping VM-2 using its private IP Address. Filter for ICMP traffic in WireShark and observe the network traffic - requests from VM-1 (source IP) and replies from VM-2 (destination IP).
</p>
<br />

<p>
<img width="1496" alt="Screenshot 2023-08-07 at 11 43 39 PM" src="https://github.com/gregjames1/Network-Security-Groups/assets/129281605/6429e167-2624-4f9f-8719-dd9fbb82e767">
</p>
<p>
Return to the Azure portal, navigate to Network Security Groups, and select VM-2 (Ubuntu Server). Select inbound security rules from the left menu, choose add, and select the ICMP protocol, deny the action, enter a priority higher than 300 (to ensure that the new rule is evaluated prior to the other existing rules), and click the add button.
</p>
<br />

<p>
<img width="1822" alt="Screenshot 2023-08-06 at 7 09 53 PM" src="https://github.com/gregjames1/Network-Security-Groups/assets/129281605/a0e20410-db42-4be0-b28d-aec7f6efd08c">
</p>
<p>
Return to the remote Windows session and observe that the ping requests begin to timeout as the new security rule takes effect. View the traffic in WireShark and notice that the requests begin to go unanswered due to the new rule. Stop the ping requests in VM-1 and delete the rule created in the previous step or alter the rule to allow ICMP traffic.
</p>
<br />

<p>
<img width="1860" alt="Screenshot 2023-08-06 at 7 19 38 PM" src="https://github.com/gregjames1/Network-Security-Groups/assets/129281605/6c1d85e6-4c74-4dcc-abf0-9a1265368ecb">
</p>
<p>
Return to WireShark and filter for SSH traffic. In PowerShell, SSH into VM-2 using the private IP address and the credentials set up when creating the server. Observe the traffic in WireShark as you connect to the server using this protocol.
</p>
<br />

<p>
<img width="2268" alt="Screenshot 2023-08-06 at 7 47 36 PM" src="https://github.com/gregjames1/Network-Security-Groups/assets/129281605/829be2f6-ed11-460f-8eb2-f6d850ad00c6">
</p>
<p>
Exit the SSH session, close PowerShell, and open Command Prompt as an administrator. Filter for DHCP traffic in WireShark. Enter "ipconfig /renew" in Command Prompt to request a new IP address to be assigned to VM-1 and observe the traffic in WireShark. Although in the above image, an error was encountered while requesting an new IP address, we are still able to observe the network activity in WireShark.
</p>
<br />

<p>
<img width="2067" alt="Screenshot 2023-08-06 at 7 51 48 PM" src="https://github.com/gregjames1/Network-Security-Groups/assets/129281605/cf53319f-e032-49f8-8ba7-42e5c0a8d6b5">
</p>
<p>
Filter for DNS traffic in WireShark. In Command Prompt, enter "nslookup www.netflix.com" and observe the traffic in WireShark.
</p>
<br />
