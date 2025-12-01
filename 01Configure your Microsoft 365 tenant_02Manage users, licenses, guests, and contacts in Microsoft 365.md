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


