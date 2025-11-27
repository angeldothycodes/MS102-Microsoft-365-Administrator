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

