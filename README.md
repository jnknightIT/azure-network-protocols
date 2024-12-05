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

- Create VMs and Install Wireshark
- Observe ICMP Traffic
- Observe SSH Traffic
- Observe RDP Traffic

<h2>Actions and Observations</h2>

<p>
<img src="https://i.imgur.com/8UEz44P.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
  
</p>
<p>
Set up two virtual machines within Microsoft Azure. One will use Windows 10 OS  and the other will use Ubuntu connect them to the same virtural network.
</p>
<br />

<p>
<img src="https://i.imgur.com/zThBmd7.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
use RDC to connect to the Windows 10 vm once logged in download Wireshark.
</p>
<br />

<p>
<img src="https://i.imgur.com/WLxvqvN.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
  <img src="https://i.imgur.com/OntWOyw.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
open Wireshark highlight the network in the middle of the application and click the blue shark fin in the top left you should now see the network traffic on the VM.


</p>
<br />

<p>
<img src="https://i.imgur.com/NtaexLL.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
  <img src="https://i.imgur.com/7VcSpKs.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
   <img src="https://i.imgur.com/jzoTxDm.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>in Wireshark filter for ICMP traffic. Get the private IP address of the Lenux VM and ping it within the Windows vm.
  on Azure portal go to the Lenux vm -> Network Settings -> inbound security rules (add a new rule and deny all ICMPv4 request).
  ping the private IP again and the request should timeout. (you can delete the rule afterwords if you want.)
</p>
<br />

<p>
<img src="https://i.imgur.com/Pq6NQH5.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>

</p>
<p>
from the Windows VM ssh into the Linux VM. Open PowerShell, and type: (ssh VMUSERNAME@LINUX private IP address). once logged in you should be able to see the traffic between the machines in Wireshark. ssh traffic is encripted so you cant see the data!
You can drop the connection by typing "exit" in powershell.
</p>
<br />

<p>
<img src="https://i.imgur.com/n9t7Q7a.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>

</p>
<p>
In Wireshark, filter DHCP traffic by typing in "DHCP" in the search bar and press enter. Continue without saving. In Powershell, use command "nslookup" followed by a space and any website of your choice. Observe all the traffic created.
</p>
<br />

<p>
<img src="https://i.imgur.com/CX5Qxzg.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>

</p>
<p>
to see the Remote Desktop Protocol (RDP) you will type "tcp.port==3389" into Wireshark. This will display the real-time traffic that occurs between both computers.
</p>
<br />


