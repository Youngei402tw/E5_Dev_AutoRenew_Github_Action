# **E5_Dev_AutoRenew_Github_Action**

This fork of MSO_E5_Dev_AutoRenew added a feature to update the refresh token for rclone, so that there is no need to reconfig after 90 days of in activity.
It works by zipping rclone.conf in to the repo, after rclone read rclon.conf, delete the config folder. rclone.conf will be automatically updated, finally the updated rclone.conf will be zipped and upload on to the repo. Making the config process automatically done.

E5_Dev_AutoRenew_Github_Action is a Python application based on Git Actions that uses Microsoft Graph API to activate Microsoft Office 365 E5 Developer Trail membership auto-renewal automatically. This guide will provide you with easy-to-understand steps for setting up and running the application.

### Special Notes/Thanks ###
* Original version address: [https://github.com/kylierst/MSO_E5_Dev_AutoRenew_REVISION_2](https://github.com/kylierst/MSO_E5_Dev_AutoRenew)
* Thanks to Ken5998 for code improvements and fix job skipping
* Thanks MSO for original code

## **Prerequisites**

- A GitHub account
- An existing or new Microsoft Developer E5 account with trial Subscription
- An Azure Portal account
- Basic knowledge of GitHub, Python, and Azure Portal

## **Setup Steps (Encrypted Secure Version)**

!DO NOT FORK THIS REPO, INPORT IT WITH URL TO PREVENT ACCOUNT BAN FROM GITHUB!

1. Setup rclone with onedrive, make sure that the name of config should be e5
2. zip rclone.conf, check "ZIP Legacy Encryption" or else "unsupported compression method 99" will appear. Upload the zip file to this repo.
3. Set the password for rclone.zip in settings→Secrets→New repository secret
    - Name: **`PASSWD`** Value：**`your_zip_password`**
4. Goto the project setting again and choose Actions menu and scroll down until you see **Workflow permissions click Read and write permission option**
5. Go to your personal settings page on GitHub, select Developer settings > Personal access tokens > Generate new token.
    - Set the name to **`GITHUB_TOKEN`**.
    - Check the options **`repo`**, **`admin:repo_hook`**, and **`workflow`**.
    - Generate the token.
6. Click on the star button at the top right corner of the page to call it once.
7. Click on the Actions tab above to see the log of each run and check if the API is called correctly and if there are any errors.

## **Additional Information**

- The default setting is to run three rounds every six hours from Monday to Friday. You can modify your own crontab to change the frequency and time.
- If you need to modify the API calls, you can check the Graph Explorer at **[https://developer.microsoft.com/graph/graph-explorer/preview](https://developer.microsoft.com/graph/graph-explorer/preview)**.
- The GitHub Action provides a virtual environment with 2-core CPU, 7 GB RAM memory, and 14 GB SSD hard disk space.
- Each repository can only support 20 concurrent calls.
