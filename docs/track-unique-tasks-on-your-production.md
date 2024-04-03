---
sidebar_label: 'Track Unique Tasks on Your Production'
hide_title: 'true'
---

## Track Unique Tasks on Your Production

**Quick definition of a unique task**

Your contract is based on a **daily average** of unique tasks executed on your **Production** environment. Here is a definition of what is a unique task and how does it works :

* 1 job instance executed = 1 unique task / day.
* 1 **recurrent** job executed with the **same parameters** = 1 unique task / day (you can restart 500 times the job, if the parameters are the same it will be a single unique task).
* **Container** and **Null** job not counted.
* **SMA Utility** maintenance jobs not counted.

**How to track the current statistics ?**

In the **Enterprise Manager**, you can find a predefined report named "**Unique Task Count**". This report provides the statistics for a specific month of a year. This allows you to track the statistics on your **OpCon** environment.