<h1>Cross-Platform Patch Management</h1>
<img src="https://i.ibb.co/2n63V9p/cross-pic.png" alt="cross-pic" width="1000" height="500">

<h2>Description</h2>
<b>
Cross-platform patch management using PowerShell involves automating the process of identifying, downloading, and installing updates across various operating systems (Windows, Linux, macOS) within an organization's infrastructure. 
<br><br>
This solution helps organizations streamline patching operations, reduce the risk of exploitation, and comply with regulatory standards. By leveraging automation, businesses can lower their attack surface, ensure system compliance, and respond faster to emerging security threats.
</b>
<h2>Purpose</h2>
<p><b>This script is designed for IT administrators to automate the process of:</b></p>

<p><b>- Checking for updates.</b></p>
<p><b>- Installing updates.</b></p>
<p><b>- Logging the update process.</b></p>
<p><b>- Rebooting the system when required.</b></p>
<p><b>It’s especially useful in environments like corporate IT, where patching systems regularly is critical for security and compliance
<p><b>To ensure that it would'nt be used as an attack vector if lacking or falling behind in software updates. </b></p>
<h2>Utilities Used</h2>

- <b>PowerShell</b> 
- <b>Task Scheduler<i>(Patch management automation)</i></b>

<h2>Environments Used</h2>

- <b>Windows 10 <i>(22H2)</i></b>  
- <b>VS Code</b>  

<h2>Program Features</h2>

<p><b>1. Cross-Platform Patching</b></p>
<p><b>Utilize native tools like `PSWindowsUpdate` for Windows.</p></b>
<p><b>But first we must install it </p></b>

<img src="https://i.ibb.co/jyMDfNG/ps4.png" alt="ps4" border="0"></a>
<br>
<br>
<img src="https://i.ibb.co/WDpjNYB/ps5.png" alt="ps5" border="0"></a>

<h3>Step 1. Import the PSWindowsUpdate module</h3>

<p><b>This command loads the PSWindowsUpdate module, which provides PowerShell cmdlets for managing Windows updates. </b></p>

<p><b>It's a prerequisite for running commands like:
<p><b><code>Get-WindowsUpdate</code>:Lists available updates.</b></p>
<p><b><code>Install-WindowsUpdate</code>:Installs updates.</b></p>
<p><b><code>Get-HotFix</code>: Lists already installed updates.</b></p>

<h3>Step 2. Check for Pending Updates</h3>

<p><b>Uses the <code>Get-WindowsUpdate</code> cmdlet to scan for available updates.</b></p>
<p><b>Flags:</b></p>

<p><b>- -AcceptAll: Bypasses prompts for user confirmation.</b></p>
<p><b>- -IgnoreReboot: Skips checking whether a reboot is needed from previous updates.</b></p>

<h3>Step 3. Display Available Updates</h3> 

<p><b>Checks if updates are available and lists their KB article IDs and titles.</b></p>
<p><b>If no updates are found, the script exits.</b></p>

<h3>Step 4. Install Updates</h3> 

<p><b>Installs all available updates using <code>Install-WindowsUpdate</code>.</b></p>

<p><b>Flags:</b></p>

<p><b>- -AcceptAll: Automatically accepts installation.</b></p>
<p><b>- -IgnoreReboot: Prevents an automatic reboot.</b></p>
<p><b>- -Verbose: Outputs detailed installation information.</b></p>

<h3>Step 5. Log Update Status</h3>

<p><b>Saves details of the updates to a log file in the <code>C:\PatchManagementLogs folder.</code></b></p>
<p><b>The log filename includes the current date <code>(yyyyMMdd format)</code> for easy tracking.</b></p>

<h3>Step 6. Reboot if Required</h3>

<p><b>Uses <code>Test-PendingReboot</code> to check if a system reboot is required after installing updates.</b></p>
<p><b>If a reboot is needed:</b></p>
<p><b>- Prints a message and forces the system to restart with <code>Restart-Computer -Force</code></b></p>
<p><b>If no reboot is required:</b></p>
<p><b>- Prints a message indicating the process is complete.</b></p>

<p><b>Step 7: Save the Script</b></p>

<p><b>Save the script to a .ps1 file, e.g., PatchManagement.ps1.</b></p>

<h2>Directory</h2>

<p><b>Create a directory for logs, such as C:\PatchManagementLogs. </b></p>
<img src="https://i.ibb.co/MkqCMZg/ps8.png" border="0">

<p><b><code>New-Item:</code></b></p>
<p><b>The PowerShell cmdlet used to create a new item in the specified path.</b></p>

<p><b><code>-Path "C:\PatchManagementLogs":</code></b></p>
<p><b>Specifies the location where the item should be created. In this case, it will create the item at <code>C:\PatchManagementLogs.</code></b></p>

<p><b><code>-ItemType Directory:</code></b></p>
<p><b>Defines the type of item to create. Here, it creates a directory (a folder). </b></p>

<p><b>Now,Let's make sure the directory i.e. folder exists.</b></p>
<img src="https://i.ibb.co/VxjycWS/ps9.png" border="0">

<p><b><code>Test-Path:</code></b></p>
<p><b>A PowerShell cmdlet that verifies the existence of a path (file, folder, or other item).</b></p>

<p><b><code>C:\PatchManagementLogs:</code></b></p>
<p><b>The path being checked. This example checks if the folder PatchManagementLogs exists in the root of the C: drive.</b></p>

<p><b><code>True:</code></b></p>
<p><b>Means the path exists.</b></p>

<p><b><code>False:</code></b></p>
<p><b>Means the path does not exist.</b></p>

<h2>Running</h2>

<p><b>Now,Now, Open Powershell as an admin and run the script</b></p>

<p><b>Now verify that: </b></p>

<p><b>Updates are listed.</b></p>
<img src="https://i.ibb.co/0KGznKs/ps10.png" border="0"></a>

<p><b>Updates are installed.</b></p>
<img src="https://i.ibb.co/pjdzVq4/ps11.png" border="0">

<p><b>Now a log file should be in C:\PatchManagementLogs,lets check.</b></p>
<img src="https://i.ibb.co/K98CdwC/yup.png" border="0">

<p><b>Thier is created log file</b></p>
<img src="https://i.ibb.co/2jM7XVK/yurr.png" border="0">

<p><b>And the logs in the file listing the software updates.</b></p>
<img src="https://i.ibb.co/279qJ99/PS13.png" border="0">

<h2>Schedule the Script</h2>

<p><b>To automate the patch management process, use Task Scheduler:</b></p>

<p><b>- Open Task Scheduler.</b></p>
<p><b>- Click Create Task.</b></p>
<p><b>- Set the Trigger (e.g., run weekly on Sundays at midnight).</b></p>
<img src="https://i.ibb.co/4txRhcX/ps14.png" border="0">
<img src="https://i.ibb.co/4g2ck7S/ps15.png" border="0">

<p><b>- Set the Action to run in PowerShell:</b></p>
<img src="https://i.ibb.co/mC6GNMh/mon.png" border="0">

<p><b><code>powershell.exe:</code></b></p> 
<p><b>This launches the PowerShell executable, allowing you to run PowerShell commands or scripts from the command line, a batch file, or other automation tools.</b></p>

<p><b><code>-ExecutionPolicy Bypass:</code> Temporarily overrides the PowerShell execution policy to allow the script to run.</b></p>

<p><b>- Execution Policy: A security measure in PowerShell that controls how scripts are executed. Common policies include:</b></p>

<p><b>- Restricted: Default policy; prevents all scripts from running.</b></p>

<p><b>- RemoteSigned: Requires scripts from the internet to be signed by a trusted publisher.</b></p>

<p><b>- Bypass: Ignores the execution policy entirely for this session or command, allowing all scripts to run without restrictions.</b></p>

<p><b>- Why Bypass?: Often used in automation scenarios where you don’t want to change the system’s global execution policy permanently but need to run a script like we are doing here.</p>

<p><b><code> -File C:\Path\To\PatchManagement.ps:</code> Specifies the full path to the PowerShell script file (PatchManagement.ps) to be executed.</b></p>



<h3>End of the project walkthrough! Thank you!</h3>
