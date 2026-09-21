# @ohos.enterprise.securityManager(Security Management)

This module provides enterprise device security management capabilities, including certificate management, device security policy management, password policy management, clipboard policy management, watermark policy management, and permission management. Enterprises can use this module to monitor the device security status in real time, manage the lifecycle of enterprise certificates, configure device password policies in a unified manner, control the use of the app clipboard, set screen and app watermarks to prevent information leakage, and implement refined management of app permissions. This helps enterprises enhance device security protection capabilities and reduce data leakage risks.

> **NOTE:** 
> 
> The APIs of this module can be called only by a device administrator application that is enabled. For details, see
> [MDM Kit Development](../../../mdm/mdm-kit-guide.md).

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

## Modules to Import

```TypeScript
import { securityManager } from '@kit.MDMKit';
```

## Summary

### Functions

| Name | Description |
| --- | --- |
| [addAllowedPermissionBundle](arkts-mdm-securitymanager-addallowedpermissionbundle-f.md) | Adds an application to the permission usage exception list. Applications in the list are not subject to the permission restriction policy set via [setDisallowedPermission](arkts-mdm-securitymanager-setdisallowedpermission-f.md). This API is applicable to enterprise scenarios. For example, when the camera permission is disabled, attendance applications and collaborative office applications can still use the camera, ensuring that critical enterprise business operates normally. |
| [addUserExtendCredential](arkts-mdm-securitymanager-adduserextendcredential-f.md) | Adds the extended user credential for an account. |
| [cancelScreenWatermarkImage](arkts-mdm-securitymanager-cancelscreenwatermarkimage-f.md) | Cancels a screen watermark policy, which takes effect for all users. After the cancellation is successful, the watermark on the device screen disappears. When a device no longer requires screen watermark protection, enterprises can call this API to cancel the watermark policy. Only the user who sets the screen watermark can cancel it. For example, user 101 cannot cancel the screen mark set by user 100 |
| [cancelWatermarkImage](arkts-mdm-securitymanager-cancelwatermarkimage-f.md) | Cancels the watermark policy for a specified user. When an application no longer requires watermark protection or needs to be updated, enterprises can call this API to cancel the watermark policy. |
| [closeSession](arkts-mdm-securitymanager-closesession-f.md) | Closes a credential change session for the specified account. |
| [getAllowedPermissionBundles](arkts-mdm-securitymanager-getallowedpermissionbundles-f.md) | Obtains the list of applications in the permission exception list. |
| [getAppClipboardPolicy](arkts-mdm-securitymanager-getappclipboardpolicy-f.md#getappclipboardpolicy) | Obtains the device clipboard policy. |
| [getAppClipboardPolicy](arkts-mdm-securitymanager-getappclipboardpolicy-f.md#getappclipboardpolicy-1) | Obtains the device clipboard policy. Enterprises can use this API to query the current clipboard policy for policy audit and compliance check, ensuring that the clipboard policy complies with enterprise security requirements. |
| [getAppClipboardPolicy](arkts-mdm-securitymanager-getappclipboardpolicy-f.md#getappclipboardpolicy-2) | Obtains the device clipboard policy of a specified application for a specified user. |
| [getAppClipboardPolicy](arkts-mdm-securitymanager-getappclipboardpolicy-f.md#getappclipboardpolicy-3) | Obtains the device clipboard policy of a specified application for a specified user. Enterprises can use this API to query the clipboard usage permission configuration of a specific application for policy audit and compliance check. |
| [getDeviceSecurityLevelPolicy](arkts-mdm-securitymanager-getdevicesecuritylevelpolicy-f.md) | Gets the device security level policy. |
| [getDisallowedPermissions](arkts-mdm-securitymanager-getdisallowedpermissions-f.md) | Obtains the list of disabled permissions of a specified user. |
| [getExternalSourceExtensionsPolicy](arkts-mdm-securitymanager-getexternalsourceextensionspolicy-f.md#getexternalsourceextensionspolicy) | Obtains the management policy for extensions from external sources. |
| [getExternalSourceExtensionsPolicy](arkts-mdm-securitymanager-getexternalsourceextensionspolicy-f.md#getexternalsourceextensionspolicy-1) | Obtains the management policy for extensions from external sources. |
| [getPasswordPolicy](arkts-mdm-securitymanager-getpasswordpolicy-f.md#getpasswordpolicy) | Obtains the device screen lock password policy. |
| [getPasswordPolicy](arkts-mdm-securitymanager-getpasswordpolicy-f.md#getpasswordpolicy-1) | Obtains the device screen lock password policy. Enterprises can use this API to query the current password policy for policy audit and compliance check, ensuring that the device password policy complies with enterprise security specifications. |
| [getPermissionManagedState](arkts-mdm-securitymanager-getpermissionmanagedstate-f.md) | Obtains the management policy for the [user_grant permission](../../apis-ability-kit/arkts-apis/arkts-ability-permissions-t.md) of a specified application. |
| [getSecurityStatus](arkts-mdm-securitymanager-getsecuritystatus-f.md) | Obtains the security status of the current device. This API is applicable to scenarios such as device compliance check, security status audit, and policy execution effect verification, helping enterprise administrators determine whether devices meet security requirements. Enterprises can use this API to monitor the security patch status and file encryption status of devices in real time, enabling timely detection of device security risks and prompt action to protect enterprise devices and data. |
| [getUnlockPolicy](arkts-mdm-securitymanager-getunlockpolicy-f.md) | Gets the unlock policy. |
| [getUserCertificates](arkts-mdm-securitymanager-getusercertificates-f.md) | Obtains the user certificate of a specified system account. Enterprises can use this API to query the list of user certificates installed on a device for scenarios such as certificate audit and certificate validity period management, ensuring traceability of certificate management. |
| [getUserExtendCredential](arkts-mdm-securitymanager-getuserextendcredential-f.md) | Gets the extended user credential information of the specified account. |
| [getWatermarkImageApps](arkts-mdm-securitymanager-getwatermarkimageapps-f.md) | Obtains the list of application bundle names for which watermarks have been set for a specified user. |
| [installEnterpriseReSignatureCertificate](arkts-mdm-securitymanager-installenterpriseresignaturecertificate-f.md) | Installs the enterprise application re-signing certificate. After the installation is successful, the enterprise can use the certificate to re-sign applications. |
| [installUserCertificate](arkts-mdm-securitymanager-installusercertificate-f.md#installusercertificate) | Installs a user certificate. This API uses a promise to return the result. Enterprises can use this API to install certificates on devices in scenarios such as enterprise VPN connection, security authentication, and digital signatures, implementing enterprise-level secure communication and data protection. |
| [installUserCertificate](arkts-mdm-securitymanager-installusercertificate-f.md#installusercertificate-1) | Installs a user certificate based on the system account. Enterprises can install independent certificates for different user accounts, enabling security isolation and personalized certificate management in multi-user environments, thus meeting the security control requirements of multi-user devices. |
| [isScreenLockDisabledForAccount](arkts-mdm-securitymanager-isscreenlockdisabledforaccount-f.md) | Checks whether swipe-to-unlock is disabled for the current user. |
| [isWeakPinEnabled](arkts-mdm-securitymanager-isweakpinenabled-f.md) | Check whether weak PIN verification is enabled. |
| [openSession](arkts-mdm-securitymanager-opensession-f.md) | Opens a credential change session for the specified account. |
| [removeAllowedPermissionBundle](arkts-mdm-securitymanager-removeallowedpermissionbundle-f.md) | Removes an application from the permission usage exception list. After the application is removed, it cannot use the corresponding permission any more. |
| [removeUserExtendCredential](arkts-mdm-securitymanager-removeuserextendcredential-f.md) | Removes the extended user credential. |
| [setAppClipboardPolicy](arkts-mdm-securitymanager-setappclipboardpolicy-f.md#setappclipboardpolicy) | Sets the device clipboard policy. After the policy is set, applications will be restricted in their clipboard usage according to the configured policy. This API is applicable to enterprise data leakage prevention scenarios, such as restricting clipboard usage for sensitive applications (such as enterprise email and financial systems) to prevent sensitive data from being copied to unauthorized applications, thereby reducing the risk of data leakage. Enterprises can use this API to control application clipboard usage permissions, preventing sensitive data from being leaked to unauthorized applications via the clipboard, and enhancing enterprise data security protection capabilities. |
| [setAppClipboardPolicy](arkts-mdm-securitymanager-setappclipboardpolicy-f.md#setappclipboardpolicy-1) | Sets the device clipboard policy of a specified application for a specified user. After the policy is set, the clipboard of the specified application will be restricted in its usage scope according to the configured policy. Enterprises can configure differentiated clipboard usage permissions for different applications across different users, enabling fine-grained data access control and meeting the security management requirements in multi-user, multi-application scenarios. |
| [setDeviceSecurityLevelPolicy](arkts-mdm-securitymanager-setdevicesecuritylevelpolicy-f.md) | Sets the device security level policy. |
| [setDisallowedPermission](arkts-mdm-securitymanager-setdisallowedpermission-f.md) | Disables the specified permission of the specified user. After the permission is disabled, all applications under the specified user will be denied by default when applying for or using the specified permission. This API is applicable to enterprise security compliance scenarios, such as disabling high-risk permissions like camera and microphone to prevent privacy leaks, or disabling specific features (such as Bluetooth sharing) to prevent enterprise data from being transferred out. |
| [setExternalSourceExtensionsPolicy](arkts-mdm-securitymanager-setexternalsourceextensionspolicy-f.md) | Sets the management policy for extensions from external sources. After the policy is set, the system controls the running behavior of extensions from external sources based on the configured policy. This API is applicable to enterprise security management scenarios, such as preventing employees from installing unauthorized browser extensions or forcibly enabling enterprise-approved extension functions to ensure enterprise device security. |
| [setPasswordPolicy](arkts-mdm-securitymanager-setpasswordpolicy-f.md) | Sets the device screen lock password policy. After the policy is set, when a user sets a lock screen password, if the password does not meet the requirements, a security prompt will be displayed asking the user to reset the password. This policy is applicable to enterprise security compliance scenarios, such as requiring employees to use strong passwords and change passwords periodically, to reduce the risk of enterprise data leakage. |
| [setPermissionManagedState](arkts-mdm-securitymanager-setpermissionmanagedstate-f.md) | Sets the management policy for the [user_grant permission](../../apis-ability-kit/arkts-apis/arkts-ability-permissions-t.md) of a specified application. This is applicable to enterprise application batch deployment scenarios, such as granting permissions silently to reduce permission prompt interruptions, and unifying permission management policies for enterprise applications, thereby improving employee user experience and management efficiency. |
| [setScreenLockDisabledForAccount](arkts-mdm-securitymanager-setscreenlockdisabledforaccount-f.md) | Disables or enables swipe-to-unlock for the current user. When enabled, the user must swipe on the screen after the screen is turned on to access the home screen. When disabled, the screen goes directly to the home screen after being turned on. This API is suitable for enterprise device management scenarios, such as disabling swipe-to-unlock in specific security environments to simplify operations, or enabling it in general scenarios as a basic security measure. |
| [setScreenWatermarkImage](arkts-mdm-securitymanager-setscreenwatermarkimage-f.md) | Sets a screen watermark policy, which takes effect for all users. |
| [setUnlockPolicy](arkts-mdm-securitymanager-setunlockpolicy-f.md) | Sets the unlock policy. |
| [setWatermarkImage](arkts-mdm-securitymanager-setwatermarkimage-f.md#setwatermarkimage) | Sets a watermark policy for a specified application of a specified user. Currently, a maximum of 100 policies can be saved. |
| [setWatermarkImage](arkts-mdm-securitymanager-setwatermarkimage-f.md#setwatermarkimage-1) | Sets a watermark policy for a specified application of a specified user. Currently, a maximum of 100 policies can be saved. |
| [setWeakPinEnable](arkts-mdm-securitymanager-setweakpinenable-f.md) | Sets the weak PIN enable status. |
| [uninstallEnterpriseReSignatureCertificate](arkts-mdm-securitymanager-uninstallenterpriseresignaturecertificate-f.md) | Uninstalls the enterprise application re-signing certificate. After the enterprise re-signing certificate is uninstalled, the applications signed using this certificate can run properly before the device is restarted, but cannot run after the device is restarted. |
| [uninstallUserCertificate](arkts-mdm-securitymanager-uninstallusercertificate-f.md) | Uninstalls a user certificate. This API uses a promise to return the result. This API is applicable to enterprise certificate management scenarios, such as replacing an expired certificate and revoking an employee's access to enterprise resources. Enterprises can call this API to uninstall a certificate when the certificate expires, is replaced, or is no longer needed, ensuring the flexibility and security of device certificate management. |

<!--Del-->
### Functions(System API)

| Name | Description |
| --- | --- |
| [getDeviceEncryptionStatus](arkts-mdm-securitymanager-getdeviceencryptionstatus-f-sys.md) | Queries the encryption status of the device file system. |
| [getPasswordPolicy](arkts-mdm-securitymanager-getpasswordpolicy-f-sys.md#getpasswordpolicy-2) | Obtains the device screen lock password policy. |
| [getSecurityPatchTag](arkts-mdm-securitymanager-getsecuritypatchtag-f-sys.md) | Queries the security patch tag of a device. |
<!--DelEnd-->

### Interfaces

| Name | Description |
| --- | --- |
| [AddCredentialInfo](arkts-mdm-securitymanager-addcredentialinfo-i.md) | Add credential information. |
| [ApplicationInstance](arkts-mdm-securitymanager-applicationinstance-i.md) | Application instance |
| [CertBlob](arkts-mdm-securitymanager-certblob-i.md) | Represents the certificate information. |
| [PasswordPolicy](arkts-mdm-securitymanager-passwordpolicy-i.md) | Represents a device screen lock password policy. |
| [RemoveCredentialInfo](arkts-mdm-securitymanager-removecredentialinfo-i.md) | Remove credential information. |
| [UserExtCredentialInfo](arkts-mdm-securitymanager-userextcredentialinfo-i.md) | Use extended credential information. |
| [WatermarkProperties](arkts-mdm-securitymanager-watermarkproperties-i.md) | Defines watermark properties. |

<!--Del-->
### Interfaces(System API)

| Name | Description |
| --- | --- |
| [DeviceEncryptionStatus](arkts-mdm-securitymanager-deviceencryptionstatus-i-sys.md) | Represents the file system encryption status. |
<!--DelEnd-->

### Enums

| Name | Description |
| --- | --- |
| [ClipboardPolicy](arkts-mdm-securitymanager-clipboardpolicy-e.md) | Represents a device clipboard policy. |
| [DeviceSecurityLevelPolicy](arkts-mdm-securitymanager-devicesecuritylevelpolicy-e.md) | The device security level policy |
| [PasswordAlgs](arkts-mdm-securitymanager-passwordalgs-e.md) | Enumerates the encryption algorithms used to process password data. |
| [PermissionManagedState](arkts-mdm-securitymanager-permissionmanagedstate-e.md) | Represents the management status of application permissions. |
| [UnlockPolicy](arkts-mdm-securitymanager-unlockpolicy-e.md) | The policy of unlock device. |
