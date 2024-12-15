# Using Linux to Automate User Management and Access Controls
<h2>Description</h2>

This guide provides a practical approach to managing users, groups, and directory permissions in Linux. It focuses on creating directory structures and user groups aligned with organizational teams like Development, Operations, and Analytics. Using tools such as chown and chmod, administrators can assign appropriate permissions, ensuring only authorized users have access.

The guide includes examples of creating users (e.g., Jess Waller for Development, Blake Dorsey for Operations, and Joey Ewart for Analytics) and configuring permissions to restrict access strictly to their assigned directories, preventing unauthorized access.
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
      <li>Navigate to the CentOS Download Page: https://www.centos.org/download/</li>
   </ul>
   <ul>
      <li>Choose the version that matches your host operating system (Windows, macOS, or Linux).</li>
   </ul>
   
   <li>Configure your VM Settings and Mount your Linux OS</li>
   <ul>
      <li>Allocate at least 2 CPUs, 4GB RAM, and 20GB storage for the VM.</li>
   </ul>
   <ul>
      <li>Choose the version that matches your host operating system (Windows, macOS, or Linux).</li>
   </ul>
    <br><img src="https://imgur.com/yTznV63.png" height="40%" width="40%" alt="script"/>
    <br/>
</ol>
<h2>Step 2: Directory Creation and Group Management </h2>
<ol>
   <li>Sign in as the root user to make the appropriate changes.</li>
   <ul>
      <li>If you're not already the root user, switch by running: 'sudo su'</li>
   </ul>
   <br/>
   <img src="https://imgur.com/VxKIU5j.png" height="40%" width="40%" alt="script"/>
   <br/>
   <li>Create 3 directories: Engineering, Operations, Analytics</li>
   <img src="https://imgur.com/lDg1CTi.png" height="40%" width="40%" alt="script"/>
   <br/>
   <li>Create several blank dummy files in each directory:</li>
   <img src="https://imgur.com/4TM5d0s.png" height="40%" width="40%" alt="script" "/>
   <br/>
   <li>Using the command 'cd' to enter each created directory and 'ls' to view your created files.</li>
  <ul> <li>Explanation- cd means: change directory, ls means: list files, touch means: create new files </li></ul>
   <img src="https://imgur.com/OctSqJH.png" height="40%" width="40%" alt="script" "/>
   <br/>
   <img src="https://imgur.com/Kb3ZvFA.png" height="40%" width="40%" alt="script" "/>
   <br/>
   <img src="https://imgur.com/SNiJSiJ.png" height="40%" width="40%" alt="script" "/>
   <br/>
  </ul>
  <li>Create 3 groups: Engineering, Operations, Analytics</li>
   <img src="https://imgur.com/7W7QiVt.png" height="40%" width="40%" alt="script" "/> <br/>
   <ul> <li>Run the following command 'cat /etc/group' to view a list of all the created groups. </li></ul>
   <img src="https://imgur.com/at8JCC2.png" height="40%" width="40%" alt="script" "/> <br/>
   <li>Assign the respective group to each directory using the 'chown' command:</li>
   <ul> <li>Run the following commands: 'sudo chown root:Engineers Engineering', 'sudo chown root:Operations Operations', 'sudo chown root:DataAnalysts Analytics'. Then, run the command 'll'(displays a long list of file info) to list all the file permissions. </li></ul>
   <img src="https://imgur.com/BxLxwMl.png" height="40%" width="40%" alt="script" "/> <br/>
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
   <h2>Step 7: Conclusion</h2>
 In this project, I developed an automated user management solution for Linux, covering onboarding, access control, and offboarding. I created a Bash script to automate account creation with secure default settings, restricted SSH access based on roles, and implemented group-based access controls. The project also includes login monitoring for proactive security and regular user access reviews, ensuring that only authorized users have access. This demonstrates my skills in Linux administration, automation, and security, showcasing essential competencies for a System Administrator role.     
</ol>
