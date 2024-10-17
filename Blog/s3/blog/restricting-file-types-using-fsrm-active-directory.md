---
title: "Restricting File Types Using File Server Resource Manager (FSRM) in Active Directory"
excerpt: "Learn how to restrict the types of files stored in a folder by deploying File Server Resource Manager (FSRM) in Active Directory, blocking audio and video files to save storage space."
publishDate: "October 17, 2024"
tags:
    - File Server Resource Manager
    - FSRM
    - Active Directory
    - File Screening
slug: restricting-file-types-using-fsrm-active-directory
isFeatured: false
seo:
    image:
        src: 'https://image.linnlatt.info/it-support-activedirectory-office365-techskill.jpg'
        alt: "File Server Resource Manager (FSRM) Configuration"
---

![Creating and Managing Users in Office 365](https://cdn-dynmedia-1.microsoft.com/is/image/microsoftcorp/RF-Microsoft-M365-Sizzle_tbmnl_en-us?scl=1 "Hero Image")

:::main{style="color:red"}
!!!Important: The content and graphics in this document are based on material from the JSS IT Support course. I have compiled it for easy future reference, with assistance from ChatGPT.
:::

Organizations often face the challenge of optimizing storage by controlling what types of files can be stored in specific directories. For instance, large media files like audio and video can quickly consume storage space. To address this, I used **File Server Resource Manager (FSRM)**, a powerful tool available in Active Directory, to restrict file types.

In this scenario, I’ll demonstrate how I configured FSRM to block users from saving audio and video files in a shared folder, ensuring efficient use of disk space.



## Step 1: Installing FSRM

To begin with, I installed **File Server Resource Manager** on the server.

### 1. Launch Server Manager  
   Open **Server Manager** and click on **Manage**.

   ![Server Manager](https://www.jobskillshare.org/wp-content/uploads/2022/01/word-image-136.png)

### 2. Add Roles and Features  
   From the **Manage** menu, select **Add Roles and Features**.

   ![Add Roles and Features](https://www.jobskillshare.org/wp-content/uploads/2022/01/word-image-137.png)

   Proceed through the installation wizard. Select the appropriate server and expand **File and Storage Services** → **File and iSCSI Services**.

### 3. Select FSRM Role  
   In the list of roles, check **File Server Resource Manager** and click **Next**. If prompted, click **Add Features**.

   ![Select FSRM](https://www.jobskillshare.org/wp-content/uploads/2022/01/word-image-143.png)

### 4. Complete Installation  
   After reviewing the settings, click **Install** to begin the installation. Once completed, FSRM will be available.

---

## Step 2: Configuring FSRM to Restrict File Types

Now that FSRM is installed, I’ll configure it to block audio and video files from being saved in a specific folder.

### 1. Open File Server Resource Manager  
   In **Server Manager**, click **Tools** and select **File Server Resource Manager**.

   ![File Server Resource Manager](https://www.jobskillshare.org/wp-content/uploads/2022/01/word-image-148.png)

### 2. Access File Screening Management  
   In the FSRM window, expand **File Screening Management** and select **File Screens**.

   ![File Screening Management](https://www.jobskillshare.org/wp-content/uploads/2022/01/word-image-149.png)

### 3. Create a File Screen  
   Right-click **File Screens** and select **Create File Screen**.

   ![Create File Screen](https://www.jobskillshare.org/wp-content/uploads/2022/01/word-image-152.png)

   In the **Create File Screen** dialog box, click **Browse** and navigate to the folder where the restriction should be applied. For this scenario, I selected **C:/Share2/GroupA** as the folder.

   ![Select Folder](https://www.jobskillshare.org/wp-content/uploads/2022/01/word-image-153.png)

### 4. Choose File Screen Template  
   From the **Derive properties from this file screen template** dropdown, select **Block Audio and Video Files**. This template will automatically block common audio and video formats.

   ![File Screen Template](https://www.jobskillshare.org/wp-content/uploads/2022/01/word-image-154.png)

   Click **Create** to apply the file screen.

---

## Step 3: Diagnosing Issues with Event Viewer

If a user attempts to save a restricted file type (e.g., an MP3 or MP4) in the folder, they will see a notification informing them that the action is not allowed. However, if troubleshooting is necessary, the **Event Viewer** can provide additional details.

### 1. Open Event Viewer  
   In **Server Manager**, go to **Tools** and select **Event Viewer**.

   ![Event Viewer](https://www.jobskillshare.org/wp-content/uploads/2022/01/word-image-157.png)

### 2. Check Logs  
   Expand **Windows Logs** and review the **Application** and **System** logs for any errors related to file screening. Look for entries marked in red that may explain why a particular file type was blocked.

   ![Windows Logs](https://www.jobskillshare.org/wp-content/uploads/2022/01/word-image-158.png)

---

## Step 4: Organizational Units vs. Containers

In Active Directory, **Organizational Units (OUs)** offer a way to group objects like users and computers. Unlike generic containers, OUs can have group policies applied to them, making them valuable for managing permissions and configurations within specific parts of an organization.

For example, you can apply a group policy to an OU that restricts file access based on organizational roles.

---

## Step 5: Creating Organizational Units

Let’s see how OUs can be created and used for targeted management in Active Directory.

### Example 1: Creating an OU for Desktops

1. Right-click the domain (e.g., `dcjk.jobskillshare.org`) and select **New** → **Organizational Unit**.

   ![Create OU](https://www.jobskillshare.org/wp-content/uploads/2022/01/word-image-160.png)

2. In the dialog box, name the OU (e.g., “Desktop”) and click **OK**.

   ![Name OU](https://www.jobskillshare.org/wp-content/uploads/2022/01/word-image-161.png)

   The new OU will now appear under the domain. Group policies can be applied to this OU, while generic containers like **Computers** cannot have policies applied.

   ![Desktop OU](https://www.jobskillshare.org/wp-content/uploads/2022/01/word-image-162.png)

### Example 2: Creating an OU for Staff Members

Let’s create another OU called **Staff Members**:

1. Highlight the domain and click the **Create a new organizational unit** button.

   ![Create Staff OU](https://www.jobskillshare.org/wp-content/uploads/2022/01/word-image-163.png)

2. In the dialog box, enter **Staff Members** as the name and click **OK**.

   ![Staff Members OU](https://www.jobskillshare.org/wp-content/uploads/2022/01/word-image-164.png)

   You can now apply a group policy to this OU. For example, the policy could grant users in the **Staff Members** OU access to sensitive financial systems or restricted resources.

   ![OU Applied](https://www.jobskillshare.org/wp-content/uploads/2022/01/word-image-165.png)

---

## Conclusion

By deploying **File Server Resource Manager (FSRM)**, I was able to block specific file types, such as audio and video files, from being stored in a shared folder. Additionally, understanding the difference between **Organizational Units (OUs)** and **containers** in Active Directory provided insights into how policies can be applied more effectively within an organization.

This approach ensures that storage is used efficiently while maintaining control over the types of files that users can store. If you are managing a file server, I highly recommend using FSRM for effective file type management.

