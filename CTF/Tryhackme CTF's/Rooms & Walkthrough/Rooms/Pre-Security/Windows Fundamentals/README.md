# [Windows Fundamentals](https://tryhackme.com/room/windowsfundamentals1xbx)

Windows operating system (OS) is a complex product with many system files, utilities, settings, features, etc. 
This module will attempt to provide a general overview of just a handful of what makes up the Windows OS, navigate the user interface, make changes to the system, etc. The content is aimed at those who wish to understand and use the Windows OS on a more comfortable level.
Launch the attached virtual machine. The virtual machine should open within your web browser. 

> Hamza , 27/2/22

-----------


## PART 1 :

- What encryption can you enable on Pro that you can't enable in Home?

`BitLocker`

- Which selection will hide/disable the Search box?

![](https://assets.tryhackme.com/additional/win-fun1/win-taskbar1.png)

`search > hidden`

- Which selection will hide/disable the Task View button?

`Show Task View button`

- Besides Clock, Volume, and Network, what other icon is visible in the Notification Area?

![](https://assets.tryhackme.com/additional/win-fun1/win-desktop2.png)


`Action Center`

- What is the meaning of NTFS? 

![](https://assets.tryhackme.com/additional/win-fun1/win-file-system.gif)

`New Technology File System`

- What is the system variable for the Windows folder?

![](https://assets.tryhackme.com/additional/win-fun1/windows-system32.png)


`%windir%`


- What is the name of the other user account?

![](https://assets.tryhackme.com/additional/win-fun1/win-other-user1.png)

`tryhackmebilly`

- What groups is this user a member of?

![](https://assets.tryhackme.com/additional/win-fun1/win-lusrmgr.gif)

`Remote Desktop Users,Users`


- What built-in account is for guest access to the computer?

`Guest`



- What is the account status?

`Account is disabled`


- What does UAC mean?

`User Account Control`

- In the Control Panel, change the view to Small icons. What is the last setting in the Control Panel view?

`Windows Defender Firewall`

- What is the keyboard shortcut to open Task Manager?

`Ctrl+Shift+Esc`

---------------------------

##  PART 2 :

- What is the name of the service that lists Systems Internals as the manufacturer?

![](https://assets.tryhackme.com/additional/win-fun2/msconfig3.png)

`PsShutdown`

- Whom is the Windows license registered to?

`Windows User`

- What is the command for Windows Troubleshooting?

`C:\Windows\System32\control.exe /name Microsoft.Troubleshooting`

- What command will open the Control Panel? (The answer is  the name of .exe, not the full path)

`control.exe`

- What is the command to open User Account Control Settings? (The answer is the name of the .exe file, not the full path)

![](https://assets.tryhackme.com/additional/win-fun2/uac.png)

`UserAccountControlSettings.exe`

- What is the command to open Computer Management?

![](https://assets.tryhackme.com/additional/win-fun2/event-viewer.png)

`compmgmt.msc`

- At what time every day is the GoogleUpdateTaskMachineUA task configured to run?

`6:15 AM`

- What is the name of the hidden share?

`sh4r3dF0Ld3r`

- What is the command to open System Information?

![](https://assets.tryhackme.com/additional/win-fun2/env-variables.png)

`msinfo32.exe`

- What is listed under System Name?

`THM-WINFUN2`


- Under Environment Variables, what is the value for ComSpec?

`%SystemRoot%\system32\cmd.exe`


- What is the command to open Resource Monitor?

`resmon.exe`

- In System Configuration, what is the full command for Internet Protocol Configuration?

`C:\Windows\System32\cmd.exe /k %windir%\system32\ipconfig.exe`

- For the ipconfig command, how do you show detailed information?

`ipconfig /all`

- What is the command to open the Registry Editor?

`regedt32.exe`

---------------

## PART 3 :

- There were two definition updates installed in the attached VM. On what date were these updates installed?

![](https://assets.tryhackme.com/additional/win-fun3/windows-update3.png)

`5/3/2021`


- In the above image, which area needs immediate attention?

![](https://assets.tryhackme.com/additional/win-fun3/windows-security1b.png)

`Virus & threat protection`

- Specifically, what is turned off that Windows is notifying you to turn on?

`Real-time protection`

- If you were connected to airport Wi-Fi, what most likely will be the active firewall profile? 

![](https://assets.tryhackme.com/additional/win-fun3/windows-firewall4.png)

`Public network`

- What is the TPM?

`Trusted Platform Module`

- What must a user insert on computers that DO NOT have a TPM version 1.2 or later?

`USB startup key`

- What is VSS? 

`Volume Shadow Copy Service`






