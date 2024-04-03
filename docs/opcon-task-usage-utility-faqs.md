---
sidebar_label: 'OpCon Task Usage Utility FAQS'
hide_title: 'true'
---

## OpCon Task Usage Utility FAQS

This article answers the most common questions regarding the OpCon Task Usage Utility.  Detailed instructions and steps in configuring and setting up the Task Usage Utility job in OpCon can be found in this **article**.

**Frequently Asked Questions**

* Why do I need to do this?

    * With the **SMA Technologies subscription agreement**, your SMA Technologies Customer Success Team will be able to use this information to make sure that your automation needs are in line with your **subscription plan**.

    * This automated solution removed any manual tasks in place to capture this information.

    * Failure to have this true usage tracking may cause confusion and erroneous assumptions being made about your subscription model.  This helps to have an informative discussion with your CSM.

* Is this required to provide SMA Technologies the TaskCount according to our current subscription plan?

    * The purpose of sending us your statistics is to allow us to regularly monitor your automation needs and ensure that your subscription plan is in line with them.

* What data is the Task Usage Utility extracting?

    * We track all uniquely running tasks: for time periods, departments, and machines.
    
    * Tasks that are re-run with the same parameters and core tasks run by certain executables are excluded from the official counts. We only count the tasks configured for customer automation.

    * The extracted data are aggregate counts of tasks and capture the OpCon component in use. No customer-specific information is extracted.

    * During installation, this tool will create a new schedule and run as an OpCon job which can be configured like any other job.

    * On the first run, the job will collect all daily counts for the previous year. Subsequent jobs will only collect counts from where the previous job left off.

* Will my data be secure?

    * The data is extracted daily and either automatically uploaded to our secure cloud system or can be emailed to us and the data is securely housed in the cloud repository. The aggregate data is available to your Customer Success Manager, and they are able to understand your usage and needs as you grow your business.

* Is it mandatory to run the extract and send the file on a daily basis?

    * It is not mandatory to run this job on a daily basis but it is recommended to run this job a minimum of once a week.