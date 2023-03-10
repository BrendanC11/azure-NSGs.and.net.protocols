<p align="center">
<img src="https://i.imgur.com/Ua7udoS.png" alt="Traffic Examination"/>
</p>

<h1>Network Security Groups (NSGs) and Inspecting Traffic Between Azure Virtual Machines</h1>
This lab aims to aid in our understanding of different types of web protocols and how machines interact with each other over a network. We will observe three different types of traffic in this lab being; ICMP, DHCP, and DNS. <br />

<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines)
- Remote Desktop Connection
- Various Command-Line Tools
- Various Network Protocols (DNS, DHCP, ICMP)
- Wireshark (Protocol Analyzer)

<h2>Operating Systems Used </h2>

- Windows 10
- Ubuntu Server 20.04

<h2>High-Level Steps</h2>

- Create a Resource Group. 
- Create two Virtual Machines. 
- Remote Desktop into the windows virtual machine. 
- Download and install Wireshark. 
- “Ping” to observe ICMP traffic.
- Modify incoming security rules for the Linux VM
- “Ipconfig /renew” to Observe DHCP traffic
- “nslookup” to Observe DNS Traffic
- Clean-up Azure

<h2>Actions and Observations</h2>

<b>1. Create a Resource Group.</b>
  
<p>
This is where we will store our two virtual machines. Go to “Azure -> resource groups -> create”
</p>

<p>
<img src="https://i.imgur.com/C7TmwAn.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
  
<br />

<b>2.	Create two Virtual Machines.</b>
  
<p>
One should be a windows 10 Virtual Machine, the other should be a Linux virtual machine. When creating these VMs, place them both inside the resource group that we just created. 

The first VM will be called “Windows-VM” and will run “Windows 10 Pro.” Username will be “Labuser” and the password will be “Password1234”
</p>

<p>
<img src="https://i.imgur.com/uv3viED.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
  
<br />

<p>
The second VM will be called “Linux-VM” and will run “Ubuntu Server 20.04 LTS.” Username will be “Labuser” and the password will be “Password1234” The reason we can use the same username and password on both virtual machines is because they are two separate machines, thus having their own unique IP Address when we connect to them.
</p>

<p>
<img src="https://i.imgur.com/FyKrVLk.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>

<br />

<p>
Note: when we crated our first virtual machine, being “Windows-VM” a virtual network was automatically created called “Windows-VM-Net”. With this in mind, when we crate the second virtual machine we must go to the networking page and check that the virtual network that was created is selected. 
</p>

<p>
<img src="https://i.imgur.com/vbNeczg.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
  
<br />

<p>
<b>3.	Remote Desktop into the windows virtual machine.</b>
  
Within Azure, navigate to your windows virtual machine and copy Its public IP address. Open Remote Desktop Connection on your PC and paste the IP address of the windows VM. Log in to the VM using the username and password that we crated when initially creating the VM.
</p>

<p>
<img src="https://i.imgur.com/E4C7FDQ.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
  
<br />

<p>
<b>4.	Download and install Wireshark. </b>
  
Once you are inside your Windows VM, open a web browser and download the Windows 10 64bit Wireshark installer. Install the software from the file in your downloads folder. Once Wireshark is installed, open the program. Once inside Wireshark, select “Ethernet” and then press the blue shark fin button in the top left of Wireshark. 
</p>

<p>
<img src="https://i.imgur.com/S4f1Um7.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
  
<br />

<p>
We will use Wireshark to observe ICMP, DHCP, and DNS traffic.

We will now filter for ICMP traffic only. To do this, go to the search bar at the top of Wireshark and search for “ICMP” then press enter. This will make it so that Wireshark only shows us ICMP traffic that is happening over the network, as opposed to all traffic.
</p>

<p>
<img src="https://i.imgur.com/LDrCUDX.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
  
<br />

<p>
It is important to remember that ICMP stands for “Internet Control Messaging Protocol” which is the protocol that ping uses. When we begin pinging another machine, we will see the ICMP traffic in Wireshark.
</p>
  
<br />

<p>
<b>5.	“Ping” to observe ICMP traffic.</b>
  
Obtain the private IP address of the linux virtual machine within azure. For this example, the private IP address of the linux virtual machine is “10.0.0.5”.
</p>

<p>
<img src="https://i.imgur.com/VM2nyzQ.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>

<br />
