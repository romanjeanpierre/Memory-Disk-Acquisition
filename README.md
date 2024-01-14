<h1>Infected Workstation: Memory Dump & Disk Imaging Collection</h1>

<h2>Brief Description</h2>
<p>This project focuses on digital data acquisition through the utilization of industry-standard tools. The primary objective involves leveraging FTK Imager and Sysinternals for disk imaging and memory dump processes, alongside the deployment of KAPE to extract crucial artifacts on a remote workstation.</p>

<h2>Pre-Project Kickoff: Critical Data Integrity Methodologies</h2>

<h3><b>a)</b> Order of Volatility</h3>
<p>The Order of Volatility in digital forensics emphasizes the importance and prioritization of data sources during evidence collection.</p>
<ol>
    <li>Registers & Cache: Highly volatile; data in CPU cache and registers changes rapidly. Immediate retrieval is essential.</li>
    <li>Memory (RAM): Fast, temporary storage; contains valuable data about running processes and network connections. Susceptible to loss during power spikes or disconnection.</li>
    <li>Disk (HDD and SSD): Once overwritten, data is irrecoverable; SSDs have additional risks. Disk space is non-volatile when the system is offline.</li>
    <li>Remote Logging and Monitoring Data: Higher volatility than hard drives, but less vital. Priority is still given to hard drive data.</li>
    <li>Physical Configuration, Network Topology, Archival Media: Less vital or non-volatile. Physical and network information aids investigations, while archived data is often on separate devices.</li>
</ol>

<h3><b>b)</b> Chain of Custody</h3>
<p>The Chain of Custody is pivotal in computer forensics, ensuring evidence integrity by documenting handling details from collection to court...</p>

<h2>Overview</h2>
<p align="center">
    <img src="https://imgur.com/guy3Nys.png" height="80%" width="80%" alt="Project Overview Image">
</p>

<h2>Languages and Utilities Used</h2>
<ul>
    <li><b>PowerShell</b></li>
    <li><b>FTK Imager</b></li>
    <li><b>ProcDump - sysinternals</b></li>
    <li><b>KAPE</b></li>
</ul>

<h2>Project Walk-Through:</h2>
<h3>Collecting Memory Dump using FTK Imager</h3>
<br/>
<p>Open FTK Imager: Go to File > Capture Memory > Select Destination Path > Capture Memory</p>
<br/>
<img src="https://imgur.com/guy3Nys.png" height="80%" width="80%" alt="FTK Imager Memory Capture">
<br/>
<br/>
<h3>Collecting Memory Dump: ProcDump (Sysinternals) to retrieve memory image of a specific process</h3>
<br/>
<p>Change the Directory to where the procdump.exe file resides, use the calculator application as an example</p>
<br/>
<img src="https://imgur.com/Dj1GCrN.png" height="80%" width="80%" alt="ProcDump Directory Change">
<br/>
<br/>
<p>Get Process ID (PID) for the calculator application</p>
<br/>
<p>Shell command: <code>Get-Process | findstr -I calc</code></p>
<br/>
<p>Results Output: PID = 4420</p>
<br/>
<img src="https://imgur.com/ABxLoZm.png" height="80%" width="80%" alt="PID Results Output">
<br/>
<br/>
<p>After retrieving PID, use ProcDump to create a full memory dump of this process using:</p>
<br/>
<p>Command: <code>.\procdump.exe -ma 4420</code></p>
<br/>
<img src="https://imgur.com/K1zVv80.png" height="80%" width="80%" alt="ProcDump Memory Dump">
<br/>
<br/>
<p>In an incident response engagement, we can use these utilities to capture the image of Malware running on a system.
<br/>
<br/>
<h3>Collecting Disk Image using FTK Imager</h3>
<br/>
<p>Open FTK Imager: Go to File > Create Disk Image > Select Source from Physical Drive</p>
<br/>
<img src="https://imgur.com/liZWHGq.png" height="80%" width="80%" alt="FTK Imager Disk Image Creation">
<br/>
<br/>
<p>Select a Drive input</p>
<br/>
<br/>
<img src="https://imgur.com/Zxb4QuC.png" height="80%" width="80%" alt="Drive Input Selection">
<br/>
<br/>
<p>Create Image - Select the output destination for the file. Click Add and change the format type to a .E01 file. This filetype is used by analysis tools, such as the enterprise-grade forensics triage software EnCase.</p>
<br/>
<img src="https://imgur.com/MVLtw1f.png" height="80%" width="80%" alt="FTK Imager Disk Image Output">
<br/>
<br/>
<p>Select Output location and filename:</p>
<br/>
<img src="https://imgur.com/7o9Ijn0.png" height="80%" width="80%" alt="Output Location and Filename">
<br/>
<img src="https://imgur.com/eywXn2y.png" height="80%" width="80%" alt="Output Location and Filename 2">
<br/>
<p>Once the disk image is complete, FTK Imager will provide us with hash values for integrity purposes.</p>
<!-- Add additional content as needed -->

</body>
</html>
<p>So we can ensure that the disk image or any copies are the exact same as when it was acquired. This allows us to prove or disprove claims of data corruption or tampering.</p>
<br/>
<img src="https://imgur.com/yXysp7b.png" height="80%" width="80%" alt="FTK Imager Disk Image Hash Values">
<br/>
<br/>

<!-- Add additional sections or content as needed -->

<h2>Conclusion</h2>
<p>In conclusion, the use of industry-standard tools such as FTK Imager, Sysinternals, and KAPE facilitates efficient and effective digital data acquisition for forensic purposes. The adherence to critical data integrity methodologies, including the Order of Volatility and Chain of Custody, ensures the reliability and admissibility of the acquired evidence in legal proceedings.</p>

<p>This project walkthrough provides a comprehensive guide to collecting memory dumps and disk images, crucial steps in investigating and responding to incidents involving potentially compromised workstations.</p>

<h2>References</h2>
<ul>
    <li>Reference 1: Insert your reference here</li>
    <li>Reference 2: Insert your reference here</li>
    <!-- Add more references as needed -->
</ul>

</body>
</html>
