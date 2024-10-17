---
title: "Learning Active Directory: Centralized Management and User Support"
excerpt: "A deep dive into Active Directory and Centernalized management, covering user management, troubleshooting common issues, and best practices for IT administrators."
publishDate: "October 14, 2024"
tags:
    - Active Directory
    - IT Support
slug: learning-active-directory-centralized-management
isFeatured: true
seo:
    image:
        src: 'https://image.linnlatt.info/it-support-activedirectory-office365-techskill.jpg'
        alt: "Active Directory and Office 365 Management"
---
![Active directory management image](https://image.linnlatt.info/it-support-activedirectory-office365-techskill-d1.jpg "Hero Image")

:::main{style="color:red"}
Note!!! Content and assistance provided with the help of ChatGPT, an AI language model by OpenAI.
:::

## Learning Active Directory: Centralizing User and Computer Management

One of the most important concepts I've been exploring recently is **Active Directory (AD)**—a Microsoft service that helps manage users, computers, policies, and much more in an organization. It makes administration across a network much easier by centralizing control.

Here's a breakdown of some key concepts and steps I've learned while working with Active Directory.

### **Key Terminology**:

- **Domain**: A network that has an AD setup. This network can have multiple users and computers all managed centrally.
- **Domain Controller (DC)**: The server that has full control over the domain. It stores AD data and manages the interactions between users and the domain.
- **Server Windows**: The operating system running on the domain controller.

### **Checking if a Machine is Server or Client**

To quickly find out if a machine is a server or client:

1. **Right-click on "This PC"** > Click **"Properties"** > Check the **Windows specification**.

   Or, you can open **Command Prompt (cmd)** and type `winver` to get the Windows version and details.

### **Joining a Computer to the Domain**

This is one of the first things I learned: adding a computer to a domain. The steps are fairly simple:

1. Go to **Computer** > **System** > Click on **Rename this PC (Advanced)** on the right side of the display.
2. Choose **Change**, then switch from the **workgroup** to the **domain** and type the domain name (e.g., `company.local`).

### **Setting a Static IP Address**

In certain setups, it's important to assign a static IP to a computer:

1. Navigate to **Network Connections** > **Right-click Ethernet** > **Properties**.
2. Choose **IPv4** > Click on **Properties**, then manually set the IP address.
3. Don't forget to set the domain controller as the DNS server.

---

## Common Active Directory Support Tickets

Here are some of the most common support tickets I’ve encountered, and how to resolve them. This includes both GUI and PowerShell/Command-line solutions, which I've found incredibly useful.

### **Ticket 1: User Account Lockout**

**Issue**: A user can't log in because their account is locked.
**Resolution Steps**:

1. Verify the user's identity.
2. Check their lockout status in AD.
3. Unlock the account using **Active Directory Users and Computers**.
4. Advise the user to reset their password afterward.

**PowerShell Solution**:

```powershell
Unlock-ADAccount -Identity username
```

**Best Practices**:

- Educate users on account lockout policies to prevent repeated lockouts.
- Encourage users to avoid multiple failed login attempts.

### **Ticket 2: Password Reset**

**Issue**: A user needs to reset their password.
**Resolution Steps**:

1. Verify the user's identity.
2. Generate a temporary password.
3. Reset the password in AD, and inform the user to change it at login.

**PowerShell**:

```powershell
Set-ADAccountPassword -Identity username -NewPassword (ConvertTo-SecureString -AsPlainText "NewPassword123" -Force)
```

**CMD**:

```bash
net user username NewPassword123
```

**Best Practices**:

- Advise users to create strong, memorable passwords.
- Consider implementing self-service password reset tools to reduce ticket volume.

### **Ticket 3: Adding a User to a Group**

**Issue**: A user needs access to a specific resource or system.
**Resolution Steps**:

1. Verify the access request and permission.
2. Add the user to the required AD group.

**PowerShell**:

```powershell
Add-ADGroupMember -Identity "GroupName" -Members username
```

**CMD**:

```bash
net localgroup GroupName username /add
```

**Best Practices**:

- Regularly review group memberships to maintain security.
- Limit permissions to only what’s necessary (principle of least privilege).

### **Ticket 4: User Account Creation**

**Issue**: Creating a new account for a user.
**Resolution Steps**:

1. Gather the required details (full name, department, etc.) from HR.
2. Create the account in AD and assign the necessary permissions.

**PowerShell**:

```powershell
New-ADUser -Name "FullName" -GivenName "FirstName" -Surname "LastName" -SamAccountName "username" -UserPrincipalName "username@domain.com" -Path "OU=Users,DC=domain,DC=com" -AccountPassword (ConvertTo-SecureString -AsPlainText "Password123" -Force) -Enabled $true
```

**Best Practices**:

- Ensure consistency by using a standardized account creation process.

### **Ticket 5: Account Deactivation**

**Issue**: Deactivating an account when an employee leaves.
**Resolution Steps**:

1. Verify with HR that the user has left the company.
2. Deactivate the account in AD.
3. Revoke access to all systems.

**PowerShell**:

```powershell
Disable-ADAccount -Identity username
```

**Best Practices**:

- Use a checklist to ensure no step is missed during the deactivation process.
- Regularly audit AD for inactive accounts.

### **Ticket 6: Group Policy Issues**

**Issue**: A Group Policy Object (GPO) is not applying properly.
**Resolution Steps**:

1. Ensure the user is in the correct Organizational Unit (OU).
2. Check the GPO links and inheritance.
3. Force a Group Policy update using `gpupdate /force`.
4. Verify the policy using `gpresult /r`.

**CMD**:

```bash
gpupdate /force
gpresult /r
```

**Best Practices**:

- Always test GPOs before deploying them to production environments.
- Regularly review and update GPOs to reflect organizational changes.

### **Ticket 7: User Name Change**

**Issue**: A user needs their name updated in Active Directory due to a legal name change.
**Resolution Steps**:

1. Receive the legal name change documentation from HR.
2. Update the user's first and last name in Active Directory.
3. Ensure any associated email addresses or user attributes are updated to reflect the change.
4. Notify the user and HR once the changes are complete.

**PowerShell**:

```powershell
Set-ADUser -Identity username -GivenName "NewFirstName" -Surname "NewLastName"
```

**Best Practices**:

- Maintain a record of name changes for auditing and compliance purposes.
- Communicate changes promptly to all relevant departments and the user to avoid confusion or access issues.

### **Ticket 8: Account Permission Issues**

**Issue**: A user cannot access a specific resource due to insufficient permissions.
**Resolution Steps**:

1. Verify the user’s access request and determine the required permissions.
2. Check the user's current group memberships and access rights.
3. Modify the permissions or group memberships in AD to grant the required access.
4. Inform the user of the changes.

**PowerShell**:

```powershell
Add-ADGroupMember -Identity "ResourceGroupName" -Members username
```

**CMD**:

```bash
net localgroup ResourceGroupName username /add
```

**Best Practices**:

- Review user permissions regularly to ensure they are appropriate for their role.
- Apply the **principle of least privilege**—grant users only the permissions they need to perform their jobs.

### **Ticket 9: Password Expiry**

**Issue**: A user’s password has expired, and they are unable to log in.
**Resolution Steps**:

1. Verify the user’s identity before proceeding.
2. Generate a temporary password and reset the password in Active Directory.
3. Inform the user about the temporary password and instruct them to change it immediately after logging in.

**PowerShell**:

```powershell
Set-ADAccountPassword -Identity username -NewPassword (ConvertTo-SecureString -AsPlainText "TemporaryPassword123" -Force)
```

**CMD**:

```bash
net user username TemporaryPassword123
```

**Best Practices**:

- Implement a password expiration notification policy that informs users before their passwords expire.
- Encourage regular password updates to enhance security.

### **Ticket 10: Incorrect User Details**

**Issue**: A user’s information (e.g., name, department, email) is incorrect in Active Directory.
**Resolution Steps**:

1. Confirm the correct details with the user.
2. Update the user’s information in Active Directory, ensuring that all associated attributes (like email) are correctly updated.
3. Notify the user once the changes are made.

**PowerShell**:

```powershell
Set-ADUser -Identity username -GivenName "CorrectFirstName" -Surname "CorrectLastName" -EmailAddress "correctemail@domain.com"
```

**Best Practices**:

- Keep user information in AD accurate and up to date.
- Create a process for users to request updates to their information to streamline this task.

---

## Final Thoughts: Key Takeaways from My AD Experience

Working with **Active Directory** has taught me the importance of **centralized management** in a network environment. Whether it's resetting passwords, unlocking accounts, or managing user groups, AD allows for efficient control over network resources.

Some tips I’ve learned:

- **Use PowerShell**: While the graphical interface is useful, PowerShell commands are often quicker and more flexible, especially for bulk operations.
- **Always verify identity**: Whether resetting a password or unlocking an account, confirming user identity is a critical security step.
- **Follow best practices**: Implementing password policies, the principle of least privilege, and regular audits keeps the network secure.

I'm excited to continue learning more about Active Directory and network management. Each troubleshooting ticket provides an opportunity to deepen my knowledge and improve my problem-solving skills.

---
