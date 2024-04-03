---
sidebar_label: 'Avoid Conficts Between OpCon and Antivirus'
hide_title: 'true'
---

## Avoid Conflicts Between OpCon and Antivirus

Best Practices to avoid any conflict between OpCon processes and antivirus or a log scanner.

**Security on your server**

More than ever, **security** is a sensitive and critical element in protecting your company infrastructure and data integrity. You probably already have or plan to add another security layer on your server through an antivirus, scanner or even a log collector. The purpose of this article is to provide the best practices that OpCon and your security applications coexist harmoniously without any conflict.

**OpCon and antivirus** 

OpCon is a critical application as it's handling your automatisation and therefore its processes must remain protected from external interference to avoid dysfunction or outage.

By default, an antivirus is scanning the whole system, all the folders and the files searching for viruses or malwares. In a scan operation, it happens that the antivirus is holding a critical files for one of OpCon processes or LSAM such as a log file, a tracking file or anything else needed for proper functioning.

**Possible symptoms**

The following symptoms can be caused by an antivirus scan:

* A non-critical process is stuck because the log is not accessible.
* A critical process is stuck because the log file/trk is not accessible : can lead to a Production outage.
* e.g. SMA NetCom can't access the tracking file, the SMASchedMan can't write in the log, etc.
* As it's a critical process, the SMAServMan will shut down after unsuccessful attempts to start.
* Jobs are stuck because the LSAM can't access its files (tracking files or log files).
* The communication is not necessary down but the jobs will remain in "Still attempted start" because the LSAM can't start them.
* Spikes in resource usage can occur, causing the system to slow or crash

See the article **"Troubleshooting OpCon files locked"** for more information about the identification and the resolution of this kind of issue.

**Recommendations**

In order to prevent any issues on your OpCon environment, our recommendations are to add the following repositories, and any other OPCON-related folders, on your **Antivirus whitelist or exclusions**:

* `C:\ProgramData\OpConxps`: where are located all the .ini, tracking, log files, etc.
* `C:\Program Files\OpConxps`: where are located the programs, LSAMs, Connectors.
* `C:\Program Files (x86)\OpConxps`: where are located DDI, SNMP, some utilities.

If your OpCon applications are not installed on the C: disk, please exclude the appropriate folders. (e.g. `D:\OpConxps`)

Other things to consider are app exclusions, and any .exe's related back to OpCon should be considered. Some examples are:

* `(PATH)\OpconXPS\SMAResourceMonitor\SMAResourceMonitor.exe`
* `(PATH)\OpConxps\MSLSAM\MSLsam.exe`
* `(PATH)\OpConxps\MSLSAM\MSJORS.exe`
* `(PATH)\OpConxps\SAM\SMAOpConRestApi.Controllers.exe*`
* `(PATH)\OpConxps\SAM\SMAServMan.exe`
* `(PATH)\OpconXPS\SAM\ENS\SMANotifyHandler.exe`

:::info Note

The particular one to keep in mind is the SMAOpConRestApi.Controllers.exe. In versions prior to 20, the restAPI was a separate installer and could be placed in a separate directory. In versions 20+, the api is included in the opcon installer and as a result will always be in the opconxps directory specified.

:::

For your **Firewall** configuration, please refer to this article: [Ports used by OpCon communication](ports-used-by-opcon-communication).