# Using Linux to Automate User Management and Access Controls
<h2>Description</h2>
This project focuses on automating user account management and implementing access controls to streamline and secure the onboarding/offboarding processes. Automating user management is a valuable skill in system administration, as it ensures consistent security practices and reduces manual work. Below is a step-by-step guide for implementation.
<br />
<h2>Step 1: Download and Install VirtualBox and CentOS to add to your VM </h2>
<ol>
   <li>Go to the VirtualBox Website</li>
   <ul>
      <li>Navigate to the VirtualBox Downloads Page.</li>
   </ul>
   <ul>
      <li>Choose the version that matches your host operating system (Windows, macOS, or Linux).</li>
   </ul>
   <li>Download and Install VirtualBox</li>
   <ul>
      <li>Click the link to download the VirtualBox installer for your operating system.</li>
   </ul>
   <ul>
      <li>Open the downloaded installer and follow the prompts to install VirtualBox.</li>
   </ul>
   <ul>
      <li>Leave the default options selected unless you require custom settings.</li>
   </ul>
   <li>Go to the CentOS Website</li>
   <ul>
      <li>To host my Linux server, I will be using the CentOS operating system.</li>
   </ul>
   <ul>
      <li>Navigate to the CentOS Download Page.</li>
   </ul>
   <ul>
      <li>Choose the version that matches your host operating system (Windows, macOS, or Linux).</li>
   </ul>
</ol>
<h2>Step 2: Prepare Your Environment </h2>
<ol>
   <li>Configure your VM Settings and Mount your Linux OS</li>
   <ul>
      <li>Allocate at least 2 CPUs, 4GB RAM, and 20GB storage for the VM.</li>
   </ul>
   <ul>
      <li>Choose the version that matches your host operating system (Windows, macOS, or Linux).</li>
   </ul>
   <li>Install Essential Tools:</li>
   <ul>
      <li>Once your VM has finished setting up, you will want to prepare it for use.</li>
   </ul>
   <ul>
      <li>You will want to update and upgrade packages by running the following bash script: 
         <br/>
         <img src="https://i.imgur.com/xLBPzXn.png" height="40%" width="40%" alt="script"/>
         <br/>
      </li>
   </ul>
   <ul>
      <li>You will want to install tools for user and system management by running the following bash script:
         <br/>
         <img src="https://i.imgur.com/eVUHNRy.png" height="40%" width="40%" alt="script"/>
         <br/>
      </li>
   </ul>
</ol>
<h2>Step 3: Automate User Account Creation </h2>
<ol>
   <li>Write a Bash Script</li>
   <ul>
      <li>Create a script to automate adding users and assigning them to groups. The script name we will be using is (user_management.sh):.</li>
   </ul>
   <br/>
   <img src="https://i.imgur.com/7V1Ieb7.png" height="40%" width="40%" alt="script"/>
   <br/>
   <li>Make the Script Executable:</li>
   <img src="https://i.imgur.com/HsDzzg6.png" height="40%" width="40%" alt="script"/>
   <br/>
   <li>Run the Script:</li>
   <img src="https://i.imgur.com/y0pv2di.png" height="40%" width="40%" alt="script" "/>
   <br/>
   </li></ul>
</ol>
<h2>Step 4: Implement Access Control Policies </h2>
<ol>
   <li>Define User Roles: Assign specific roles to users based on their function in the lab.</li>
   <ul>
      <li>Administrators: Full access to all VMs, Active Directory management, and Splunk configurations.</li>
   </ul>
   <ul>
      <li>Standard Users: Limited access to specific Windows or Linux machines for testing and learning purposes.</li>
   </ul>
   <ul>
      <li>Guests: Minimal access, primarily for observing system activity without making changes.</li>
   </ul>
   <ul>
      <br></br>
      <li>Create groups for specific roles (e.g., admin, user, guest) by running the following code:</li>
   </ul>
   <img src="https://i.imgur.com/RXI5kjZ.png" height="30%" width="30%" alt="script"/>
   <br/>
   <li>Assign Permissions to Groups</li>
   </ul>
   <ul>
      <li>Use the chmod and chown commands to set directory permissions.</li>
   </ul>
   <img src="https://i.imgur.com/9c335UK.png" height="30%" width="30%" alt="script"/>
   <li>Enforce Access Control</li>
   <ul>
      <li>Verify permissions by switching to different users and testing to see if you can access the created directories.</li>
   </ul>
   <img src="https://i.imgur.com/pY3M8ON.png" height="30%" width="30%" alt="script"/>
</ol>
<h2>Step 5: Automate Password Policies </h2>
<ol>
   <li>Password Policy: Configure strong password requirements on all systems</li>
   <ul>
      <li>Minimum length: 12 characters.</li>
   </ul>
   <ul>
      <li>Must include uppercase, lowercase, numbers, and special characters.</li>
   </ul>
   <ul>
      <li>Prevent the reuse of the last five passwords.</li>
   </ul>
   <ul>
      <li>Implement password expiration policies: Set passwords to expire every 60 days on all machines (via Group Policy for Windows and /etc/login.defs for Linux).</li>
   </ul>
   <li>Password Requirements</li>
   <ul>
      <li>Modify /etc/login.defs for system-wide policies by running the following:</li>
      <img src="https://i.imgur.com/u0ywtmF.png" height="40%" width="40%" alt="script"/>
      <br/>
   </ul>
   <ul>
      <li>Set these parameters:
         <br/>
      </li>
      <ul>
         <li>PASS_MAX_DAYS: Sets the maximum number of days a user can use their current password before being required to change it.</li>
      </ul>
      <ul>
         <li>PASS_MIN_DAYS: Defines the minimum number of days a user must wait before they can change their password again after setting it.</li>
      </ul>
      <ul>
         <li>PASS_MIN_LEN: Sets the minimum length for user passwords to 12 characters.</li>
      </ul>
      <ul>
         <li>PASS_WARN_AGE: Sends a warning to the user 7 days before their password is set to expire.</li>
      </ul>
      <img src="https://i.imgur.com/lhys6XV.png" height="25%" width="25%" alt="script"/>
   </ul>
   <li>Implement Account Lockout:</li>
   <ul>
      <li>Edit /etc/pam.d/common-auth to lock accounts after three failed login attempts by running the following:</li>
      <img src="https://i.imgur.com/mdQCxCn.png" height="25%" width="25%" alt="script"/>
      <br/>
      <ul>
         <li>Add the following line of code:</li>
         <img src="https://i.imgur.com/nsauMaI.png" height="40%" width="40%" alt="script"/>
         <br/>
         <li>auth required pam_tally2.so: Specifies the use of the pam_tally2 module, which keeps a tally of failed login attempts for user accounts.
         <li>deny = 3: Sets a limit of 3 failed login attempts before the account is locked.</li>
         <li>unlock_time=600: Configures the lockout period to 600 seconds (10 minutes). After this time, the account is automatically unlocked.</li>
         <li>onerr=fail: Ensures that if there’s an error in the PAM module, access is denied by default.</li>
         <li>audit: Enables logging of authentication attempts, including both successful and failed logins.</li>
         </li>
      </ul>
   </ul>
</ol>

<h2>Step 6: Monitor User Activity </h2>
<ol>
   <li>Enable Audit Logging</li>
   <ul>
      <li>Install auditd:</li>
   </ul>
   <br/>
   <img src="https://i.imgur.com/tBsG67J.png" height="40%" width="40%" alt="script"/>
   <br/>
   <li>Start and enable the service:</li>
   <img src="https://i.imgur.com/TWlGzOR.png" height="40%" width="40%" alt="script"/>
   <br/>
   <li>Define Audit Rules</li>
   <img src="https://i.imgur.com/y0pv2di.png" height="40%" width="40%" alt="script" "/>
   <br/>
   </li></ul>
</ol>
