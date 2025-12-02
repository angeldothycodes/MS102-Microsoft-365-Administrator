# Determine the User Identity Model for Your Organization

To plan user identities, you must first understand the different types of Microsoft 365 user identities: **Cloud identities**, **Synchronized identities**, and **Federated identities**.  
An organization can choose to maintain identities only in Microsoft 365 or integrate identities with its on-premises Active Directory.

<img width="986" height="568" alt="image" src="https://github.com/user-attachments/assets/a651584b-553c-45fc-8317-8906473103b5" />


---

## Cloud Identities

A **cloud identity** is a user account that only exists in **Microsoft Entra ID**.

> **Important**  
> Azure Active Directory (Azure AD) is now Microsoft Entra ID.

While an organization can create a cloud identity with the same name as an on-premises AD DS account, there is **no link** between the two.  
Admins create cloud identities through the Microsoft 365 admin center.  
Most small organizations use cloud identities because they don’t need to maintain on-prem AD.

---

## Synchronized Identities

A **synchronized identity** is a user that exists in **on-prem AD DS** and also in **Microsoft 365**, with a link between them.  
Any changes made on-prem are synchronized to Microsoft 365.

Organizations can synchronize identities using:

- **Microsoft Entra Connect Sync**
- **Microsoft Entra Cloud Sync**

On-prem AD DS becomes the **authoritative source** for most information.  
Only a small set of M365 attributes sync back to AD DS.

### Authentication for Synchronized Identities

- By default, authentication happens in **Microsoft 365**.
- If **Pass-Through Authentication (PTA)** is enabled, authentication is done **directly against on-prem AD**, bypassing Microsoft 365.

If PTA **is not enabled**, Microsoft 365 evaluates the username/password with no dependency on on-prem environments.

---

## Federated Identities

A **federated identity** is authenticated by an external **Identity Provider (IdP)**.  
When a user accesses a federated service, Microsoft Entra ID redirects authentication to the trusted IdP.

### Federation Setup Involves:

- **Configuring relying party trust**
- **Exchange of metadata** (certificates, endpoints)
- **Trust policy configuration**, such as:
  - Accepted claims and attributes  
  - Rules for handling authentication  
  - Security requirements  

Common IdPs include **Active Directory Federation Services (AD FS)**.

After authentication, the IdP returns a **security token** with user claims, and Microsoft Entra validates it.

### Pros and Cons

Implementing federation used to require deploying AD FS, adding complexity.  
With Entra Connect Sync and Cloud Sync, much of this infrastructure is simplified.

Because authentication depends on AD FS availability, on-prem outages (like internet loss) can cause Microsoft 365 authentication failures—unless AD DS + AD FS are hosted redundantly in Azure.

### Main Benefit

- **Single Sign-On (SSO)** — users logged into domain-joined devices automatically authenticate to Microsoft 365.
- Uses **on-prem password and lockout policies**.

---

# Determining the Best Model

Each identity model has advantages and disadvantages.  
Use the table below to determine which fits your organization.

---

## Identity Model Comparison

| Model | Cloud Identity | Synchronized Identity | Federated Identity |
|-------|----------------|------------------------|---------------------|
| **Definition** | User account exists only in Microsoft 365 | User exists in AD DS and an identical user exists in Microsoft 365 | Synchronized user account authenticated via AD FS |
| **Best for…** | Small/medium orgs or organizations not needing on-prem AD | Orgs already running on-prem AD and planning to move to cloud | Orgs that need centralized authentication or special sign-in (like ID cards) |
| **Greatest Benefit** | Simple; no extra tools needed | Same Sign-In; manage identities in one place | Full SSO; manage identities in one place |



# Create User Accounts in Microsoft 365

Depending on an organization's needs, user accounts can be provisioned using the following methods:

---

## Methods for Creating User Accounts

### 1. Microsoft 365 Admin Center
A simple web interface for individually creating and managing:
- Users  
- Licenses  
- Permissions  

Also available as the **Microsoft 365 admin app** for mobile devices.

---

### 2. Import Multiple Users (CSV)
Allows bulk import of users using a **CSV file**.

---

### 3. Windows PowerShell
Use cmdlet/script-based commands to create and manage users.

> **Note:**  
> Azure AD, Azure AD Preview, and MSOnline PowerShell modules are deprecated.  
> **Microsoft Graph PowerShell** is the module to use for Microsoft Entra ID and Microsoft 365.

---

### 4. Directory Synchronization
Requires provisioning and managing users via on-premises **Active Directory**.  
Synchronization tools:

- **Microsoft Entra Connect Sync**  
- **Microsoft Entra Cloud Sync** (does *not* support Exchange hybrid)

Organizations using directory sync must create users **on-premises**, not in Microsoft 365 admin center or PowerShell.

---

# Creating Users with Microsoft 365 Admin Center

This is the simplest method for creating one or more user accounts.

### Steps:

1. Sign in to **Microsoft 365 admin center**.
2. In the left navigation, select **Users > Active users**.
3. Select **Add a user**.
4. On **Set up the basics**, enter user and password info. Choose the correct domain.
5. On **Assign product licenses**, select licenses.
6. On **Optional settings**, assign roles.
7. On **Review and finish**, verify all information and select **Finish adding**.

---

# Creating Users with Import Multiple Users (CSV)

### Steps:

1. In **Active users**, select **Add multiple users**.
2. Upload the CSV file.
3. Review validation results (fix any errors shown in the log).
4. On **Set user options**, configure:
   - Sign-in status  
   - Location  
   - Licenses  
5. On **View your results**, choose email recipients for results.  
   > Recommended: include your own email to distribute temporary passwords.

---

# Creating Users with Windows PowerShell

Many administrators prefer PowerShell for automation and bulk tasks.

### Install Required Modules

```powershell
Install-Module Microsoft.Graph -Scope CurrentUser
Import-Module Microsoft.Graph.Identity.DirectoryManagement
Connect-MgGraph -Scopes 'User.ReadWrite.All'
```


# Create a New User

Minimum required properties must be provided, including the user’s password.

Example template:

$PasswordProfile = @{ Password = 'user password' }

New-MgUser `
  -UserPrincipalName username@domainname `
  -DisplayName 'Firstname Lastname' `
  -GivenName 'Firstname' `
  -Surname 'Lastname' `
  -PasswordProfile $PasswordProfile `
  -AccountEnabled `
  -MailNickName 'emailalias'


Example: Create a User for Allan Deyoung:
$PasswordProfile = @{ Password = 'User.pw1' }

New-MgUser `
  -UserPrincipalName AllanD@Adatum.onmicrosoft.com `
  -DisplayName 'Allan Deyoung' `
  -GivenName 'Allan' `
  -Surname 'Deyoung' `
  -PasswordProfile $PasswordProfile `
  -AccountEnabled `
  -MailNickName 'AllanD'


# Manage User Account Settings in Microsoft 365

Organizations can manage Microsoft 365 user accounts immediately after subscription purchase. User accounts can be managed through:

- **Microsoft 365 admin center**
- **PowerShell**
- **Directory synchronization** (Microsoft Entra Connect Sync or Cloud Sync)

Identity model selection determines where accounts are managed:

---

## Identity Models

### **Cloud-only**
- Users are created and managed in:
  - Microsoft 365 admin center  
  - PowerShell  
  - Microsoft Entra admin center  

### **Hybrid**
- Microsoft 365 synchronizes user accounts from **on-premises AD DS**
- Accounts must be managed using AD DS tools

---

# Account Management Tools

| Tool | Notes |
|------|-------|
| **Microsoft 365 admin center** | - Add users individually or in bulk<br>- Simple web interface<br>- Cannot modify synced accounts (only location & license)<br>- Not usable with SSO options |
| **Windows PowerShell** | - Create accounts via scripts<br>- Supports bulk creation<br>- Can assign locations and licenses regardless of account origin |
| **Bulk import (CSV)** | - Add many users at once<br>- CSV-based upload<br>- Not usable with SSO options |
| **Microsoft Entra ID** | - Free edition included with Microsoft 365<br>- Supports SSPR for cloud-only users<br>- Enhanced functionality available via P1/P2 |
| **Directory synchronization** | - Integrates on-prem identities with Microsoft Entra ID<br>- Required for SSO<br>- Required for hybrid Exchange, staged migrations<br>- Syncs mail-enabled/security groups<br>- Requires meeting AD DS attribute standards<br>- Installed on-premises servers |

---

# Important Notes

If you create accounts **without assigning a license**, the user can access the Microsoft 365 admin center but **cannot use any services**.

After assigning:
- **Location**
- **Licenses**

The system replicates the account, and the user can sign in and access services.

---

# Manage User Accounts in Microsoft 365 Admin Center

You can manage:

- Administrator roles  
- Sign-in status  
- User locations  
- Licenses  

These settings can be modified through:

- Microsoft 365 admin center  
- PowerShell  

The admin center is the simplest interface.

---

## Editing a User Account

### Steps:

1. Go to **Microsoft 365 admin center**.
2. Select **Users > Active Users**.
3. Select a user to open the **user account pane**, which contains these tabs:

---

## User Account Pane Tabs

### **Account**
- Modify:
  - Username & aliases  
  - Email addresses  
  - Group membership  
  - Roles  
  - Contact info  
- Manage:
  - MFA  
  - Sign-out from all sessions  
- View:
  - Sign-in history (30 days)  
  - Microsoft 365 app activations  

---

### **Devices**
- Displays devices enrolled in Intune.

---

### **Licenses and Apps**
- Modify assigned licenses  
- Set user location  
- Customize available apps  

---

### **Mail**
- Modify:
  - Mailbox permissions  
  - Forwarding  
  - Automatic replies  
  - GAL visibility  
  - Litigation hold  
  - Exchange properties  
  - Email apps  

---

### **OneDrive**
- Access user’s files  
- View storage quota  
- Manage external sharing  
- Links to SharePoint admin center for:
  - Data retention settings  
  - Default storage space  



# Manage User Licenses in Microsoft 365

Microsoft paid cloud services, such as Microsoft 365, Enterprise Mobility + Security, Dynamics 365, and other similar products, require licenses. These licenses are assigned to each user who needs access to these services. To manage licenses, administrators use one of the management portals (Microsoft 365 or Azure) and PowerShell cmdlets. Microsoft Entra ID is the underlying infrastructure that supports identity management for all Microsoft Cloud services. Microsoft Entra ID stores information about license assignment states for users.

One of the most basic tasks for Microsoft 365 Administrators is user management. To manage users, you must understand how to manage their licenses. Your organization’s users need licenses to use Microsoft 365 services, such as Microsoft Outlook and Microsoft SharePoint Online. When an administrator assigns a license to a user, the system automatically sets up the service for that user. For example, when you assign a SharePoint Online license to a user, the system assigns the user edit permissions on the default team site.

Only members of the **Global admin** and **User Management admin** roles can assign or remove licenses.

> **Important:**  
> When an administrator removes a license from a user, the system deletes any service data associated with that user. You have a 30-day grace period to recover that data. After 30 days, the data is not recoverable.

---

## Viewing User License Information

### View number of licenses remaining
1. In the Microsoft 365 admin center, go to **Billing > Licenses**.  
2. Under **Subscriptions**, view:
   - Total available licenses  
   - Assigned licenses  

### View unlicensed users
1. In the Microsoft 365 admin center, go to **Users > Active users**.  
2. Select **Filter**.  
3. Choose **Unlicensed users**.

---

## Assigning a License (Admin Center)

Administrators can assign or remove licenses for one or multiple users.

1. Go to **Users > Active users**.
2. Select the users.
3. Click **Manage product licenses** (or **More actions > Manage product licenses**).
4. Choose one option:
   - **Replace** — Remove existing licenses and assign new ones.
   - **Assign more** — Keep existing and add more.
   - **Unassign all** — Remove all licenses.

---

## Managing User Licenses with Microsoft Graph PowerShell

Before assigning a license, the **UsageLocation** property must be set on the user account.

### Required permissions
- Assign/remove license: `User.ReadWrite.All` or similar
- View tenant license info: `Organization.Read.All`

### Connect to Microsoft Graph

Connect-MgGraph -Scopes User.ReadWrite.All, Organization.Read.All


### View available licensing plans
Get-MgSubscribedSku

### Find unlicensed accounts
Get-MgUser -Filter 'assignedLicenses/$count eq 0' -ConsistencyLevel eventual -CountVariable unlicensedUserCount -All


### Find unlicensed synchronized users
Get-MgUser -Filter 'assignedLicenses/$count eq 0 and OnPremisesSyncEnabled eq true' -ConsistencyLevel eventual -CountVariable unlicensedUserCount -All -Select UserPrincipalName


### Find accounts without UsageLocation
Get-MgUser -Select Id,DisplayName,Mail,UserPrincipalName,UsageLocation,UserType | where { $_.UsageLocation -eq $null -and $_.UserType -eq 'Member' }


### Set UsageLocation

$userUPN="<user sign-in name (UPN)>"
$userLoc="<ISO 3166-1 alpha-2 country code>"

Update-MgUser -UserId $userUPN -UsageLocation $userLoc

### Example
Update-MgUser -UserId "belindan@litwareinc.com" -UsageLocation US

### Note:
Without -All, Get-MgUser only returns the first 100 users.


## Assigning Licenses via PowerShell

### Basic license assignment
Set-MgUserLicense -UserId $userUPN -AddLicenses @{SkuId = "<SkuId>"} -RemoveLicenses @()

#### Example: Assign Microsoft 365 E5 license
$e5Sku = Get-MgSubscribedSku -All | Where SkuPartNumber -eq 'SPE_E5'
Set-MgUserLicense -UserId "belindan@litwareinc.com" -AddLicenses @{SkuId = $e5Sku.SkuId} -RemoveLicenses @()

#### Example: Assign E5 + EMS E5

$e5Sku = Get-MgSubscribedSku -All | Where SkuPartNumber -eq 'SPE_E5'
$e5EmsSku = Get-MgSubscribedSku -All | Where SkuPartNumber -eq 'EMSPREMIUM'

$addLicenses = @(
    @{SkuId = $e5Sku.SkuId},
    @{SkuId = $e5EmsSku.SkuId}
)

Set-MgUserLicense -UserId "belinda@litwareinc.com" -AddLicenses $addLicenses -RemoveLicenses @()


#### Example: Assign E5 but disable Bookings + Customer Lockbox

$e5Sku = Get-MgSubscribedSku -All | Where SkuPartNumber -eq 'SPE_E5'
$disabledPlans = $e5Sku.ServicePlans |
    Where ServicePlanName -in ("LOCKBOX_ENTERPRISE", "MICROSOFTBOOKINGS") |
    Select -ExpandProperty ServicePlanId

$addLicenses = @(
    @{
        SkuId = $e5Sku.SkuId
        DisabledPlans = $disabledPlans
    }
)

Set-MgUserLicense -UserId "belinda@litwareinc.com" -AddLicenses $addLicenses -RemoveLicenses @()

#### Example: Keep existing disabled plans, disable Sway + Forms

$userLicense = Get-MgUserLicenseDetail -UserId "belinda@litwareinc.com"
$userDisabledPlans = $userLicense.ServicePlans |
    Where ProvisioningStatus -eq "Disabled" |
    Select -ExpandProperty ServicePlanId

$e5Sku = Get-MgSubscribedSku -All | Where SkuPartNumber -eq 'SPE_E5'

$newDisabledPlans = $e5Sku.ServicePlans |
    Where ServicePlanName -in ("SWAY", "FORMS_PLAN_E5") |
    Select -ExpandProperty ServicePlanId

$disabledPlans = ($userDisabledPlans + $newDisabledPlans) | Select -Unique

$addLicenses = @(
    @{
        SkuId = $e5Sku.SkuId
        DisabledPlans = $disabledPlans
    }
)

Set-MgUserLicense -UserId "belinda@litwareinc.com" -AddLicenses $addLicenses -RemoveLicenses @()
