# TimeRemaining

[![image](https://github.com/LesFerch/WinSetView/assets/79026235/0188480f-ca53-45d5-b9ff-daafff32869e)Download the zip file](https://github.com/LesFerch/TimeRemaining/archive/refs/heads/main.zip)

This is a package that provides an on-screen countdown of time remaining before a forced logout.

The execution is set up via two scheduled tasks, one running in the user context that provides the display, and one running in the SYSTEM context that will restore the countdown if the user kills the display task.

The display task includes an **Add Time** button that, when clicked, will run another script elevated to allow an administrator to give the user more time.

The script also displays a toast notification to the user when there's 2 minutes left (the time can be adjusted in the script).

## Installation

From the **Code** menu on the GitHub page, select **Download ZIP**.

Unzip the files to the folder **C:\HTA-TimeRemaining**. If you wish to use a different folder, you will have to edit the scheduled task XML files to the correct path.

**Note**: The target folder cannot have any spaces in its path (e.g. it won't work inside a subfolder of "Program Files"). This is a limitation of the **Elevate.exe** program needed to elevate and wait for the AddTime script.

Edit the permissions of the folder so that standard users have **read-only** access.

Open Task Scheduler, click **Import Task...** and select the file **TimeRemaining.xml**. Repeat for the file  **TimeRemaining-Maintain.xml**.

That's it! The scripts will run on next login.

**Note**: The tasks are set to run the scripts on login. Since **TimeRemaining.hta** is run in the user context, it automatically closes when the user logs out. However the **Maintain.vbs** script runs as SYSTEM, so it detects when the user logs out and closes itself.

**Note**: The **Maintain.vbs** script (that restarts TimeRemaining.hta) does not work reliably with user switching. You must logout and login to be sure that it tracks the correct user.

\
[![image](https://github.com/LesFerch/WinSetView/assets/79026235/63b7acbc-36ef-4578-b96a-d0b7ea0cba3a)](https://github.com/LesFerch/TimeRemaining)
