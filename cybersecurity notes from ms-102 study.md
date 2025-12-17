
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

