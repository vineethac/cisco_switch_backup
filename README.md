# Overview
This project saves running configuration of Cisco switches to a TFTP server. 
Note: I tested it on Cisco Nexus 9K switches.
# Prerequisites
1. TFTP server should be configured and running.
2. SSH should be enabled on the switch.
3. PowerShell module Posh-SSH should be installed on the node from which the script is running.
4. All the switches should have same user name and password.
5. Password should be encrypted and written to a text file called "keyfile.txt" under "/lib/key" location.
# How to use?
Once the project is cloned to your local machine, follow the steps below.
1. Edit "ip_list.txt" and provide IP of the switches that you want to backup.
2. Next step is to edit "invoke_switch_config_backup.ps1" and provide TFTP server location (at the end of the script).
3. If user name to login to your switch is not "admin", you need to edit it in "invoke_switch_config_backup.ps1". 
4. Encrypt the password and save it in "keyfile.txt" under "/lib/key" location. Example: "Pass1234" | ConvertTo-SecureString -AsPlainText -Force | ConvertFrom-SecureString | Out-File "C:\keyfile.txt" . Here "Pass1234" will be encrypted and stored in "C:\keyfile.txt". Copy this "keyfile.txt" and replace it with key file under "/lib/key".
5. PS > .\invoke_switch_config_backup.ps1
# Use case
You can schedule this PS script using a task scheduler, so that the running configuration of switches can be backed up automatically on a daily basis or as per requirements. 
![image](https://user-images.githubusercontent.com/30316226/71763041-ca2dda80-2e9c-11ea-9d57-a46ece45278e.png)

# References
1. Encrypting creds with PowerShell: https://www.pdq.com/blog/secure-password-with-powershell-encrypting-credentials-part-1/
2. Setting up a TFTP server: http://www.tricksguide.com/how-to-setup-a-tftp-server-tftpd32-windows.html
