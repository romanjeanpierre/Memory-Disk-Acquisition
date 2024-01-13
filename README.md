<h1> Infected Workstation: Memory Dump & Disk Imaging Collection </h1>


<h2>Brief Description</h2>
This project involves the implementation of a vulnerable virtual machine configured to allow unrestricted inbound and outbound traffic without constraints on the Firewall. A Powershell script is then used to continuously extract security event ID 4625 (indicating failed log-on attempts) from the Windows Event Viewer. Additionally, the script captures API requests to "IP geolocation", translating source IP addresses into Longitude and Latitude data. This data is then ingested into Microsoft Sentinel to be mapped out for visualization. 

<h2>Project Objective</h2>
Illustrate the rapid exploitation of misconfigured workstations on the web, showcasing the risks to organizational security posed by global brute-force attacks.

<h2>Overview</h2>
<p align="center">
<img src="https://i.imgur.com/y3Aqek1.png" height="80%" width="80%">

<h2>Languages and Utilities Used</h2>

- <b>PowerShell</b>
- <b>Kusto Query Language (KQL)</b>
- <b>Windows 10</b>
- <b>Microsoft Azure</b>
- <b>Log Analytics Workspace<b>
- <b>Azure Sentinel (SIEM)<b>

<h2>Project walk-through:</h2>
Step 1: Deploy Virtual Machine
<br/>
<br/>
Instance Details:
<br/>
<br/>
<img src="https://i.imgur.com/F8fdKPW.png" height="80%" width="80%"/>
<br />
<br />
Networking Details: <br/>
<br/>
<img src="https://i.imgur.com/oGd6m6h.png" height="80%" width="80%"/>
<br />
<br />
Misconfigure the VM to allow RDP traffic, create a new NIC network security group, remove existing inbound rules, and add a new inbound rule allowing any protocol
<br />
<br />
<br />
Step 2: Config Environment
<br/>
<br/> Microsoft Defender: 
<br/>
<br/>
<img src="https://i.imgur.com/OnKGVRq.png" height="80%" width="80%" />
<br/>
<br/>
Log Analytics Workspace:  
<br/>
<br/>
<img src="https://i.imgur.com/YP977ZY.png" height="80%" width="80%" />
<br />
<br />
Disable Firewall in VM: 
<br/>
<br/>
<img src="https://i.imgur.com/GyhISce.png" height="80%" width="80%" />
<br />
<br />
Use Host Machine to verify if ICMP packets are reachable using 'ping -t <VM IP address>'.
<br />
<br />
<br />
Step 3: Script Execution 
<br />
<br />
Powershell: 
<br/> 
<br/>
<img src="https://i.imgur.com/D7thSgi.png" height="80%" width="80%" /> 
<br/> 
<br/>
The Powershell script detects failed RDP logins in Windows Security Events, ingesting logs into Log Analytics workspaces, and enriching output with geographical data.
<br />
<br /> 
<br /> 
Step 4: Extract Fields from Custom Log File 
<br/>
<br/>
Run Query:<br/>
<br/>
<img src="https://i.imgur.com/ZD0hxYm.png" height="80%" width="80%"/>
<br />
<br /> 
Results of Failed RDP after 24 Hours:
<br/>
<br/> 
<img src="https://i.imgur.com/qUX0dqS.png" height="80%" width="80%" />
<br />
<br />
<!--
 ```diff
- text in red
+ text in green
! text in orange
# text in gray
@@ text in purple (and bold)@@
```
--!>
