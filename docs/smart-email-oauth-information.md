---
sidebar_label: 'SMArt Email OAuth Information'
hide_title: 'true'
---

## SMArt Email OAuth Information

Starting October 1st, 2022 Microsoft will begin to **disable basic authentication** methods for Exchange Online customers.

This will have an impact on jobs using **OpCon’s SMArt Email** connector that authenticate with a Microsoft email account. **SMArt Email jobs** may begin to be impacted as soon as October 1st, 2022 based on when basic authentication is disabled for your specific service provider.

In support of this initiative, we have updated our **SMArt Email** connector to support Microsoft’s **OAuth** authentication method. Enabling this new method will require you to install a small update for the connector and a few configuration steps to complete authentication credentials with the new method. Once updates to the application and configuration are complete, all existing **SMArt Email** jobs will begin leveraging the new method and credentials automatically without any changes being required at the job level or to the configuration file.

**These updates will only be required for SMArt Email authentication with Microsoft Exchange-based email accounts.**

Please refer to the Knowledge Base Article **“Steps for Updating SMArt Email to support MS OAuth”** for steps on implementing the latest version of **SMArt Email**.

**Below is some additional information and links from Microsoft’s announcement:**

“To be clear, we will start on October 1; this is not the date we turn it off for everyone. We will randomly select tenants, send 7-day warning Message Center posts (and post-Service Health Dashboard notices), then we will turn off Basic Auth in the tenant. We expect to complete this by the end of this year.”

“We're removing the ability to use **Basic authentication** in Exchange Online for Exchange ActiveSync (EAS), POP, IMAP, Remote PowerShell, Exchange Web Services (EWS), Offline Address Book (OAB), Outlook for Windows, and Mac.”

“We are not turning off SMTP AUTH, but we will disable SMTP AUTH in all tenants in which it's not being used.”

“This decision requires customers to move from apps that use basic authentication to apps that use Modern authentication.”

https://docs.microsoft.com/en-us/exchange/clients-and-mobile-in-exchange-       online/deprecation-of-basic-authentication-exchange-online

https://techcommunity.microsoft.com/t5/exchange-team-blog/basic-authentication-deprecation-in-exchange-online-may-2022/ba-p/3301866

https://techcommunity.microsoft.com/t5/exchange-team-blog/basic-authentication-and-exchange-online-september-2021-update/ba-p/2772210