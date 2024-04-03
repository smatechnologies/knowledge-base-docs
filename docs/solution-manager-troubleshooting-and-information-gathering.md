---
sidebar_label: 'Solution Manager Troubleshooting and Information Gathering'
hide_title: 'true'
---

## Solution Manager Troubleshooting and Information Gathering

**What**

If you encounter an error on your Solution Manager web interface, you can follow the steps below to troubleshoot or collect the information to provide us with in a support ticket.

**Steps**
 
**1. When exactly did the bug happen (Allows to locate error in logs)?**

When visiting Solution Manager a pop up for user information comes up.  Client enters the user information and does not recognize the user account.  Client clicks cancel and they are able to view Solution Manager log in screen.  Next they click on Windows Authentication is able to log in when clicking the option twice.

Internet Options => Security for Local Intranet for User Authentication has Automatic logon only in Intranet zone.  Trusted site for custom has Automatic logon with current user name and password.

Client does not want to change Local Intranet for User Authentication to Automatic logon with current user name and password.

Local intranet also has the website within their security level settings.

**2. Logs**
 
Three way to generate logs:

a.Instant Log (Recommended)
   When an error can be easily reproduced, thanks to:
   - Enable instant log: Ctrl-Alt-L (A red bug icon appears at the bottom right of the Solution Manager)
   - Reproduce the error
   - Press Ctrl-Alt-L again to stop the capture
   - Download the generated log file

b.Standard way (If the bug cannot be reproduced in a short period)
   - By default, the Solution Manager send log files on the server only if a warning or an error occurs.
   If no warning or error is emitted, you can change the configuration: "Send Trigger" to "Send on Interval and Max Size" in the Solution Manager > Profile > Application Settings tab > Debug > Server Send > Send Trigger
   - Please also turn on "API" debugging in the **Solution Manager > Profile > Application Settings tab > Debug > Server Send**
   - Logout/Login if Log configuration has been changed
   - Reproduce the issue
   - If "Send Trigger" is set on "Send on Interval and Max Size", thanks to be sure the interval is expired before take log files from the server

c. Web Browser console (only in case of failure of other methods. On white Page or if logs are empty and shouldn't)   - Please Change the configuration: "Client Log Level" to "TRACE" in the Solution Manager > Profile > Application Settings tab > Debug
   - Open Chrome Dev Tools (F12)
   - Refresh the page (F5)
   - Reproduce the issue
   - Select the "Console" tab (Can be slightly different in other web browsers)
   - Select "Default levels" if "Custom levels" filter is set
   - Right click on the console, "Save as..."
   - Select the "Network" tab
   - Right click on the list, "Save all as HAR with content"

Attached to the case are the console saves from their browser.

