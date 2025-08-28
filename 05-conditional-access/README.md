# 🔐 Conditional Access Policies

This section documents the Conditional Access (CA) policies tested in a lab environment using Microsoft Entra ID (formerly Azure AD). These policies were created to simulate real-world access control scenarios based on device compliance, user role, and location.

---

## 🎯 Objectives

- Implement MFA for all users and admin roles
- Block legacy authentication
- Require compliant, MDM-enrolled devices for accessing Microsoft 365 apps
- Test user impact and policy behavior in Report-only mode before enforcement

---

## 🛠️ Tools Used

- Microsoft Entra Admin Center (entra.microsoft.com)
- Microsoft Intune Admin Center
- Test Windows 10 and iPadOS devices
- Microsoft 365 Business Premium licensing

---

## 🧪 Policies Implemented

| Policy Name                                                 | Purpose                                                 | Mode        | Created On       |
|-------------------------------------------------------------|---------------------------------------------------------|-------------|------------------|
| Block legacy authentication                                | Blocks basic/legacy auth protocols                      | **On**      | 07/10/2025       |
| MFA for all users                                           | Requires MFA for all cloud resources                    | **On**      | 07/10/2025       |
| MFA for Azure Management                                   | Enforces MFA for managing Azure/Entra resources         | **On**      | 07/10/2025       |
| MFA for administrators                                      | Extra layer of protection for privileged accounts       | **On**      | 07/10/2025       |
| Require MDM-enrolled and compliant device for M365 access   | Enforces Intune compliance before app access            | **Report-only** | 08/03/2025   |

---

## 📸 Screenshots

| Screenshot Name                              | Description                                             |
|----------------------------------------------|---------------------------------------------------------|
| `[ca-policies-overview].png`                 | List view of all CA policies in Entra Admin Center     |
| `[ca-policy-block-legacy].png`               | Block legacy authentication – policy configuration     |
| `[ca-policy-mfa-required-m365].png`          | MFA for all users – user & resource assignment         |
| `[ca-policy-mfa-admins].png`                 | MFA for admins – role targeting setup                  |
| `[c-_policy-mdm-required-m365].png`          | Require compliant device – full policy breakdown       |

Place all screenshots in the `/screenshots/05-conditional-access/` directory.

---

## 🧪 Policy Testing Notes

### Test Device Behavior (Report-only Mode)

- Used Report-only to monitor user logins and verify enforcement logic before enforcing policies
- Verified that non-compliant devices triggered Report-only logs in Sign-in Logs
- Confirmed MFA prompt behavior from test user accounts via Microsoft 365 login

### Conditional Access Insights

- CA insights were used to observe which conditions (device, user, location) matched each login
- Logged failed and successful login attempts for further evaluation

---

## 🔍 Troubleshooting & Problem-Solving Highlights

| Issue Observed                                 | Root Cause Analysis & Resolution Approach                                                                                     |
|------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------|
| Conditional Access policy not enforcing as expected | Verified policy status was not left in Report-only mode; reviewed scope assignments to ensure target users and apps were included. Adjusted exclusions and re-tested to confirm enforcement. |
| Users bypassing MFA prompts unexpectedly       | Analyzed conflicting policies and Conditional Access exclusions; used Sign-in logs to identify inconsistent behaviors and refined policy priorities to enforce MFA reliably.             |
| Legitimate users blocked due to device compliance issues | Diagnosed gaps in device enrollment status and compliance reporting from Intune; communicated with end-users to remediate device issues or update compliance policies for edge cases.       |
| Unexpected app access denials                   | Correlated Conditional Access evaluation details in Sign-in logs with policy conditions (location, device state, user risk); iterated policy rules to balance security and user productivity. |
| Policy impact monitoring and validation        | Implemented Report-only mode monitoring, analyzed Azure AD sign-in telemetry, and generated actionable insights to optimize policy effectiveness before full enforcement.                      |

---


