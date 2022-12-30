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

- Create Resoure Group
- Create Windows 10 and Linux (Ubuntu) VMs
- Connect to Microsoft Remote Desktop
- Download Wireshark 
- Observe Traffic for ICMP, SSH, DHCP, DNS, RDP

<h2>Actions and Observations</h2>

<p>
<img src="https://i.imgur.com/qrHcjFE.png" height="80%" width="80%" alt="VMs"/>
</p>
<p>
The first step is to create two virtual machines inside the Azure portal. One Virtual Machine will be using Windows 10 (21H2). The other will be using Linux (Ubuntu). Each machine will be assigned a private IP address. These addresses will be used to test the connection to the other.
</p>
<br />

<p>
<img src="https://i.imgur.com/691xq2x.png" height="80%" width="80%" alt="IMCP"/>
</p>
<p>
Next, you must download Wireshark onto the the windows 10 VM.When the step is complete, open Wireshark and filter for ICMP traffic only. Retrieve the private IP address of the Ubuntu VM and attempt to ping it from within the Windows 10 VM. If the ping is successful, traffic starts to show up in the protocal analyzer. No packets lost during this process which mean it was 100% successful.
</p>
<br />

<p>
<img src="https://i.imgur.com/2PBiFGh.png" height="80%" width="80%" alt="SSH"/>
<img src="https://i.imgur.com/vCr07c9.png" height="80%" width="80%" alt="SSH2"/>
</p>
<p>
Next, filter Wireshark for SSH traffic only. SSH will allow the user to connect to VM2 Linux through the terminal using "ssh <Username>@<Private IP>". Once the connection is attained, the terminal will prompt you to enter the password for the account. When typing, the password will not show up. That is intentional and serves as a security mechanism. After entering the password, you will be inside the Linux machine. From there, you can look up files, create files, and make edits. It will start to filter a lot of traffic due to the activity of the ssh. 
</p>
<br />

<p>
<img src="https://i.imgur.com/AluFKeZ.png" height="80%" width="80%" alt="DHCP"/>
</p>
<p>
Finally, you will filter Wireshark for DHCP. DHCP checks for newly assigned IP addresses. First, open the terminal, then you will type " ipconfig /renew ". That will assign a new IP address to the current computer. After being entered, you will see brief activity showing up in the network analyzer. 
</p>
<br />
