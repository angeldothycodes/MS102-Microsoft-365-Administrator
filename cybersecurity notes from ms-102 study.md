
# Zero Trust Security Model – Core Concept

Traditionally, organizations believed in a **“trust but verify later”** approach. The idea was simple:

- If someone is inside the company network, they are assumed to be safe.
- Security measures such as:
  - **Firewalls**: Software or hardware that blocks unauthorized access.
  - **Antivirus programs**: Software to detect malware.
  - **Access controls**: Rules that decide who can do what.
- Employees and devices are assumed trustworthy.

---

## Problem with this traditional approach:
- Devices and users inside a network are not always safe. Hackers or malware can exploit weaknesses.
- Employees or contractors can accidentally click malicious links, open unsafe files, or fall for phishing attacks.
- One infected device can compromise the entire network.

---

# Zero Trust Approach

Zero Trust assumes everything is potentially unsafe, even internal resources.  
Think of it as: **“Never trust, always verify.”**

---

## Key Principles of Zero Trust:

### 1. Verify explicitly
- Authenticate users and devices every time they access a resource.
- **Example:** Just because a user is on the company network, do not assume they are allowed to access a sensitive file.

### 2. Use least-privileged access
- Give users only the access they need to perform their job.
- **Example:** A marketing employee does not need access to the financial database.

### 3. Assume breach
- Plan for the possibility that an attacker is already in the system.
- Segment networks to limit the spread of a potential attack.

---

# Five Steps to Secure Identity Infrastructure

Identity is central to Zero Trust. Here’s what organizations should do:

## 1. Strengthen credentials
- Use strong passwords and multifactor authentication (MFA).
- MFA means a user must provide two or more proofs of identity, e.g., a password plus a code sent to a phone.

## 2. Reduce attack surface
- Stop using outdated, insecure protocols.
- Limit entry points and control administrative access tightly.

## 3. Automate threat response
- Automate detection and responses so attacks are stopped quickly.

## 4. Increase awareness
- Use auditing and logging to monitor suspicious activity.
- Detect patterns that could indicate internal or external attacks.

#### 5. Enable user self-help
- Make it easy for employees to recover accounts or reset passwords without compromising security.



# 1. Identity – The Starting Point of Zero Trust

## Why Identity Comes First

### In the past:
- Security focused on networks (office buildings, firewalls).
- If you were “inside,” you were trusted.

### Today:
- Employees work remotely.
- Devices are personal (Bring Your Own Device).
- Applications are in the cloud.

👉 **There is no longer a clear network boundary.**

Because of this, **identity becomes the new security perimeter**.

---

### Identity means:
- Who the user is
- How they prove who they are
- What they are allowed to access

---

## What Microsoft Recommends

Microsoft says:
> Start with a strong cloud identity foundation.

This means:
- Strong sign-in methods
- Protected user credentials
- Protected devices

The main tool Microsoft provides for this is:
**Microsoft Entra ID**

---

### What is Microsoft Entra ID?
Microsoft Entra ID is Microsoft’s cloud-based identity and access management service.

In simple terms:
- It stores user accounts.
- It verifies sign-ins.
- It controls access to applications and data.


  
# Passwordless Authentication

Passwords are one of the weakest security mechanisms.

## Why?
- People reuse passwords.
- People choose weak passwords.
- Passwords get stolen through phishing.

**Passwordless authentication removes passwords entirely.**

Instead of typing a password, users sign in using:

---

### Windows Hello for Business
- Uses biometrics such as fingerprint or facial recognition.
- The credential stays on the device.

### Microsoft Authenticator app
- A mobile application that approves sign-ins.
- The user confirms: *“Yes, this is me.”*

### FIDO2 security keys
- Physical keys (like USB or NFC devices).
- You must physically possess the key to sign in.

### Temporary Access Pass
- A time-limited code.
- Used to set up or recover passwordless sign-in.
- Prevents permanent passwords from being required.

---


# 1. Identity – The Starting Point of Zero Trust

## Why Identity Comes First

### In the past:
- Security focused on networks (office buildings, firewalls).
- If you were “inside,” you were trusted.

### Today:
- Employees work remotely.
- Devices are personal (Bring Your Own Device).
- Applications are in the cloud.

👉 **There is no longer a clear network boundary.**

Because of this, **identity becomes the new security perimeter**.

---

### Identity means:
- Who the user is
- How they prove who they are
- What they are allowed to access

---

## What Microsoft Recommends
Microsoft says:
> Start with a strong cloud identity foundation.

This means:
- Strong sign-in methods
- Protected user credentials
- Protected devices

The main tool Microsoft provides for this is:
**Microsoft Entra ID**

---

### What is Microsoft Entra ID?
Microsoft Entra ID is Microsoft’s cloud-based identity and access management service.

In simple terms:
- It stores user accounts.
- It verifies sign-ins.
- It controls access to applications and data.

---

# Passwordless Authentication

Passwords are one of the weakest security mechanisms.

## Why?
- People reuse passwords.
- People choose weak passwords.
- Passwords get stolen through phishing.

**Passwordless authentication removes passwords entirely.**

Instead of typing a password, users sign in using:

---

### Windows Hello for Business
- Uses biometrics such as fingerprint or facial recognition.
- The credential stays on the device.

### Microsoft Authenticator app
- A mobile application that approves sign-ins.
- The user confirms: *“Yes, this is me.”*

### FIDO2 security keys
- Physical keys (like USB or NFC devices).
- You must physically possess the key to sign in.

### Temporary Access Pass
- A time-limited code.
- Used to set up or recover passwordless sign-in.
- Prevents permanent passwords from being required.

👉 **This directly supports Zero Trust because identity proof is stronger and harder to steal.**

---

# Microsoft Entra Conditional Access

This is extremely important.

**Conditional Access is the policy engine behind Zero Trust.**

A policy engine means:
- A system that evaluates conditions
- Then decides whether access is allowed, blocked, or restricted

Conditional Access uses **context** to decide.

Context includes:
- Who the user is
- What they are trying to do
- Which application they are using
- How sensitive the data is

**Example:**
- A user can read a document.
- But downloading it requires extra verification.

👉 **This allows granular control, not all-or-nothing access.**

---

# Microsoft Entra Verifiable Credentials

This feature allows organizations to verify claims without storing personal data.

**Example claims:**
- Educational credentials
- Professional certifications

Instead of storing sensitive documents:
- The system verifies the credential is valid.
- The organization does not store the actual data.

This improves:
- Security
- Privacy
- Trust

---

# 2. Security – “Assume Breach” in Practice

## What “Assume Breach” Means
Assume breach means:
- Act as if an attacker is already inside your environment.
- Design security to detect quickly and limit damage.

**The problem many organizations face:**
- Security tools are fragmented.
- One tool for email.
- One tool for endpoints.
- One tool for logs.

This makes investigations slow and complex.

---

## Microsoft’s Integrated Security Approach
Microsoft combines tools instead of separating them.

Two important terms:
- **SIEM (Security Information and Event Management)**
  - Collects and analyzes security logs.
  - Detects suspicious behavior across systems.
- **XDR (Extended Detection and Response)**
  - Correlates signals from multiple sources:
    - Endpoints
    - Email
    - Identities
    - Cloud applications
  - Automatically investigates and responds.

Microsoft combines these into:
**Microsoft Defender XDR**  
*(formerly Microsoft 365 Defender)*

---

### Key Security Capabilities
- **Unified Security Portal**
  - One place to see alerts.
  - One investigation experience.
  - Reduced admin complexity.
- **Threat Analytics**
  - Reports written by Microsoft security experts.
  - Explain active threats and mitigation steps.
- **Secured-core Systems**
  - Security built into:
    - Hardware
    - Firmware
    - Operating system
  - Protection starts before the system boots.
  - Prevents advanced malware attacks.
- **Cross-Platform Protection**
  - Works on:
    - Windows
    - macOS
    - Linux
    - Android
    - iOS
- **Microsoft Sentinel**
  - Cloud-based SIEM.
  - Works across:
    - Microsoft cloud
    - Amazon Web Services
    - Google Cloud Platform
    - Other third-party platforms

👉 **This supports Zero Trust by providing visibility everywhere.**

---

# 3. Compliance – Protection from the Inside Out

Zero Trust is not only about stopping hackers.

It is also about:
- Preventing data leaks
- Detecting insider risk
- Protecting sensitive information

---

## Microsoft Purview
Microsoft Purview is a data governance and compliance platform.

It helps organizations:
- Discover where data exists
- Classify data
- Apply protection rules

---

### Key Compliance Features
- **Protected Document Coauthoring**
  - Multiple users can edit protected files.
  - Security controls remain in place.
- **Insider Risk Management**
  - Detects risky internal behavior.
  - Uses machine learning.
  - Respects privacy by design.
- **Data Loss Prevention (DLP)**
  - Prevents sensitive data from leaving the organization.
  - Works across:
    - Cloud services
    - Browsers
    - On-premises systems
- **Multicloud Data Protection**
  - Same sensitivity labels apply to:
    - Microsoft cloud
    - Other cloud providers
    - On-premises databases

👉 **This ensures Zero Trust protects data everywhere, not just Microsoft systems.**

---

# 4. Skilling – People Are Part of Zero Trust

Even the best tools fail if people do not know how to use them.

Microsoft addresses the security skills gap by providing structured learning paths and certifications.

---

## Microsoft Security Certifications
- **Security, Compliance, and Identity Fundamentals**
  - Entry-level understanding.
- **Information Protection Administrator Associate**
  - Focuses on compliance and data protection.
- **Security Operations Analyst Associate**
  - Focuses on detection and response.
- **Identity and Access Administrator Associate**
  - Focuses on identity and access management using Microsoft Entra ID.

Microsoft also provides:
- **Microsoft Security Technical Content Library**
- Role-based learning content

---

## Final Bootcamp Summary
- Zero Trust is a strategy, not a product.
- Identity is the foundation.
- Security assumes breaches will happen.
-- Compliance protects data from misuse.



# Big Picture First (Very Important)

Microsoft 365 security is **not one single tool**. It is a **set of tools**, and each one protects a different layer of your organization.

For your question, there are **three main security pillars** you must understand:

- **Microsoft Purview** → protects **data**
- **Microsoft Defender XDR** → protects against **attacks and threats**
- **Microsoft Entra ID** (with Conditional Access and Identity Protection) → protects **identity and access**

Think of it this way:
- **Who is the user?** → Microsoft Entra ID
- **Is something attacking us?** → Microsoft Defender XDR
- **Is sensitive data being handled safely?** → Microsoft Purview

---

# 1. Microsoft Purview
**“Data protection, data governance, and compliance”**

### What Purview is for:
Microsoft Purview is about **protecting information**, not users or devices.

It answers questions like:
- What data do we have?
- Where is sensitive data stored?
- Who can access or share it?
- Is data being leaked intentionally or accidentally?

### What Purview protects:
- Documents
- Emails
- Files
- Databases
- Cloud and on-premises data

---

### Core things Purview does (plain explanation):

#### 1. Data classification
Purview can scan files and emails and identify sensitive information such as:
- Credit card numbers
- Government identification numbers
- Confidential company documents

It then **labels them** (for example: *Public, Confidential, Highly Confidential*).

#### 2. Information protection
Once data is labeled, Purview can:
- Encrypt the file
- Prevent copying
- Prevent sharing outside the company
- Restrict printing or downloading

#### 3. Data Loss Prevention (DLP)
This prevents accidental or intentional data leaks.

**Example:**
- A user tries to email a confidential file to a personal email address
- Purview blocks the action or warns the user

#### 4. Insider Risk Management
Purview looks for risky behavior by internal users, such as:
- Downloading large amounts of data
- Accessing sensitive files outside normal work hours

This is done with **privacy controls**, not spying.

**In simple terms:**
Purview protects the **data itself**, no matter where it goes.

---

# 2. Microsoft Defender XDR
**“Threat detection, attack investigation, and response”**

### What Defender XDR is for:
Microsoft Defender XDR focuses on **security threats and attacks**.

It answers questions like:
- Are we being attacked?
- Is malware present?
- Is a user account compromised?
- How did the attack happen?
- How do we stop it quickly?

### What Defender XDR protects:
- Devices (Windows, macOS, Linux, mobile phones)
- Email systems
- User accounts
- Applications
- Cloud workloads

---

### What “XDR” means (important):
**Extended Detection and Response**

This means:
- It does not look at just one thing (like antivirus)
- It correlates signals across many systems

**Example:**
- Suspicious email
- Same user clicks link
- Device shows malware activity
- Account attempts unusual sign-ins

Defender XDR connects all of these together into **one incident**.

---

### Core capabilities explained simply:
#### 1. Threat detection
It detects:
- Malware
- Phishing attacks
- Ransomware
- Suspicious user behavior

#### 2. Investigation
It automatically:
- Analyzes what happened
- Determines how the attack started
- Identifies affected users and devices

#### 3. Response and remediation
It can:
- Isolate infected devices
- Block malicious files
- Reset compromised user accounts
- Stop the attack from spreading

**In simple terms:**
Defender XDR protects your organization from **active attacks and security incidents**.

---

# 3. Microsoft Entra ID (Identity and Access Security)
**“Who can access what, from where, and under what conditions”**

### What Entra ID is for:
It protects **identity**, which is the most targeted attack surface today.

It answers:
- Is this really the user?
- Is this sign-in risky?
- Should access be allowed, blocked, or restricted?

---

### Core security features:
#### 1. Authentication
Verifies who the user is using:
- Passwords
- Multifactor authentication (password + phone, app, or biometrics)
- Passwordless sign-in

#### 2. Conditional Access
This applies rules to sign-ins.

**Example rules:**
- Require multifactor authentication if user signs in from outside the country
- Block access if device is not compliant
- Allow access only to low-risk applications on unmanaged devices

#### 3. Identity Protection
Detects risky sign-ins such as:
- Impossible travel (two countries in minutes)
- Sign-ins from known malicious locations
- Credential theft attempts

**In simple terms:**
Entra ID decides whether a user is allowed to sign in and what they are allowed to access.

---

# Final Side-by-Side Summary (Very Important)

| Tool                  | Main Purpose                     | Protects                                      |
|----------------------|---------------------------------|----------------------------------------------|
| **Microsoft Purview** | Data protection and compliance  | Files, emails, documents, sensitive data    |
| **Microsoft Defender XDR** | Threat detection and response      | Devices, emails, users, attacks             |
| **Microsoft Entra ID** | Identity and access security         | User sign-ins, authentication, access decisions |

---

## One Simple Scenario (Putting It All Together)
A user tries to download a confidential file from home.

- **Microsoft Entra ID**
  - Verifies identity
  - Checks location and device
  - Requires multifactor authentication

- **Microsoft Purview**
  - Recognizes the file as confidential
  - Prevents external sharing or downloading

- **Microsoft Defender XDR**
  - Monitors for malware or suspicious behavior
  - Responds if the device is compromised

---

## One-Sentence Memory Trick
- **Entra ID** = Who are you and should you get in?
- **Defender XDR** = Are we under attack right now?
- **Purview** = Is our data being used
