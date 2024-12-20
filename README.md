# Using Linux to Automate User Management and Access Controls
<h2>Description</h2>
This guide provides a practical approach to managing users, groups, and directory permissions in Linux. It focuses on creating directory structures and user groups aligned with organizational teams like Engineering, Operations, and Analytics. Using tools such as chown and chmod, administrators can assign appropriate permissions, ensuring only authorized users have access.
The guide includes examples of creating users and configuring permissions to restrict access strictly to their assigned directories, preventing unauthorized access.
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
   <ul>
      <li>Explanation- cd means: change directory, ls means: list files, touch means: create new files </li>
   </ul>
   <img src="https://imgur.com/OctSqJH.png" height="40%" width="40%" alt="script" "/>
   <br/>
   <img src="https://imgur.com/Kb3ZvFA.png" height="40%" width="40%" alt="script" "/>
   <br/>
   <img src="https://imgur.com/SNiJSiJ.png" height="40%" width="40%" alt="script" "/>
   <br/>
   </ul>
   <li>Create 3 groups: Engineering, Operations, Analytics</li>
   <img src="https://imgur.com/7W7QiVt.png" height="40%" width="40%" alt="script" "/> <br/>
   <ul>
      <li>Run the following command 'cat /etc/group' to view a list of all the created groups. </li>
   </ul>
   <img src="https://imgur.com/at8JCC2.png" height="40%" width="40%" alt="script" "/> <br/>
   <li>Assign the respective group to each directory using the 'chown' command:</li>
   <ul>
      <li>Run the following commands: 'sudo chown root:Engineers Engineering', 'sudo chown root:Operations Operations', 'sudo chown root:DataAnalysts Analytics'. Then, run the command 'll'(displays a long list of file info) to list all the file permissions. </li>
   </ul>
   <img src="https://imgur.com/BxLxwMl.png" height="40%" width="40%" alt="script" "/> <br/>
   <li>Set permissions using chmod so only the group owner has access:</li>
   <img src="https://imgur.com/o3fHpll.png" height="40%" width="40%" alt="script" "/> <br/>
   <ul>
      <li>chmod: changes file permissions, 770 means: sets files or directory permissions so only the owner and group can read, write, and execurte while others cannot.  </li>
   </ul>
   <img src="https://imgur.com/S0l5PUS.png" height="40%" width="40%" alt="script" "/> <br/>
   <li>Create the users with their associated group and set passwords for them by running the  following commands:</li>
   <img src="https://imgur.com/GwGeTA2.png" height="40%" width="40%" alt="script" "/> <br/>

   <li>Explanation: </li>
   <ul>
    <li> -m: Creates a home directory for the user.</li>
   </ul>
   <ul>
    <li> -G Engineers: Adds the user to the Engineers group.</li>
   </ul>
   <ul>
    <li> -s /bin/bash: Sets /bin/bash as the default shell for the user.</li>
   </ul>
   <ul>
    <li>-c "Jordan Blake, jblake@linuxproject.com": Adds the full name and email to the comment (GECOS) field.</li>
   </ul>
   <ul>
    <li>echo "jblake:password" | sudo chpasswd: This sets the password for the user (password should be replaced with the actual password you want to assign).</li>
   </ul>
</ol>
<h2>Step 3: Verify User Prmissions </h2>
<ol>
   <li>Switch to each user and verify directory permissions. Switch to each user with su:</li>
    <br><img src="https://imgur.com/jW2Hd5J.png" height="30%" width="30%" alt="script"/></br>
   <ul>
      <li>Verify that only /Engineering is accessible to jblake by trying to cd into the other directories (/Operations and /Analytics). They should get a "Permission denied" error.</li>
   </ul>
   <ul>
      <li>Use the following commands to test:</li>
   </ul>
   <img src="https://imgur.com/wSFoM16.png" height="30%" width="30%" alt="script"/>
   <br/>
</ol>
<h2>Step 4: Create Bash Script for Automation </h2>
<ol>
   <li>Now, let’s create a bash script that automates everything we did for user and permission creation.</li>
   <ul>
      <li>Run the code: nano setup_users_and_permissions.sh</li>
   </ul>
   <img src="https://imgur.com/LfKoiGW.png" height="40%" width="40%" alt="script"/>
   <br/>

   <li>Create the bash script by running the following:</li>
   <ul>
      <img src="https://imgur.com/e8QQhBB.png" height="40%" width="40%" alt="script"/>
      <br/>
   </ul>

   </ul>
   <li>Make the script executable:</li>
   <ul>
      <li>Run the following script: chmod +x setup_users_and_permissions.sh</li>
      <img src="https://imgur.com/9JCPC7W.png" height="25%" width="25%" alt="script"/>
      <br/>
      <ul>
      <li> Run the script as the root user</li>
      </ul>
<li>Note, when running script, it will says users already exists as we already created them earlier. This script automates our process making it more efficient. You can now login as the created users and test that the permissions are accurate.</li>
   </ul>
</ol>
   <h2>Step 7: Conclusion</h2>
  In conclusion, this guide offers a practical framework for managing users, groups, and directory permissions in Linux. By aligning directory structures and user groups with organizational teams such as Engineering, Operations, and Analytics, administrators can streamline access control. Leveraging tools like chown and chmod, permissions can be precisely configured to ensure that only authorized users access specific directories. Through clear examples of user creation and permission configuration, this guide demonstrates how to effectively restrict access and enhance security within a Linux environment..     
</ol>
