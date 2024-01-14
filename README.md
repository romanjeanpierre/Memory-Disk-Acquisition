<h1> Infected Workstation: Memory Dump & Disk Imaging Collection </h1>


<h2>Brief Description</h2>
This project focuses on digital data acquisition through the utilization of industry-standard tools. The primary objective involves leveraging FTK Imager and Sysinternals for disk imaging and memory dump processes, alongside the deployment of KAPE to extract crucial artifacts on a remote workstation. 

<h2>Pre-Project Kickoff: Critical Data Integrity Methodologies </h2>

<h3> <b> a) </b> Order of Volatility</h3>
The Order of Volatility in digital forensics emphasizes the importance and prioritization of data sources during evidence collection.

1. Registers & Cache: Highly volatile; data in CPU cache and registers changes rapidly. Immediate retrieval is essential.

2. Memory (RAM): Fast, temporary storage; contains valuable data about running processes and network connections. Susceptible to loss during power spikes or disconnection.

3. Disk (HDD and SSD): Once overwritten, data is irrecoverable; SSDs have additional risks. Disk space is non-volatile when the system is offline.

4. Remote Logging and Monitoring Data: Higher volatility than hard drives, but less vital. Priority is still given to hard drive data.

5. Physical Configuration, Network Topology, Archival Media: Less vital or non-volatile. Physical and network information aids investigations, while archived data is often on separate devices.

<h3> <b> b) </b> Chain of Custody </h3>

The Chain of Custody is pivotal in computer forensics, ensuring evidence integrity by documenting handling details from collection to court. It prevents unauthorized alterations and guarantees the original state. Vital for court acceptance, it offers insight into evidence handling, protecting its integrity universally in criminal investigations. The process involves hashing for integrity, using hardware blockers for physical evidence, creating forensic copies for analysis, and storing them in secure containers. A Chain of Custody form, filled by examiners, ensures seamless handling and communication.

<h2>Overview</h2>
<p align="center">
<img src="https://imgur.com/guy3Nys.png" height="80%" width="80%">

<h2>Languages and Utilities Used</h2>

- <b>PowerShell</b>
- <b>FTK Imager</b>
- <b>ProcDump - sysinternals</b>
- <b>KAPE</b>

<h2>Project walk-through:</h2>
Collecting Memory Dump: FTK Imager
<br/>
<br/>
Open FTK Imager: Go to File > Capture Memory > Select Destination Path > Capture Memory
<br/>
<br/>
<img src="https://imgur.com/guy3Nys.png" height="80%" width="80%"/>
<br />
<br />
Collecting Memory Dump: ProcDump (Sysinternals) to retrieve memory image of specific process <br/>
<br/>
Change the Directory to where the procdump.exe file resides, use calculator application for example
<br/>
<br/>
<img src="https://imgur.com/Dj1GCrN.png" height="80%" width="80%"/>
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
