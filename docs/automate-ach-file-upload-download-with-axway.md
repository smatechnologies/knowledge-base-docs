---
sidebar_label: 'Automate ACH File Upload/Download With AXWAY'
hide_title: 'true'
---

## Automate ACH File Upload/Download With AXWAY

**What?** 

You can automate the download/upload of your ACH files to AXWAY with a KickoffScript and a Download/Upload script.

The **KickoffScript.cmd** is straight forward where %1 is the Download/Upload Script:

`"C:\Program Files (x86)\Axway\SecureClient\sclient.cmd" script %1`

The **OpCon** job should be set up with the following syntax:

`"<Path>\KickoffScript.cmd" "<Path>\Download/Upload.txt>"`

The Download/Upload script use FTP commnads to get the files. In these scripts, you will need to update the parameters to reflect your environment. 

| Download Script | Upload Script |
| --------------- | ------------- |
| open SiteName | open SiteName |
| chdir SourcePath | chdir DestinationPath |
| lchdir LocalPath | lchdir LocalPath |
| mget FileName | lchdir LocalPath |
| close | mput FileName |
| | close |

* **SiteName** - is the name of the site that is configured in Axway
* **SourcePath** - is the path to the files located on the site that they are connecting to
* **LocalPath** - is the path to where they would like to download the files to
* **FileName** - is what they would like to name the files. Typically, this is just a *.*
 
:::tip Example

**Download Command Line:**
**OpCon Job:**

`"<Path to KickoffScript.txt>" "C:\FED ACH\scripts\TestDownload.txt"`

The contents of the **“TestDownload.txt”** file will generally contain something similar to the following:

```
open FedACH_dit_outbound

chdir /fedlinecommand_dit/outbound/all

mget *.*

close
```

:::

:::tip Example

**Upload Command Line:**

**OpCon Job:**

`"<Path to KickoffScript.txt>" “C:\FED ACH\scripts\TestUpload.txt"`

The contents of the **“TestUpload.txt”** file will generally contain the following:

```
open FedACH_dit_inbound

chdir /fedlinecommand_dit/outbound/all

mput *.*

close
```

:::

OpCon needs a dedicated LSAM running under the credentials approved by the Fed. You can have multiple LSAMs on the same machine, but the agent service calling the sclient.cmd command must be running as the Fed-approved credential.

**All the scripts needed for this are attached to the article.**

Axway Sites are profile based just like WS_FTP

Sample of Site Names:

*Test*

*FedACH_dit_inbound*

*FedACH_dit_outbound*

*Production*

*FedACH_prod_inbound*

*FedACH_prod_outbound*

**Axway** is installed in:

`C:\Program Files (x86)\Axway\SecureClient`