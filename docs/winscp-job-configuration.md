---
sidebar_label: 'WinSCP Job Configuration'
hide_title: 'true'
---

## WinSCP Job Configuration

WinSCP is a free SFTP tool for Windows that allow you to perform secured file transfer using SFTP, SCP or SSH-1/SSH-2 protocols. This article will show you how to create a Windows Job in OpCon to control a file transfer operated by WinSCP using FTPS or SFTP.

**Requirements**

* An MSLSAM
* WinSCP installed

**Preparation**

Depending on the user log in, a batch profile for WinSCP may need to be created. Create a **Batch User** within Enterprise Manager to match the user profile using WinSCP.

![](../static/img/rtaImage-187.png)

Then in the next step we'll create three **global properties**:

* Global Property for **username**: WinSCPUser
* Create Global property for **password** (Encrypted): WinSCPPassword
* **Hostkey** for public key : WinSCPHostKey (if setup is for FTPS, skip to the next step "Job Creation with FTPS protocol")
* Configuration of the SFTP Hotkey : see "Get SFTP Hostkey"

**Job Creation with FTPS protocol**

To **upload** a file, create a job with the following command line as example using **"put"**:

* `"C:\Program Files (x86)\WinSCP\winscp.com" /log="C:\Winscp\Log\WinSCP[[$JOBID]].log" /command "open ftps://[[WinSCPUser]]:
[[WinSCPPassword]]@files.smatechnologies.com/" "**put** C:\Winscp\Debug.log /SMA_Employees/Jesparza/" "exit"`

**About the command line**

* `"C:\Program Files (x86)\WinSCP\winscp.com"`: the folder where is located the winscp.com program
* `/log="C:\Winscp\Log\WinSCP[[$JOBID]].log"`: the place where the log are sent
* `/command "open ftps://[[WinSCPUser]]:[[WinSCPPassword]]@files.smatechnologies.com/"`: the connection string to the server
* "**put** `C:\Winscp\Debug.log /SMA_Employees/Jesparza/"`: the source file you want to upload and its destination (get for download)

![](../static/img/rtaImage-188.png)

* When using this command, ensure **/log** has a path to a directory, this will begin saving log files to the directory, this will help with troubleshooting.

:::info Note 

If the directory has a space use 2 double quotes from the start of the directory to the end of the file extension.

:::

:::tip Example 

`“put“ ”C:\Program Files\File.txt”” /Directory/`”

:::

To **download** a file, create a job with the following command line as example using "**get**":

`"C:\Program Files (x86)\WinSCP\winscp.com" /log="C:\Winscp\Log\WinSCP[[$JOBID]].log" /command "open ftps://[[WinSCPUser]]:[[WinSCPPassword]]@files.smatechnologies.com/" "get /SMA_Employees/Jesparza/File.txt C:\Winscp\ " "exit"`

![](../static/img/rtaImage-189.png)

**Get a public HostKey for SFTP**

Open puttygen.exe which is located directly under PuTTY or WinSCP, examples:

* `C:\Program Files\PuTTY\puttygen.exe`
* `C:\Program Files (x86)\WinSCP\PuTTY\puttygen.exe`

![](../static/img/rtaImage-190.png)

Copy the Public key generated into the **WinSCPHostKey** global property created in the **Preparation** step.

To download a file using SFTP, create a job with the following command line as example using **"get"** with a **-hostkey** parameter:
`"C:\Program Files (x86)\WinSCP\winscp.com" /log=”C:\Winscp\Log\WinSCP[[$JOBID]].log” /command "open sftp://[[WinSCPUser]]:[[WinSCPPassword]]@files.smatechnologies.com/ -hostkey=""[[WinSCPHostKey]]" "get /SMA_Employees/Jesparza/*.log C:\Winscp\" "exit"`

* When using this command, ensure /log has a path to a directory, this will begin saving log files in the directory, this will help with troubleshooting.

:::info Note 

If the directory has a space use 2 double quotes from the start of the directory to the end of the file extension.

:::

:::tip Example 

`“put“”C:\Program Files\File.txt”” /Directory/”`

:::

:::tip **Example downloading file(s) using Private Key and PassPhrase**

`winscp.com /log="C:\Winscp\Log\WinSCP.log" /command "open sftp://username@sftp.SMA.com/ -privatekey=""C:\Location\FileName.ppk"" -passphrase=""PASSPHRASE""" "get /Dir/Filename.txt D:\directory\" "exit"`

:::

