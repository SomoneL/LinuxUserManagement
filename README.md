# Using Linux to Automate User Management and Access Controls

<h2>Description</h2>
This project focuses on automating user account management and implementing access controls to streamline and secure the onboarding/offboarding processes. Automating user management is a valuable skill in system administration, as it ensures consistent security practices and reduces manual work. Below is a step-by-step guide for implementation.
<br />


<h2>Step 1: Download and Install VirtualBox and CentOS to add to your VM </h2>
<ol>
  <li>Go to the VirtualBox Website</li>
   <ul><li>Navigate to the VirtualBox Downloads Page.</li></ul>
   <ul><li>Choose the version that matches your host operating system (Windows, macOS, or Linux).</li></ul>
 
  <li>Download and Install VirtualBox</li>
   <ul><li>Click the link to download the VirtualBox installer for your operating system.</li></ul>
   <ul><li>Open the downloaded installer and follow the prompts to install VirtualBox.</li></ul>
   <ul><li>Leave the default options selected unless you require custom settings.</li></ul>
   
 <li>Go to the CentOS Website</li>
   <ul><li>To host my Linux server, I will be using the CentOS operating system.</li></ul>
   <ul><li>Navigate to the CentOS Download Page.</li></ul>
   <ul><li>Choose the version that matches your host operating system (Windows, macOS, or Linux).</li></ul>
</ol> 
 


<h2>Step 2: Prepare Your Environment </h2>
<ol>
  <li>Configure your VM Settings and Mount your Linux OS</li>
   <ul><li>Allocate at least 2 CPUs, 4GB RAM, and 20GB storage for the VM.</li></ul>
   <ul><li>Choose the version that matches your host operating system (Windows, macOS, or Linux).</li></ul>
 
  <li>Install Essential Tools:</li>
   <ul><li>Once your VM has finished setting up, you will want to prepare it for use.</li></ul>
   <ul><li>You will want to update and upgrade packages by running the following bash script: 
<br/>
<img src="https://i.imgur.com/xLBPzXn.png" height="40%" width="40%" alt="script"/>
<br/></li></ul>
   
   <ul><li>You will want to install tools for user and system management by running the following bash script:
   
<br/>
<img src="https://i.imgur.com/eVUHNRy.png" height="40%" width="40%" alt="script"/>
<br/></li></ul>
   
</ol> 



<h2>Program walk-through:</h2>

<p align="center">
Launch the utility: <br/>
<img src="https://i.imgur.com/62TgaWL.png" height="80%" width="80%" alt="bash script"/>
<br />
<br />
Select the disk:  <br/>
<img src="https://i.imgur.com/tcTyMUE.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Enter the number of passes: <br/>
<img src="https://i.imgur.com/nCIbXbg.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Confirm your selection:  <br/>
<img src="https://i.imgur.com/cdFHBiU.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Wait for process to complete (may take some time):  <br/>
<img src="https://i.imgur.com/JL945Ga.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Sanitization complete:  <br/>
<img src="https://i.imgur.com/K71yaM2.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Observe the wiped disk:  <br/>
<img src="https://i.imgur.com/AeZkvFQ.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>

<!--
 ```diff
- text in red
+ text in green
! text in orange
# text in gray
@@ text in purple (and bold)@@
```
--!>
