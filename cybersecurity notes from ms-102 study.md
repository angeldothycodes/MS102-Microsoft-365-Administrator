
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
