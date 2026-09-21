# @ohos.enterprise.systemManager(System Management)

This module provides system management capabilities, including NTP time server settings, OTA update policy management, system update management, key event handling policies, log collection, and device activation lock management. It is suitable for enterprise device management scenarios, helping enterprise administrators uniformly manage device system configurations, update policies, and security policies, thereby improving enterprise device management efficiency and security.

> **NOTE:** 
> 
> The APIs of this module can be called only by a device administrator application that is enabled. For details, see
> [MDM Kit Development](../../../mdm/mdm-kit-guide.md).

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

## Modules to Import

```TypeScript
import { systemManager } from '@kit.MDMKit';
```

## Summary

### Functions

| Name | Description |
| --- | --- |
| [addAllowedPrinterIPAddressesForAccount](arkts-mdm-systemmanager-addallowedprinteripaddressesforaccount-f.md) | Adds allowed printer IP addresses for current account. The policy takes effect only for current account. |
| [addAllowedPrinterIPAddressesForDevice](arkts-mdm-systemmanager-addallowedprinteripaddressesfordevice-f.md) | Adds allowed printer IP addresses for device. The policy takes effect for all accounts. |
| [addDisallowedNearLinkProtocols](arkts-mdm-systemmanager-adddisallowednearlinkprotocols-f.md) | Adds a list of NearLink protocols that are not allowed to be used for a specified user. NearLink Kit provides a low -power, high-speed short-range communication service that supports connection and data interaction between NearLink devices. This API does not take effect for system services and system applications such as the keyboard and stylus. |
| [addKeyEventPolicies](arkts-mdm-systemmanager-addkeyeventpolicies-f.md) | Adds a key event handling policy. When the system triggers a key event, if the event matches the delivered key event policy, the MDM app will be notified via the [EnterpriseAdminExtensionAbility.onKeyEvent](arkts-mdm-enterprise-enterpriseadminextensionability-enterpriseadminextensionability-c.md#onkeyevent) callback, with the key event information of the matched policy carried in the callback. |
| [createExactTimer](arkts-mdm-systemmanager-createexacttimer-f.md) | Creates an exact timer. This API uses a promise to return the timer ID. |
| [destroyExactTimer](arkts-mdm-systemmanager-destroyexacttimer-f.md) | Destroys an exact timer. This API uses a promise to return the result. |
| [finishLogCollected](arkts-mdm-systemmanager-finishlogcollected-f.md) | Deletes the device logs collected by the current MDM app under the current user. |
| [getAllowedPrinterIPAddressesForAccount](arkts-mdm-systemmanager-getallowedprinteripaddressesforaccount-f.md) | Gets allowed printer IP addresses for current account. |
| [getAllowedPrinterIPAddressesForDevice](arkts-mdm-systemmanager-getallowedprinteripaddressesfordevice-f.md) | Gets allowed printer IP addresses for device. |
| [getAutoUnlockAfterReboot](arkts-mdm-systemmanager-getautounlockafterreboot-f.md#getautounlockafterreboot) | Checks whether the device is automatically unlocked upon reboot. |
| [getAutoUnlockAfterReboot](arkts-mdm-systemmanager-getautounlockafterreboot-f.md#getautounlockafterreboot-1) | Checks whether the device is automatically unlocked upon reboot. This API is applicable to scenarios where there is a need to verify whether the device reboot unlock policy is correctly configured, helping enterprise administrators confirm the status of the automatic device unlock function. |
| [getDisallowedNearLinkProtocols](arkts-mdm-systemmanager-getdisallowednearlinkprotocols-f.md) | Obtains the list of disallowed NearLink protocols for a specified user. This API is applicable to scenarios where there is a need to query the current NearLink protocol access restrictions for a user, helping enterprise administrators verify whether the policy has been correctly applied or obtain the current configuration before making policy adjustments. |
| [getInstallLocalEnterpriseAppEnabled](arkts-mdm-systemmanager-getinstalllocalenterpriseappenabled-f.md) | Checks whether local installation of enterprise applications is supported. This API is applicable to scenarios where there is a need to verify whether the local installation of enterprise applications is enabled on the device, helping enterprise administrators confirm the policy configuration status to ensure that enterprise applications can be properly installed. |
| [getInstallLocalEnterpriseAppEnabledForAccount](arkts-mdm-systemmanager-getinstalllocalenterpriseappenabledforaccount-f.md) | Checks whether local installation of enterprise applications is supported for a specified user. This API is applicable to scenarios where there is a need to verify whether local installation of enterprise applications is enabled for a specific user, helping enterprise administrators confirm the policy configuration status and ensure that users can normally install enterprise applications. |
| [getKeyEventPolicies](arkts-mdm-systemmanager-getkeyeventpolicies-f.md#getkeyeventpolicies) | Obtains the key event handling policy. |
| [getKeyEventPolicies](arkts-mdm-systemmanager-getkeyeventpolicies-f.md#getkeyeventpolicies-1) | Obtains the key event handling policy. This API is applicable to scenarios where you need to query the current key event handling policy configuration. It helps enterprise administrators verify whether the policy has been correctly applied or obtain the current configuration before making policy adjustments. |
| [getLocalHotaDomain](arkts-mdm-systemmanager-getlocalhotadomain-f.md) | Get local HOTA domain for device. |
| [getNTPServer](arkts-mdm-systemmanager-getntpserver-f.md) | Obtains the NTP server information. This API is applicable to scenarios where you need to query the current NTP server address configured on the device, to verify whether the time synchronization configuration is correct, or to obtain the current configuration before making policy adjustments. |
| [getOtaUpdatePolicy](arkts-mdm-systemmanager-getotaupdatepolicy-f.md) | Checks the update policy. This API is applicable to scenarios where you need to obtain the current OTA update policy configuration of the device, to verify whether the policy is correctly delivered, or to obtain the current policy configuration before making policy adjustments. |
| [getUpdateAuthData](arkts-mdm-systemmanager-getupdateauthdata-f.md) | Obtains the authentication data for system update verification. This API uses a promise to return the result. This API is applicable to intranet update scenarios. Enterprise administrators can use the authentication data to verify the validity and integrity of the system update package, preventing malicious update packages and improving system security. |
| [getUpdateResult](arkts-mdm-systemmanager-getupdateresult-f.md) | Obtains the system update result. This API uses a promise to return the result. This API is applicable to scenarios where you need to check whether a system update is successful. It helps enterprise administrators understand the device update status and handle update failures in a timely manner to ensure that the device system version meets enterprise requirements. |
| [isActivationLockDisabled](arkts-mdm-systemmanager-isactivationlockdisabled-f.md) | Checks whether the device activation lock is disabled. This API is applicable to scenarios where you need to verify the device activation lock status. It helps enterprise administrators confirm the device's security configuration, especially when understanding the activation lock state is necessary for device transfer or recycling. |
| [isOtaUpdateNonceEnable](arkts-mdm-systemmanager-isotaupdatenonceenable-f.md) | Checks whether nonce is enabled for OTA update. This API is applicable to scenarios where you need to verify the OTA update security configuration on the device. It helps enterprise administrators confirm the status of the nonce verification feature to ensure system update security. |
| [notifyUpdatePackages](arkts-mdm-systemmanager-notifyupdatepackages-f.md) | Notifies the system of the update packages. In intranet updates, call this API to notify the system of the update packages, and then call [systemManager.setOtaUpdatePolicy](arkts-mdm-systemmanager-setotaupdatepolicy-f.md) to set the update policy. This API uses a promise to return the result. |
| [removeAllowedPrinterIPAddressesForAccount](arkts-mdm-systemmanager-removeallowedprinteripaddressesforaccount-f.md) | Removes allowed printer IP addresses for current account. The policy takes effect only for current account. |
| [removeAllowedPrinterIPAddressesForDevice](arkts-mdm-systemmanager-removeallowedprinteripaddressesfordevice-f.md) | Removes allowed printer IP addresses for device. The policy takes effect for all accounts. |
| [removeDisallowedNearLinkProtocols](arkts-mdm-systemmanager-removedisallowednearlinkprotocols-f.md) | Removes the list of disallowed NearLink protocols for a specified user. After successful removal, the specified user can use the removed NearLink protocols for communication again, restoring the corresponding protocol connection capabilities. Use cases: In enterprise device management scenarios, administrators can use this API to remove previously set NearLink protocol disabling policies, allowing users to resume communication between devices via NearLink protocols. This is suitable for scenarios where there is a need to restore NearLink communication capabilities for specific users, helping enterprise administrators flexibly adjust NearLink protocol access permissions of user devices to meet communication requirements in different business scenarios. |
| [removeKeyEventPolicies](arkts-mdm-systemmanager-removekeyeventpolicies-f.md) | Removes a key event handling policy. After the deletion is successful, the system restores the default handling behavior for the specified key event. This API is applicable to scenarios where there is a need to restore the default key behavior, helping enterprise administrators flexibly adjust device key response policies to meet the needs of different business scenarios. |
| [setActivationLockDisabled](arkts-mdm-systemmanager-setactivationlockdisabled-f.md) | Enables or disables the device activation lock. After the device activation lock is disabled, the Find Device function will no longer be available. This function is only available on certain devices. |
| [setAutoUnlockAfterReboot](arkts-mdm-systemmanager-setautounlockafterreboot-f.md) | Sets automatic unlocking upon device reboot. This setting takes effect only on devices without a screen lock password. This API is applicable to enterprise unattended devices or scenarios where services need to be quickly restored through a restart, avoiding device downtime caused by manual unlocking, thereby improving device operation and maintenance efficiency and service continuity. |
| [setInstallLocalEnterpriseAppEnabled](arkts-mdm-systemmanager-setinstalllocalenterpriseappenabled-f.md) | Sets whether local installation of enterprise applications is supported. When local installation is enabled, users can install enterprise applications (signing certificate distribution type: **enterprise_normal**) by double- tapping their installation packages on enterprise PCs/2-in-1 devices with the local installation capability. |
| [setInstallLocalEnterpriseAppEnabledForAccount](arkts-mdm-systemmanager-setinstalllocalenterpriseappenabledforaccount-f.md) | Sets whether local installation of enterprise applications is supported for a specified user. After the policy of supporting local enterprise application installation is delivered to a PC/2-in-1 enterprise device that has the local installation capability, the user can double-click an enterprise application installation package on the desktop or in the Files application to install it. |
| [setLocalHotaDomain](arkts-mdm-systemmanager-setlocalhotadomain-f.md) | Set the local HOTA domain of the device. |
| [setNTPServer](arkts-mdm-systemmanager-setntpserver-f.md) | Sets the Network Time Protocol (NTP) time server. After successful configuration, the system will use the specified NTP server for time synchronization to calibrate the system time. This API is suitable for scenarios where enterprise devices require unified time synchronization, ensuring that device time remains consistent with standard time and avoiding business issues caused by inaccurate time, such as inconsistent log timestamps and certificate validation failures. |
| [setOtaUpdateNonceEnable](arkts-mdm-systemmanager-setotaupdatenonceenable-f.md) | Sets whether to enable nonce for OTA update (nonce is enabled by default). When nonce is enabled, the system verifies the validity of the nonce during the OTA update process to prevent replay attacks and enhance system security. |
| [setOtaUpdatePolicy](arkts-mdm-systemmanager-setotaupdatepolicy-f.md) | Sets the update policy. After the setting is successful, the system performs OTA updates based on the specified policy type. Different policy types correspond to different update behaviors. In intranet updates, call [systemManager.notifyUpdatePackages](arkts-mdm-systemmanager-notifyupdatepackages-f.md) to notify the system of the update packages and then call this API to set the upgrade policy. |
| [startCollectLog](arkts-mdm-systemmanager-startcollectlog-f.md) | Starts to collect the fault logs of the [FaultType](../../apis-performance-analysis-kit/arkts-apis/arkts-performanceanalysis-faultlogger-faulttype-e.md) type that have been generated and stored on the device's hard disk. The fault logs, application service logs, and system runtime logs that are not stored on the hard disk cannot be collected. |
| [startExactTimer](arkts-mdm-systemmanager-startexacttimer-f.md) | Starts an exact timer. This API uses a promise to return the result. |
| [stopExactTimer](arkts-mdm-systemmanager-stopexacttimer-f.md) | Stops an exact timer. This API uses a promise to return the result. |

### Classes

| Name | Description |
| --- | --- |
| [ExactTimerConfig](arkts-mdm-systemmanager-exacttimerconfig-c.md) | Defines the initialization configuration for an exact timer. |

### Interfaces

| Name | Description |
| --- | --- |
| [ErrorInfo](arkts-mdm-systemmanager-errorinfo-i.md) | Represents the update error information. |
| [KeyEvent](arkts-mdm-systemmanager-keyevent-i.md) | Enumerates key events. When the [EnterpriseAdminExtensionAbility.onKeyEvent](arkts-mdm-enterprise-enterpriseadminextensionability-enterpriseadminextensionability-c.md#onkeyevent) key event callback is triggered, the current key event information is transferred. |
| [KeyEventPolicy](arkts-mdm-systemmanager-keyeventpolicy-i.md) | Enumerates key event handling policies. When a key event occurs, only the keys for which the key event handling policy has been delivered are intercepted. For key events where no handling policy has been delivered, the system executes its original response logic. |
| [KeyItem](arkts-mdm-systemmanager-keyitem-i.md) | Enumerates other key information. This refers to the information of other keys that have been pressed when the current [KeyCode](arkts-mdm-systemmanager-keycode-e.md) event occurs. |
| [NotifyDescription](arkts-mdm-systemmanager-notifydescription-i.md) | Represents the update notification defined by an enterprise. |
| [OtaUpdatePolicy](arkts-mdm-systemmanager-otaupdatepolicy-i.md) | Represents an OTA update policy. |
| [Package](arkts-mdm-systemmanager-package-i.md) | Represents the details about a system update package. |
| [PackageDescription](arkts-mdm-systemmanager-packagedescription-i.md) | Represents the description of a system update package. |
| [SystemUpdateInfo](arkts-mdm-systemmanager-systemupdateinfo-i.md) | Represents information about the system version to update. |
| [UpdatePackageInfo](arkts-mdm-systemmanager-updatepackageinfo-i.md) | Represents information about the system update packages. |
| [UpdateResult](arkts-mdm-systemmanager-updateresult-i.md) | Represents the update result information. |

### Enums

| Name | Description |
| --- | --- |
| [KeyAction](arkts-mdm-systemmanager-keyaction-e.md) | Enumerates key actions. |
| [KeyCode](arkts-mdm-systemmanager-keycode-e.md) | Key code. The [addKeyEventPolicies](arkts-mdm-systemmanager-addkeyeventpolicies-f.md), [removeKeyEventPolicies](arkts-mdm-systemmanager-removekeyeventpolicies-f.md), [getKeyEventPolicies](arkts-mdm-systemmanager-getkeyeventpolicies-f.md), and [onKeyEvent](arkts-mdm-enterprise-enterpriseadminextensionability-enterpriseadminextensionability-c.md#onkeyevent) APIs map key codes to the corresponding physical keys on the device. |
| [KeyPolicy](arkts-mdm-systemmanager-keypolicy-e.md) | Enumerates key policies. This refers to the system behavior triggered after the key code delivered by the MDM app matches the system key event. |
| [NearLinkProtocol](arkts-mdm-systemmanager-nearlinkprotocol-e.md) | Enumerates NearLink protocols. |
| [PackageType](arkts-mdm-systemmanager-packagetype-e.md) | Enumerates the update package types. |
| [PolicyType](arkts-mdm-systemmanager-policytype-e.md) | Enumerates the update policy types. |
| [UpdateStatus](arkts-mdm-systemmanager-updatestatus-e.md) | Enumerates the system update statuses. |
