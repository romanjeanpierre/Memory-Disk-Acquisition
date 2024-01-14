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
Collecting Memory Dump using FTK Imager
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
Get Process ID (PID) for calculator application
<br/>
<br/>
Shell command => Get-Process | findstr -I calc
<br/>
<br/>
Results Output: PID = 4420
<br/>
<br/>
<img src="https://imgur.com/ABxLoZm.png" height="80%" width="80%" />
<br/>
After retrieving PID we can now use ProcDump to create a full memory dump of this process using 
<br/>
<br/>
Command => .\procdump.exe -ma 4420
<br/>
<br/>
<img src="https://imgur.com/K1zVv80.png" height="80%" width="80%" />
<br />
In an incident response engagement, we can use these utilities to capture the image of Malware running on a system. 
Disable Firewall in VM: 
<br/>
<br/>
<br />
Collecting Disk Image using FTK Imager 
<br />
<br />
Open FTK Imager: Go to File > Create Disk Image > Select Source from Physical Drive
<br/> 
<br/>
<img src="https://imgur.com/liZWHGq.png" height="80%" width="80%" /> 
<br/> 
<br/>
Select a Drive input 
<br />
<br /> 
<img src="https://imgur.com/Zxb4QuC.png" height="80%" width="80%"/>
<br/>
<br/>
Create Image - Select the output destination for the file. Click Add and change the format type to a .E01 file. This filetype is used by analysis tools, such as the enterprise-grade forensics triage software EnCase.
<br/>
<img src="https://imgur.com/MVLtw1f.png" height="80%" width="80%"/>
<br />
<br /> 
Select Output location and filename:
<br/>
<br/> 
<img src="https://imgur.com/7o9Ijn0.png" height="80%" width="80%" />
<br />
<img src="https://imgur.com/eywXn2y.png" height="80%" width="80%" />
<br />
Once the disk image is complete, FTK Imager will provide us with hash values for integrity purposes, so in the future we can ensure that the disk image, or any copies, are the exact same as when it was acquired. This allows us to prove or disprove claims of data corruption or tampering.
<br/>
<img src="https://imgur.com/yXysp7b.png" height="80%" width="80%"/>
<br/>
<br/>

<!--
 ```diff
- text in red
+ text in green
! text in orange
# text in gray
@@ text in purple (and bold)@@
```
--!>
