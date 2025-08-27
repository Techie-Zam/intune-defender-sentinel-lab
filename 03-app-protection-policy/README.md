# 📱 App Protection Policy via Microsoft Intune

This section documents the configuration and deployment of App Protection Policies (APP) in Microsoft Intune. APPs help protect corporate data on both managed and unmanaged devices by applying policies at the app level, especially useful for mobile applications on iOS and Android.

---

## 🎯 Objective

Implement App Protection Policies to ensure data security, control data sharing, and enforce compliance without requiring full device enrollment.

---

## 📋 Policies Configured

| Platform | Policy Name             | Key Settings                                    | Deployment Scope             |
|----------|------------------------|------------------------------------------------|------------------------------|
| iOS      | iOS App Protection     | Data encryption, save restrictions, PIN required | Targeted users/groups        |
| Android  | Android App Protection | Data transfer restrictions, encrypt backups, conditional launch | Targeted users/groups        |

---

## 🛠 Key Configuration Highlights

- **Data Protection:** Prevent data leakage by restricting copy/paste, save as, and backup to cloud services.
- **Access Requirements:** Require app PIN or biometric authentication to access managed apps.
- **Conditional Launch:** Block or wipe apps if device jailbreak/root is detected or if device is not compliant.
- **Selective Wipe:** Ability to wipe corporate data without affecting personal data on the device.
- **Policy Assignment:** Assigned to specific Azure AD user groups for targeted protection.

---

## 🔧 Tools Used

- Microsoft Endpoint Manager Admin Center
- iOS and Android test devices (enrolled and unenrolled)
- Azure AD user groups for policy targeting

---

## 📸 Sample Screenshots

| Screenshot Description           | Preview                        |
|---------------------------------|-------------------------------|
| App Protection Policy Overview   | ![App Protection Policy](app-protection-overview.png)  |
| Data Protection Settings         | ![Data Protection](data-protection-settings.png)       |
| Access Requirements Configuration| ![Access Requirements](access-requirements.png)       |


---

## 💡 Notes

- APP works both on enrolled and unenrolled devices, making it ideal for BYOD scenarios.
- Testing includes app behavior when policy is applied, including copy/paste restrictions and app PIN prompts.
- Integration with Conditional Access policies enhances overall security posture.

---

## 🚀 Next Steps

- Expand policies to additional apps and platforms.
- Integrate with Conditional Access for enhanced security.
- Automate monitoring of app compliance and usage.

---


