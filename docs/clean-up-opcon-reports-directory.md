---
sidebar_label: 'Clean Up opcon_reports Directory'
hide_title: 'true'
---

## Clean Up opcon_reports Directory

**How to clean-up your directory**

Use these commands clean up all the files and symbolic links in the opcon_reports directory across all SYMs on your Symitar host.

This one removes the files that don't match **BATCH_OUTPUT**:

`find /SYM/SYM*/opcon_reports/*/ -type f ! -name 'BATCH_OUTPUT*' -exec rm {} \;`

This one removes the links that don't match **BATCH_OUTPUT**

`find /SYM/SYM*/opcon_reports/*/ -type l ! -name 'BATCH_OUTPUT*' -exec rm {} \;`

If you want to have a permanent solution, do the following to the **SMA_DEFAULTS** file for each SYM that jobs are run in. 

1. Set the directive to false to stop creating the links.

`cd /SYM/SYM000/BATCH/`

`vi SMA_DEFAULTS`

add the following line:

`;CREATE_OPCON_REPORTS_LINKS false`

2. Allow at least a **week** to **10 days** for old links to be removed by the backup and prune job in the SMAUtility schedule.

3. Verify the *CREATE_OPCON_REPORTS_LINKS* false is working by going to the `/SYM/SYMnnn/opcon_reports` folder and doing an "`ls -la`"