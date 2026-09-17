# @ohos.enterprise.deviceSettings(Device Settings Management)

This module provides enterprise device settings capabilities, including setting and obtaining the device screen-off time, system time, power policy, Eye Comfort mode, default input method, wallpaper, and hidden setting items.

> **NOTE:** 
> 
> The APIs of this module can be called only by a device administrator application that is enabled. For details, see
> [MDM Kit Development](../../../mdm/mdm-kit-guide.md).

**Since:** 12

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

## Modules to Import

```TypeScript
import { deviceSettings } from '@kit.MDMKit';
```

## Summary

### Functions

| Name | Description |
| --- | --- |
| [addHiddenSettingsMenu](arkts-mdm-devicesettings-addhiddensettingsmenu-f.md) | Adds a setting item to the hidden setting item list of the current user. Then the setting item is hidden in the current user's settings menu and cannot be found in settings search. Even if the setting item is located through some means, it cannot be opened when tapped. The settings take effect immediately after the API is called. The Settings application does not need to be restarted. |
| [getHiddenSettingsMenu](arkts-mdm-devicesettings-gethiddensettingsmenu-f.md) | Obtains the hidden setting item list of the current user. |
| [getValue](arkts-mdm-devicesettings-getvalue-f.md) | Obtains a device setting policy. |
| [getValueForAccount](arkts-mdm-devicesettings-getvalueforaccount-f.md) | Obtains the device policy of a specified user. This API allows you to obtain a specific parameter of a given user, such as obtaining the device name of user 100. |
| [removeHiddenSettingsMenu](arkts-mdm-devicesettings-removehiddensettingsmenu-f.md) | Removes a setting item from the hidden setting item list of the current user. Setting items in the hidden setting item list are hidden in the current user's settings menu and cannot be found in settings search. Even if a setting item is located through some means, it cannot be opened when tapped. If the remaining hidden setting item list is empty after the removal, all setting items are displayed. The settings take effect immediately after the API is called. The Settings application does not need to be restarted. |
| [setHomeWallpaper](arkts-mdm-devicesettings-sethomewallpaper-f.md) | Sets the home screen wallpaper. This API uses a promise to return the result. |
| [setSwitchStatus](arkts-mdm-devicesettings-setswitchstatus-f.md) | Sets the state of a switch. This API can enable or disable NearLink, Bluetooth, Wi-Fi, and NFC. After the setting is applied, users can manually enable or disable them. Bluetooth and NFC can be forced on. Once set, they cannot be manually turned on or off by the user. If a switch has been disabled through the [setDisallowedPolicy](arkts-mdm-restrictions-setdisallowedpolicy-f.md) API, error code 203 will be reported when you attempt to set the state of the switch through this API. In this case, you need to use the [setDisallowedPolicy](arkts-mdm-restrictions-setdisallowedpolicy-f.md) API to enable the switch. When multiple MDM applications are present on the device, there are no conflicts among the switch states set by different MDM applications. The policy set last takes effect. The three states, on (user can manually enable /disable), off (user can manually enable/disable), and forced on (user cannot manually disable), can be switched arbitrarily, and no conflict occurs. |
| [setUnlockWallpaper](arkts-mdm-devicesettings-setunlockwallpaper-f.md) | Sets the lock screen wallpaper. This API uses a promise to return the result. Enterprise device administrator applications can use this API to uniformly set the lock screen wallpaper for enterprise devices, for purposes such as corporate branding or security control. |
| [setValue](arkts-mdm-devicesettings-setvalue-f.md) | Sets the device policy. |
| [setValueForAccount](arkts-mdm-devicesettings-setvalueforaccount-f.md) | Sets the device policy for a specified user. This API allows you to set a specific parameter for a given user, such as setting the device name for user 100. |

<!--Del-->
### Functions(System API)

| Name | Description |
| --- | --- |
| [getPowerPolicy](arkts-mdm-devicesettings-getpowerpolicy-f-sys.md) | Obtains the power policy. |
| [getScreenOffTime](arkts-mdm-devicesettings-getscreenofftime-f-sys.md) | Obtains the device screen-off time. This API uses an asynchronous callback to return the result. |
| [getScreenOffTime](arkts-mdm-devicesettings-getscreenofftime-f-sys.md) | Obtains the device screen-off time. This API uses an asynchronous promise to return the result. |
| [installUserCertificate](arkts-mdm-devicesettings-installusercertificate-f-sys.md) | Installs a user certificate. This API uses a callback to return the result. |
| [installUserCertificate](arkts-mdm-devicesettings-installusercertificate-f-sys.md) | Installs a user certificate. This API uses a promise to return the result. |
| [setPowerPolicy](arkts-mdm-devicesettings-setpowerpolicy-f-sys.md) | Sets the power policy. |
| [setScreenOffTime](arkts-mdm-devicesettings-setscreenofftime-f-sys.md) | Sets the device screen-off time. |
| [uninstallUserCertificate](arkts-mdm-devicesettings-uninstallusercertificate-f-sys.md) | Uninstalls a user certificate. This API uses a callback to return the result. |
| [uninstallUserCertificate](arkts-mdm-devicesettings-uninstallusercertificate-f-sys.md) | Uninstalls a user certificate. This API uses a promise to return the result. |
<!--DelEnd-->

<!--Del-->
### Interfaces(System API)

| Name | Description |
| --- | --- |
| [CertBlob](arkts-mdm-devicesettings-certblob-i-sys.md) | Represents the certificate information. |
| [PowerPolicy](arkts-mdm-devicesettings-powerpolicy-i-sys.md) | Represents the power policy. |
<!--DelEnd-->

### Enums

| Name | Description |
| --- | --- |
| [SettingsItem](arkts-mdm-devicesettings-settingsitem-e.md) | Policy type. |
| [SettingsMenu](arkts-mdm-devicesettings-settingsmenu-e.md) | Describes the setting item list. |
| [SwitchKey](arkts-mdm-devicesettings-switchkey-e.md) | Enumerates switch names. |
| [SwitchStatus](arkts-mdm-devicesettings-switchstatus-e.md) | Enumerates switch states. |

<!--Del-->
### Enums(System API)

| Name | Description |
| --- | --- |
| [PowerPolicyAction](arkts-mdm-devicesettings-powerpolicyaction-e-sys.md) | Enumerates the actions that can be performed to apply the power policy. |
| [PowerScene](arkts-mdm-devicesettings-powerscene-e-sys.md) | Defines the scenario to which the power policy applies. |
<!--DelEnd-->
