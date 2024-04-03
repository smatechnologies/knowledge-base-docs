---
sidebar_label: 'File Arrival Best Practices'
hide_title: 'true'
---

## File Arrival Best Practices

**File Arrival Jobs** are a powerful tool for automation.  Here are some guidelines to use to get the most out of your processes using the File Arrival utility.

File Arrival has some normal **exit codes** to keep in mind when creating jobs. If a file matching your specified filename and creation time frame is found, the job will exit with a `0`.  

OpCon will automatically treat this* exit code as a "`Finished OK`", but it is frequently desirable to have the job **Finish OK** when no file is found (`exit code 1`) or when a file matches the filename, but was not created during the specified time frame (`exit code 3`).  

In this case, you can use the **Failure Criteria** section at the bottom of the **Job Details** page to instruct OpCon to treat those exit codes as `Finished OK`.


