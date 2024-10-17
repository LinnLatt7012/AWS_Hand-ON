---
title: "Managing Office 365 Multi-factor Authentication"
excerpt: "A step-by-step guide to setting up and managing multi-factor authentication in Office 365, enhancing security for user accounts."
publishDate: "October 17, 2024"
tags:
    - Office 365
    - Multi-Factor Authentication
    - IT Support
slug: managing-office-365-multi-factor-authentication
isFeatured: false
seo:
    image:
        src: 'https://image.linnlatt.info/it-support-activedirectory-office365-techskill.jpg'
        alt: "Managing Office 365 Multi-factor Authentication"
---

![Creating and Managing Users in Office 365](https://cdn-dynmedia-1.microsoft.com/is/image/microsoftcorp/RF-Microsoft-M365-Sizzle_tbmnl_en-us?scl=1 "Hero Image")

:::main{style="color:red"}
!!!Important: The content and graphics in this document are based on material from the JSS IT Support course. I have compiled it for easy future reference, with assistance from ChatGPT.
:::

# **Managing Office 365 Multi-factor Authentication**

In today’s digital landscape, security is a top priority. One of the best ways to enhance security for user accounts in Office 365 is by enabling **Multi-factor Authentication (MFA)**. In this post, I'll walk through how I learned to configure MFA using the Office 365 Admin Center, ensuring an extra layer of protection for user data.

## Key Highlights

By the end of this session, I successfully:

- Enabled multi-factor authentication for users in Office 365.
- Configured MFA options such as verification methods.
- Tested MFA setup through an InPrivate browser session.

> **Note:** The steps in this lab can change frequently due to updates in Office 365. Always refer to Microsoft Learning’s most recent lab guides for accurate instructions.

---

## Steps to Enable Multi-factor Authentication in Office 365

Here’s a step-by-step guide on how I enabled multi-factor authentication (MFA) for users:

### 1. **Join the Office 365 Domain**

   Start by joining the Office 365 domain from the PLABWIN101 virtual machine. Once done, open Microsoft Edge (or any browser) and go to [https://portal.office.com/](https://portal.office.com/).

   ![Join Office 365 Domain](https://www.jobskillshare.org/wp-content/uploads/2022/02/word-image-91.png)

### 2. **Sign in to Office 365**

   Sign in using your trial account that you created in the previous lab.

   ![Sign in Office 365](https://www.jobskillshare.org/wp-content/uploads/2022/02/word-image-92.png)

### 3. **Access the Admin Center**

   Once logged in, select **Admin** from the Office 365 dashboard.

   ![Admin Center](https://www.jobskillshare.org/wp-content/uploads/2022/02/word-image-93.png)

### 4. **Navigate to Settings**

   In the Admin Center, click on **Show all**, then expand **Settings**, and click on **Org Settings**.

   ![Org Settings](https://www.jobskillshare.org/wp-content/uploads/2022/02/word-image-96.png)

### 5. **Search for Multi-factor Authentication**

   In the **Org Settings** menu, use the **Search all settings** bar to type "Multi-factor authentication," and select the suggested option.

   ![Search MFA](https://www.jobskillshare.org/wp-content/uploads/2022/02/word-image-97.png)

### 6. **Configure MFA for Users**

   In the multi-factor authentication settings, click **Configure multi-factor authentication**. Select the user for whom you want to enable MFA and click **Enable**.

   ![Configure MFA](https://www.jobskillshare.org/wp-content/uploads/2022/02/word-image-100.png)

### 7. **Service Settings Configuration**

   Switch to the **Service Settings** tab. Under **verification options**, verify that the **Call to phone** checkbox is not selected. Save the settings and click **Close**.

   ![Service Settings](https://www.jobskillshare.org/wp-content/uploads/2022/02/word-image-103.png)

### 8. **Test the MFA Setup**

   To ensure the MFA setup is working, open a new **InPrivate** window in Microsoft Edge. Go to [https://portal.office.com/](https://portal.office.com/) and log in using the account you enabled MFA for.

   ![InPrivate Browser](https://www.jobskillshare.org/wp-content/uploads/2022/02/word-image-105.png)

### 9. **Follow the MFA Prompt**

   After logging in, you will see a prompt for multi-factor authentication. There will be no “Skip for 14 days” option since MFA is enabled.

   ![MFA Prompt](https://www.jobskillshare.org/wp-content/uploads/2022/02/word-image-107.png)

### 10. **Install Microsoft Authenticator App**

   Download the **Microsoft Authenticator** app from the Play Store or App Store on your phone. Once installed, follow the steps to **scan the QR code** provided on the Office 365 portal.

   ![Install App](https://www.jobskillshare.org/wp-content/uploads/2022/02/word-image-108.png)

### 11. **Add the Account to the App**

   In the app, tap the top-right corner and select **Add Account**. Choose **Work or School Account** and use the **Scan QR Code** option to link your account.

   ![Add Account](https://www.jobskillshare.org/wp-content/uploads/2022/02/word-image-111.png)

### 12. **Complete MFA Setup**

   After scanning the QR code, the account will be added to the app. Follow the prompts on the Office 365 portal to complete the setup.

   ![Complete MFA](https://www.jobskillshare.org/wp-content/uploads/2022/02/word-image-113.png)

## Conclusion

Setting up multi-factor authentication (MFA) in Office 365 adds an extra layer of security, which is crucial for protecting user accounts and sensitive data. With these steps, I successfully enabled and configured MFA, and tested it using a live login session. If you encounter issues, remember to double-check your settings, such as removing unnecessary verification options like “Call to phone.”
