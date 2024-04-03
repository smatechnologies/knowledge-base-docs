---
sidebar_label: 'Issues With Automation of Office Products'
hide_title: 'true'
---

## Issues With Automation of Office Products

**What is the issue?**

You may encounter some issues when trying to automate some functions with **Office Products**. 

Below an example of the issue:

:::tip Example

Unable to get the SaveAs property of the Workbook class At C:\ProgramData\OpConxps\MSLSAM\Temp\TEST_PowerShellScript.ps1:195 char:1 + $ActiveWorkbook.SaveAs($outputExcel) + ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~ + CategoryInfo : OperationStopped: (:) [], COMException + FullyQualifiedErrorId : System.Runtime.InteropServices.COMException

:::

**How to solve it?**

It can happen in some situations where the user who starts the **Excel** is a system user. Excel expects the existence of the **Desktop directory**. To enable the command to work try the following :

For x64 processes **create** the following folders:

`C:\Windows\SysWOW64\config\systemprofile\Desktop`

`C:\Windows\System32\config\systemprofile\Desktop`