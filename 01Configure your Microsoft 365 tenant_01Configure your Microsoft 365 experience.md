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

