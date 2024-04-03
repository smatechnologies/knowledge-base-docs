---
sidebar_label: 'Steps For Updating SMArt Email to Support MS OAuth'
hide_title: 'true'
---

## Steps For Updating SMArt Email to Support MS OAuth

The **SMArt Email** application will be registered with the **SMATechnologies** Microsoft tenant.

* Accept the **SMArt Email** application as an enterprise application in your organization's Microsoft tenant.
* Install the latest version of the **SMArt Email** connector*
    * Select version **20** or above
    * Installation of the **SMArt Email** connector can be managed with the **OpCon Web Installer** (OWI)* application.
* Finalize the setup by running the application (SMArtEmail.exe) from the command line with the arguments:
    * **Initial Admin Setup** – run the application with arguments
        * `--msal –-renewMsalToken`
        * This will open a browser for you to grant permissions. If available, check the box that grants the permissions to everyone else in your organization.
        * Once this step has been completed, running the application with the arguments below will no longer require the browser:
            * `--msal --renewMsalToken –-renewTokenSilent`
    * **Admin Grants access to other users** – run the application with the arguments
        * `--msal --renewMsalToken --doNotSaveAccount`
        * This will open a browser for you to grant permissions. If available, check the box that grants the permissions to everyone else in your organization.
        * Run the application with the arguments `--msal –-renewMsalToken` which will open a browser for you to select an account.
        * Once these steps have been completed, running the application with the arguments below will no longer require the browser
            * `--msal --renewMsalToken –-renewTokenSilent`
    * **Checking Email**
        * Configure settings for processing emails
        * Run the application with the argument `--msal`

*The **OWI** application can be downloaded from these locations: SMA Public FTP Site -OR- Github