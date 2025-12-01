# Explore your Microsoft 365 Cloud Environment

Creating a path to an organization's digital transformation with Microsoft 365 cloud computing requires a firm foundation. Correct configuration of a Microsoft 365 subscription and Microsoft Entra tenant ensures productivity, collaboration, privacy, compliance, performance, and security.

> **Important**  
> Azure Active Directory (Azure AD) is now Microsoft Entra ID.

---

## Microsoft 365 Subscriptions and Plans

People often use **plan** and **subscription** interchangeably, but they differ:

### **Plan**
- A set of features/services included (e.g., E3, E5).
- Determines apps, security features, and capabilities.

### **Subscription**
- The act of purchasing access to a plan.
- Paid recurring fee.
- Usually includes multiple licenses for multiple users.

---

## Building the Cloud Foundation: Subscription + Tenant

A Microsoft 365 plan provides:
- Office apps (Word, Excel, PowerPoint, Outlook)
- Cloud services (Exchange Online, SharePoint Online, OneDrive, Teams, etc.)

When an organization purchases a Microsoft 365 plan:
- Microsoft automatically **creates a Microsoft Entra tenant**.
- The tenant handles:
  - Authentication
  - Authorization
  - Identity management

### Why people call it a “Microsoft 365 tenant”
Even though it’s technically a Microsoft Entra tenant:
- It is created when buying a Microsoft 365 subscription.
- It manages identities for the Microsoft 365 suite.

### Summary
- **Microsoft 365 subscription** → Paid access to services.
- **Microsoft Entra tenant** → Identity container for those services (resources, URLs, policies, global settings).

---

## Plans That Do *Not* Create a Microsoft Entra Tenant

Some Microsoft 365 plans provide limited Microsoft Entra functionality but **do not create a tenant by themselves**.

Common examples:
- **Enterprise Mobility + Security (EMS) E5**
- **Microsoft 365 Business Basic**
- **Microsoft 365 Business Standard**
- **Microsoft 365 Apps**
- **Office 365 F3**
- **Microsoft 365 F1**

These plans:
- May still use Entra ID for sign-ins.
- Do not include full tenant creation.
- Need a higher-tier plan (E3/E5) for full identity capabilities like Conditional Access or advanced identity protection.

---

## Licenses

### How licensing works:
1. Select a Microsoft 365 plan.
2. Purchase the number of licenses needed (seats/users).
3. Assign licenses in the **Microsoft 365 admin center**.
4. Add/remove licenses as organization needs change.

> **Important:** License allocation may vary depending on the plan and add-ons.

---

## Organizations With Multiple Microsoft Entra Tenants

A Microsoft 365 subscription creates **one tenant**.  
However, organizations can have multiple tenants by purchasing multiple subscriptions.

### Why large organizations use multiple subscriptions:
- **Different user requirements**  
  (different departments need different tools)
- **Licensing flexibility**  
  (mix of E3, E5, F1, contractors, etc.)
- **Compliance/security needs**
- **Mergers & acquisitions**

> **Caution:**  
> Multiple tenants add complexity in provisioning, licensing, and administration.

---

## Tenant Information

During Microsoft 365 sign-up, Microsoft asks for:
- Organization name
- Country/region
- Domain name

Microsoft uses this to create the tenant, e.g.:
https://contoso.onmicrosoft.com


### Admin Access
- Managed via **Microsoft 365 admin center**
- Admins can configure:
  - Users
  - Licenses
  - Domains
  - Security settings

### Additional Notes
- A tenant can have **up to 900 domains**.
- **One subscription → one tenant**
- Multiple subscriptions → multiple tenants

---

## Attributes of a Well-Designed Microsoft Entra Tenant

An organization must configure/manage:

### **Products & Licensing**
- Plans match organizational needs.
- Enough licenses to cover all workers.

### **Networking**
- Correct **DNS domain names**.
- Optimized traffic for:
  - On-site workers
  - VPN remote workers

### **Identity Integration**
If using on-premises AD DS:
- Sync accounts, groups, and objects.
- Ensure correct domain mapping to Exchange mailboxes.
- Assign proper licenses.

### **Identity & Access Management**
- Require passwordless or MFA.
- Use Conditional Access for security.

### **Migration / Hybrid Configuration**
- Move on-premises Office servers and data to the cloud or set up hybrid.

### **Device Management**
Using Intune or Basic Mobility:
- Enroll/manage company devices.
- Configure app management for personal devices.

---

## Example of a Complete Microsoft Entra Tenant Setup

A fully configured tenant includes:
- Microsoft 365 E5 + EMS E5 licenses
- Productivity apps
- Intune device management
- Entra tenant with:
  - Synchronized accounts
  - Domains
  - Conditional Access policies
  - (Groups and objects also exist but not shown)

# Configure Your Microsoft 365 Organizational Profile

Completing your organization's profile is a critical first step when setting up a Microsoft Entra tenant.  
Some required fields (such as **Address line**) can halt the provisioning process if left incomplete.

> **Important**  
> Only users with the **Global Administrator** role can update the organization profile.

---

## Edit Your Organization Profile

Follow these steps to modify your organization’s profile:

1. Go to the **Microsoft 365 admin center**.
2. In the left navigation pane, select **Show all** (ellipsis `...`).
3. Select **Settings > Org settings**.
4. Open the **Organization profile** tab.
5. Choose the appropriate group (e.g., *Custom themes*, *Organization information*).
6. Edit the settings and **Save**.
7. Repeat for all groups as needed.

### Organization Information Group

This section contains your basic company information:
- Organization name  
- Address  
- Phone number  
- Preferred language  
- Country/Region  

---

## Preferred Language Warning

- Determines the language for **all Microsoft communications**.
- At signup, it also sets the default language for **SharePoint Online**.
- Changing it later:
  - ✔️ Future emails from Microsoft use the new language  
  - ❌ SharePoint Online **stays** in the original language (cannot be changed)

---

## Country/Region Warning

- The **Country/Region** value **cannot be changed** after setup.
- It determines:
  - Available services
  - Billing currency and taxes
  - The Microsoft datacenter location supporting your tenant

> **Important**  
> If you enter the wrong country/region, the only fix is to **create a new account** and purchase a new subscription with the correct location.

---

# Update Your Organization’s Theme

Microsoft 365 administrators can create:
- **1 Default theme**
- **Up to 4 custom themes**  
  (assigned to Microsoft 365 Groups)

Theme changes appear in the top navigation bar of the Microsoft 365 suite.

### Steps to Create or Update a Theme

1. Go to **Settings > Org settings**.
2. Select the **Organization profile** tab.
3. Choose **Custom themes**.
4. To add a theme, select **Add theme**.
5. Configure settings under the tabs:
   - **General**
   - **Logos**
   - **Colors**

---

## General Tab

### Default Theme
- Cannot be renamed.
- Applies to all users.
- To delete the default theme, you must delete all other themes first.

You can:
- Prevent users from overriding their theme
- Show user display names

### Group Themes
- Assigned to **Microsoft 365 Groups only**  
  (not security groups, not distribution groups)
- If a user belongs to multiple groups with themes, the **default theme** is used.

Limits:
- Total themes: **5** (1 default + 4 custom)
- Each group theme can be assigned to **up to 5 Microsoft 365 groups**

Only **Global Administrators** may customize themes.

---

## Logos Tab

You can upload:
- Default logo  
- Alternate logo (optimized for dark mode)
- On-click link URL

### Requirements

**Default Logo:**
- HTTPS URL
- Publicly accessible (no authentication)
- File size < 10 KB
- Formats: JPG, PNG, GIF, SVG  
  - SVG resized to 24px height  
  - JPG/PNG/GIF scaled to 200 × 48 px  
  - Aspect ratio always preserved

**Alternate Logo:**
- Same requirements as default
- Optimized for dark theme visibility

**On-Click Link**
- Optional  
- If not provided → defaults to Microsoft 365 home page

> If the logo fails to upload, the URL likely isn’t publicly accessible.

### Contrast Ratio Note
Microsoft recommends **4.5:1** contrast ratio, but you can override the warning and save anyway.

### Responsive Behavior
On smaller screen sizes or window widths, the logo may disappear to prioritize essential header elements.

---

## Colors Tab

Customize colors for your organization theme.

You can modify:
- **Navigation bar color** (top header background)
- **Text and icon color**
- **Accent color**  
  (used on links/buttons on light backgrounds—e.g., Outlook inbox, Microsoft 365 portal)

You may also:
- Reset to default colors

---


  - Domains
  - Conditional Access policies
  - (Groups and objects also exist but not shown)

<img width="1056" height="482" alt="image" src="https://github.com/user-attachments/assets/4959ff01-ddaa-43ea-9f67-82200021e600" />



# Manage your tenant subscriptions in Microsoft 365

Maintaining minimum subscription requirements is essential for an organization to remain functional. Purchasing an insufficient number of licenses can result in implementation delays, while purchasing an excessive number of licenses can result in overspending.

The following screenshot is an example from a tenant with group-based licensing. In this case, all available licenses are already assigned. This situation results in provisioning errors due to the depleted licenses.

> Screenshot from a tenant with group-based licensing and a provisioning error due to depleted licenses.

All active and deprovisioned licenses can be reviewed from the Microsoft 365 admin center. In the left-hand navigation pane, select **Billing** → **Licenses**.  
On the **Licenses** page, select the **Subscriptions** tab.

<img width="1051" height="339" alt="image" src="https://github.com/user-attachments/assets/a97add78-a96e-43ab-b5b1-cbd0261c3ace" />

An administrator can use this page to assign and remove licenses to user accounts. Extra licenses can also be purchased from here.

> **Note:** Purchasing extra licenses changes the monthly billing date for those specific licenses.  
> Example: If the main subscription was purchased on **May 14** and another purchase was completed on **May 15**, the next billing cycle would show subscriptions with due dates of **June 15** and **June 16**, respectively.

All the information about an organization's existing subscriptions, including billing and payment information, is available within the **Billing** group in the Microsoft 365 admin center. This group includes the following pages:

### Billing Pages

- **Purchase services**  
  Enables an organization to compare up to three products at a time and start purchases.

- **Your products**  
  Displays all the plans purchased by an organization. These plans can be maintained from here.

- **Licenses**  
  Provides a summary of subscribed licenses for each plan, including available license counts.

- **Bills and payments**  
  Shows a history of all invoices charged to the organization, payment methods, and billing profiles.

- **Billing accounts**  
  Manages the organization's purchasing relationship with Microsoft—address, contact details, tax information, and agreements.

- **Payment methods**  
  Enables defining payment methods for subscription purchases.

- **Billing notifications**  
  Identifies who receives billing notifications and how each billing statement is delivered.


# Integrate Microsoft 365 with Customer Engagement Apps

One of the key responsibilities of a Microsoft 365 Administrator is managing the company tenant. Administrators must acquire and assign licenses such as Project Online, Visio, Scheduler, and Microsoft Stream. Sometimes, they must also purchase extra capabilities, such as Microsoft Purview eDiscovery (Premium).

Integrating Microsoft 365 with customer engagement apps enhances CRM functions through:

- Easier maintenance  
- Broader availability  
- Better coordination across devices  

Microsoft 365 provides two mechanisms for integration:

1. **Purchase services** (Microsoft 365 admin center)  
2. **Azure Marketplace** (Azure portal)

> **Note:** Azure Marketplace is outside the scope of this training, but included for visibility.

---

## Purchase Services Page (Microsoft 365 Admin Center)

The **Purchase services** page is located under the **Billing** group. It displays add-on services and full suite options, many of which offer a 30-day trial.

At the end of a trial, the subscription expires unless purchased. All features are available during the trial for evaluation.

Organizations use this page for:

### 1. Purchase new products
Examples:  
- Microsoft 365 Business Premium  
- Microsoft 365 Business Standard  
- Microsoft 365 Apps for Business  

### 2. Add-on services  
Examples:  
- Microsoft Teams  
- Power BI  
- Project Online  

### 3. Manage licenses  
Tasks include:  
- Adding or removing licenses  
- Changing license quantity  
- Assigning licenses to users  

### 4. View purchase history  
Shows:  
- Date of purchase  
- Service purchased  
- Amount paid  

### 5. Get product recommendations  
Microsoft offers suggestions based on organizational needs.

---

## Product Comparison

You can compare products by:

1. Selecting the **Compare** checkbox for the products.  
2. Selecting the **Compare** button.

The comparison page includes:

- **Product overview**
- **Features comparison** (side-by-side)
- **Pricing comparison**
- **Technical specifications**
- **Customer reviews**

This helps organizations evaluate and select the most suitable product.

---

## Assign Services

Two ways to assign purchased services:

1. Purchase the add-on → go to **Users** → assign license  
2. Use the **Assign to** option after claiming the license

---

## Azure Marketplace (Azure Portal)

Azure Marketplace enables IT admins to control third-party apps that users can deploy and purchase. Only approved apps can be deployed within the tenant.

There are **two marketplaces**:

### 1. Azure Marketplace
- Open to all Azure users  
- Thousands of apps (Compute, DevOps, AI, ML, etc.)  
- Users can find, try, and buy apps  

### 2. Private Azure Marketplace
- Tenant-level governance  
- Admins control which apps are approved  
- Users can only deploy approved solutions  
- Microsoft apps are automatically included  

### What is a Collection?

A **collection** is a list of approved products available across subscriptions.  
The **Default Collection**:

- Is created automatically  
- Has tenant-wide scope  
- Cannot be renamed or deleted  

---

## Azure Marketplace vs Private Azure Marketplace

| Benefit | Azure Marketplace | Private Azure Marketplace |
|--------|-------------------|---------------------------|
| Discover Microsoft & partner apps | Yes | Yes |
| Control deployment of partner (ISV) apps | Limited | Yes |
| Control deployment at plan/SKU level | No | Yes |
| Create custom collections for subscriptions | No | Yes |
| Users can request admin approval | No | Yes |

> **Note:**  
> Apps from Microsoft and endorsed Linux vendors are always approved. Only ISV apps can be controlled via Private Azure Marketplace.

---

## Steps to Create a Private Azure Marketplace

1. Assign the **Marketplace Admin** role  
2. Create the private Azure Marketplace (initially disabled, includes Default Collection)  
3. Customize collections (add approved apps)  
4. Enable the private Azure Marketplace  

After creation, Microsoft and endorsed Linux apps are included automatically.

> **Important:**  
> Private Azure Marketplace is **tenant-level**. Once enabled, it applies to all users. Collections help manage approvals at the **subscription level**.

---

## Additional Reading

- Add-ons and services  
- Govern and control using Private Azure Marketplace
  

# Configure Tenant-Level Sharing Settings for SharePoint and OneDrive

SharePoint and OneDrive are cloud-based platforms used to store, share, and collaborate on files and folders in Microsoft 365. Their external sharing features allow users to share content with people outside the organization (partners, vendors, clients, customers). Sharing also works across multiple Microsoft 365 subscriptions.

> **Tip:**  
> External sharing is turned on by default. You may want to turn it off globally first until your organization decides how to use it.

This section focuses on **organization-level sharing settings**.  
For site-level sharing, see **Change sharing settings for a site**.  
For OneDrive user-level sharing, see **Change the external sharing setting for a user's OneDrive**.

---

## Organization-Level External Sharing Settings

SharePoint has sharing settings at:
- **Organization level**
- **Site level**

To allow **any** site to share externally, you must first enable it **at the organization level**.  
OneDrive sharing can be the same or **more restrictive** than SharePoint.

Only **Global admins** and **SharePoint admins** can configure these settings.

### How to Access the Sharing Page

1. In the **Microsoft 365 admin center**, go to **Admin centers → SharePoint**.  
2. In the SharePoint admin center, select **Policies → Sharing**.

You will find these sections:

- External sharing  
- More external sharing settings  
- File and folder links  
- Advanced settings for Anyone links  
- Other settings  

---

## External Sharing Options

> **Important:**  
> Microsoft Entra external collaboration settings impact who can invite guests.

SharePoint and OneDrive offer **four main sharing options**:

| Option | Description |
|-------|-------------|
| **Anyone** | Allows sharing via unauthenticated links. Allows site sharing with guests who authenticate. Supports link expiration and view-only restrictions. Required for file requests. |
| **New and existing guests** | Requires guests to sign in using a Microsoft account or verification code. Guests not yet in the directory are added after sign-in. |
| **Existing guests** | Allows sharing only with guests already in your directory. |
| **Only people in your organization** | Disables external sharing entirely. |

> **Note:**  
> Even if organization-level sharing allows external sharing, new sites may not allow it by default.

### Best Practice
Store confidential information in **sites with external sharing turned off**.

---

## More External Sharing Settings

This section allows more granular control.

### Options

- **Limit external sharing by domain**  
  - Allow or block up to **5000 domains** (format: `domain.com`).  
  - Can also be configured via PowerShell (`Set-SPOTenant`).

- **Allow only specific security groups to share externally**

- **Guests must sign in using the same account invitations were sent to**

- **Allow guests to share items they don't own**

- **Guest access expiration**  
  Example: Access expires after X days unless renewed.

- **Verification code reauthentication frequency**

---

## File and Folder Links (Default Link Type)

Choose the default link behavior for your organization:

- **Specific people**  
  Most restrictive. Supports external sharing with specific users.

- **Only people in your organization**  
  Forwarded links work for any internal user.

- **Anyone with the link**  
  Only available if organization-level setting allows “Anyone”.  
  Forwardable internally and externally, but cannot track who accessed files.

> **Important:**  
> If a site allows only authenticated guest sharing, the default becomes **Only people in your organization**, even if "Anyone" is set at the org level.

---

## Advanced Settings for “Anyone” Links

- **Link expiration**  
  Require expiration and set max number of days.

- **Link permissions**  
  - View only  
  - View + Edit  
  Required for **file requests**.

---

## Other Settings

### Options

- **Show owners the names of people who viewed their files in OneDrive**  
  - Enabled by default.  
  - Viewer info still recorded for auditing even if disabled.

- **Allow site owners to display viewer names in SharePoint**  
  - Enabled at org level by default, *off* at site level for existing sites.  
  - Must be on at both levels.

- **Use short links for sharing files and folders**

> **Note:**  
> Viewer history includes past data even if the feature is turned off and then back on.



# Configure Tenant-Level Settings for Microsoft Teams

As a Microsoft 365 administrator, you can configure organization-level tenant settings in Microsoft Teams. These settings affect how users and guests access and use Teams features.

---

## Organization-Level Settings Overview

| Setting | Description |
|---------|-------------|
| **Guest access** | Enable or disable guest access. Guests can participate in chats, calls, meetings, and channels but have limited access to other resources. Control domains and feature access for guests. |
| **Teams upgrade** | Control the transition from Skype for Business to Teams. Options: Islands, Teams Only, Skype for Business Only, etc. Determines which app is used for chat, calls, and meetings. |
| **Teams settings** | Customize app setup, meetings, messaging, live events, voice, and device policies. Each policy defines permissions and user experience. |
| **Teams apps** | Manage which apps users can access. Approve, upload, block, or uninstall apps. Create **app permission policies** (allow/block) and **app setup policies** (pinned/default apps). |
| **Teams analytics and reports** | Monitor usage and performance. Reports include user activity, device usage, live event usage, and call quality. |

---

## Teams Meeting Settings

Teams meeting settings are divided into:

- **Meeting policy settings** – control user experience and permissions per meeting  
- **Meeting configuration settings** – apply to all meetings organization-wide  

### Meeting Policy Settings

Meeting policies can be assigned to users, groups, or the entire organization. Key settings include:

- **Allow scheduling private meetings** – schedule meetings not published to channels with specific invitees.  
- **Allow Meet Now in channels** – start instant meetings in channels.  
- **Allow channel meeting scheduling** – schedule meetings published to channels.  
- **Allow IP video** – enable users to share video during meetings.  
- **Allow screen sharing** – enable sharing of screen or app windows.  
- **Allow transcription** – enable real-time audio transcript.  
- **Allow cloud recording** – record and store meetings in the cloud.  
- **Allow live captions** – show real-time captions.  
- **Media bit rate (Kbps)** – set maximum data rate for audio/video traffic.  
- **Allow live events** – enable creation/hosting of large-scale events (up to 10,000 attendees).  

---

### Meeting Configuration Settings

Configuration settings apply to all meetings in the organization:

- **Designated presenter role mode** – Who can be a presenter: Everyone, Organization, Organization + federated, or Organizer only.  
- **Who can bypass the lobby** – Options: Everyone, Organization, Organization + federated, Organization + trusted, People I invite, Only me.  
- **Announce when callers join or leave** – Play sound when participants join/leave.  
- **Allow dial-in users to bypass the lobby** – Dial-in users join without waiting.  
- **Automatically admit people** – Auto-admit options: Everyone, Organization, Organization + federated, Organization + trusted.  
- **Allow anonymous users to join a meeting** – Enable non-signed-in users to join with a name.  
- **Allow users to chat privately** – Send private messages during meetings.  
- **Allow users to send reactions** – Send emoji reactions like thumbs up or heart.  
- **Allow users to view shared notes** – Access meeting notes during and after meetings.  



# Complete your tenant configuration in Microsoft 365

Finalizing your Microsoft 365 tenant configuration is a crucial step in ensuring a smooth transition for users and maintaining security and compliance. A well-structured checklist can help administrators verify that all necessary components are correctly configured and functioning.

---

## Common tasks for tenant configuration

While specific configurations may vary depending on your organization's needs, the following are common steps to complete your Microsoft 365 tenant setup:

- **User and Mailbox Migration:** Ensure all users are migrated and have fully functional mailboxes, with appropriate data migration where applicable.
- **System Resources and Permissions:** Configure and assign necessary permissions to system resources.
- **Domain Configuration:** Transfer and verify custom domains (vanity domains).
- **Device Management:** Enroll Windows 10 and 11 devices into Microsoft Intune and configure co-management if using Microsoft Endpoint Configuration Manager.
- **Mobile Device Governance:** Implement governance policies for mobile devices.
- **DNS Records and Mail Flow:** Update and verify DNS records globally and configure policies to protect email communications.
- **Identity Synchronization:** Set up and validate Microsoft Entra Connect Sync, if in use.
- **Multifactor Authentication (MFA):** Enable MFA for added security.
- **Security and Compliance Enhancements:** Implement Conditional Access policies, disable legacy authentication, and configure audit logging.
- **Data Protection:** Configure Data Loss Prevention (DLP) policies and enable Azure Information Protection (AIP) to classify and protect sensitive information.
- **Monitoring and Reporting:** Use tools such as Microsoft Secure Score to track and improve security configurations.
- **Regular Security Reviews:** Review and update security settings and governance policies periodically.

---

## Verifying tenant readiness

To confirm your Microsoft 365 environment is properly configured, use:

- **Microsoft Remote Connectivity Analyzer:** Checks DNS records and mail flow settings.
- **Microsoft Support and Recovery Assistant (SARA):** Diagnoses and resolves common connectivity issues.

---

## Other consideration: tenant-to-tenant migration

> **Note:**  
> Tenant-to-tenant migration refers to the process of transferring data and configurations from one Microsoft 365 tenant to another, commonly required during mergers, acquisitions, or business restructurings.  
> Given the complexity and specialized nature of such migrations, they are out of scope for this training.  
> For more details, please refer to the [Microsoft 365 tenant-to-tenant migrations article](https://learnrators can ensure a smooth and secure Microsoft 365 tenant setup by following a structured checklist and verifying key configurations. Regular reviews and proactive monitoring help maintain performance, security, and compliance.


