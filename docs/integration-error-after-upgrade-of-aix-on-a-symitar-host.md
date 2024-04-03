---
sidebar_label: 'Integration Error After Upgrade of AIX on a Symitar Host'
hide_title: 'true'
---

## Integration Error After Upgrade of AIX on a Symitar Host

**What is the issue?**

Jobs that run Episys PowerOn that transfer files are now failing after upgrading **AIX** to **7.1 TL5 SP9** or **beyond** on a Symitar host. The job in OpCon will fail with the following error message:

**Integration error: No such file or directory**

**How to solve the issue**

* Log into the AIX machine as root
* Navigate to the location of the SMA_DEFAULTS file.
    * `cd /SYM/SYM000/BATCH`
* Once there cat the file to verify the contents of the SMA_DEFAULTS file
    * `cat SMA_DEFAULTS`
    * Example of what you may see:

```
    ;MAX_EXCEPTIONS = 99999999=
    ;ERROR_LEVEL 1-4,6,10-13=
    ;CREATE_OPCON_REPORTS_LINKS = false=
    ;JAVA_HOME "/usr/java7"=
```

* If you already have `;JAVA_HOME` specified then update accordingly. If `;JAVA_HOME` isn't there, you will need to add it.
    * You will need to locate the most current version of Java by navigating to the `/usr` directory in AIX.
    * Once there you'll likely see multiple versions of Java, locate the most current version then proceed.
* Use **vi editor** to add or modify the **SMA_DEFAULTS** file to reflect the correct path to the JAVA_HOME location, as provided below.
    * `;JAVA_HOME "/usr/java8"`
* An alternative to using vi is to modify the **SMA_DEFAULTS** file on a Windows machine. If you choose this method, the file needs to be transferred on and off the host in **ASCII/Text** mode.
* Lastly, restart your jobs and you should immediately notice the change.