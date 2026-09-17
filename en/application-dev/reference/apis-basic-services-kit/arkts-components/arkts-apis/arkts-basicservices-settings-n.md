# settings

This module provides settings data access abilities.

@namespace settings

**Since:** 18

**System capability:** SystemCapability.Applications.Settings.Core

## Modules to Import

```TypeScript
import { settings } from '@kit.BasicServicesKit';
```

## Summary

### Namespaces

| Name | Description |
| --- | --- |
| [domainName](arkts-basicservices-settings-domainname-n.md) | Provide domain name for query. |
| [date](arkts-basicservices-settings-date-n.md) | Provides methods for setting time and date formats. |
| [display](arkts-basicservices-settings-display-n.md) | Provides methods for setting the display effect, including the font size, screen brightness, screen rotation, animation factor, and display color. |
| [general](arkts-basicservices-settings-general-n.md) | Provides methods for setting general information about devices, including the device name, startup wizard, airplane mode, debugging information, accessibility feature switch, and touch exploration status. |
| [input](arkts-basicservices-settings-input-n.md) | Provides methods for setting information about input methods, including automatic capitalization, automatic punctuation, autocorrect, password presentation, input method engine, and input method subtypes. |
| [network](arkts-basicservices-settings-network-n.md) | Provides methods for setting network information, including the data roaming status, HTTP proxy configurations, and preferred networks. |
| [phone](arkts-basicservices-settings-phone-n.md) | Provides methods for setting the answering mode of incoming and outgoing calls. |
| [sound](arkts-basicservices-settings-sound-n.md) | Provides methods for setting the sound effect, including the ringtone, dial tone, alarm sound, notification tone, and haptic feedback. |
| [TTS](arkts-basicservices-settings-tts-n.md) | Provides methods for setting information about text-to-speech (TTS) conversion, including the pitch, speech rate, engine, and plug-ins. |
| [wireless](arkts-basicservices-settings-wireless-n.md) | Provides methods for setting radio network information, including information about Bluetooth, Wi-Fi, Near Field Communication (NFC), and the airplane mode. |

### Functions

| Name | Description |
| --- | --- |
| [getURI](arkts-basicservices-settings-geturi-f.md) | Constructs a URI for a specific name-value pair for monitoring data of the ability that uses the Data template. |
| [getURI](arkts-basicservices-settings-geturi-f.md) | Constructs a URI for a specific name-value pair for monitoring data of the ability that uses the Data template. |
| [getValue](arkts-basicservices-settings-getvalue-f.md) | Obtains the value of a specified character string in the database. |
| [getValue](arkts-basicservices-settings-getvalue-f.md) | Obtains the value of a specified character string in the database. |
| [getValue](arkts-basicservices-settings-getvalue-f.md) | Get value from settingsdata |
| [getValue](arkts-basicservices-settings-getvalue-f.md) | Get value from settingsdata |
| [getValue](arkts-basicservices-settings-getvalue-f.md) | Get value from settingsdata [USER_SECURE] domain need ohos.permission.MANAGE_SECURE_SETTINGS permission. |
| [setValue](arkts-basicservices-settings-setvalue-f.md) | Set settingsdata value. |
| [setValue](arkts-basicservices-settings-setvalue-f.md) | Set settingsdata value. |
| [setValue](arkts-basicservices-settings-setvalue-f.md) | Set settingsdata value. [DEVICE_SHARED, USER_PROPERTY] domain need ohos.permission.MANAGE_SETTINGS permission. [USER_SECURE] domain need ohos.permission.MANAGE_SECURE_SETTINGS permission. |
| [enableAirplaneMode](arkts-basicservices-settings-enableairplanemode-f.md) | Enables or disables airplane mode. |
| [enableAirplaneMode](arkts-basicservices-settings-enableairplanemode-f.md) | Enables or disables airplane mode. |
| [canShowFloating](arkts-basicservices-settings-canshowfloating-f.md) | Checks whether a specified application can show as a floating window. |
| [canShowFloating](arkts-basicservices-settings-canshowfloating-f.md) | Checks whether a specified application can show as a floating window. |
| [getUriSync](arkts-basicservices-settings-geturisync-f.md) | Get settingsdata uri (synchronous method) |
| [getValueSync](arkts-basicservices-settings-getvaluesync-f.md) | Get value from settingsdata(synchronous method) |
| [getValueSync](arkts-basicservices-settings-getvaluesync-f.md) | Get value from settingsdata(synchronous method) |
| [getValueSync](arkts-basicservices-settings-getvaluesync-f.md) | Get value from settingsdata(synchronous method). [USER_SECURE] domain need ohos.permission.MANAGE_SECURE_SETTINGS permission. |
| [setValueSync](arkts-basicservices-settings-setvaluesync-f.md) | Set settingsdata value(synchronous method) |
| [setValueSync](arkts-basicservices-settings-setvaluesync-f.md) | Set settingsdata value(synchronous method) |
| [setValueSync](arkts-basicservices-settings-setvaluesync-f.md) | Set settingsdata value(synchronous method). [DEVICE_SHARED, USER_PROPERTY] domain need ohos.permission.MANAGE_SETTINGS permission. [USER_SECURE] domain need ohos.permission.MANAGE_SECURE_SETTINGS permission. |
| [registerKeyObserver](arkts-basicservices-settings-registerkeyobserver-f.md) | Monitor registration key(synchronous method) [USER_SECURE] domain need ohos.permission.MANAGE_SECURE_SETTINGS permission. |
| [unregisterKeyObserver](arkts-basicservices-settings-unregisterkeyobserver-f.md) | Monitor unregister key(synchronous method) [USER_SECURE] domain need ohos.permission.MANAGE_SECURE_SETTINGS permission. |
| [openNetworkManagerSettings](arkts-basicservices-settings-opennetworkmanagersettings-f.md) | Open the network manager settings page. |
| [openInputMethodSettings](arkts-basicservices-settings-openinputmethodsettings-f.md) | Open the input method settings page. |
| [openInputMethodDetail](arkts-basicservices-settings-openinputmethoddetail-f.md) | Open the input method detail page. |
| [openMobileNetworkSettingsPage](arkts-basicservices-settings-openmobilenetworksettingspage-f.md) | Open the mobile network settings page. |
| [openDisplaySettingsPage](arkts-basicservices-settings-opendisplaysettingspage-f.md) | Open the display settings page. |
| [openScreenRefreshRateSettingsPage](arkts-basicservices-settings-openscreenrefreshratesettingspage-f.md) | Open the screen refresh rate settings page. |
| [openSoundSettingsPage](arkts-basicservices-settings-opensoundsettingspage-f.md) | Open the sound settings page. |
| [openBiometricsSettingsPage](arkts-basicservices-settings-openbiometricssettingspage-f.md) | Open the biometrics and password settings page. |
| [openAboutDeviceSettingsPage](arkts-basicservices-settings-openaboutdevicesettingspage-f.md) | Open the about device settings page. |
| [openNfcSettingsPage](arkts-basicservices-settings-opennfcsettingspage-f.md) | Open the NFC settings page. |
| [openAppDetailSettingsPage](arkts-basicservices-settings-openappdetailsettingspage-f.md) | Open the app detail settings page. |
| [openDoubleClickSettingsPage](arkts-basicservices-settings-opendoubleclicksettingspage-f.md) | 1. Opens the settings page for double-pressing the Down key. 2. This API is used to set the default application started by double-pressing the Down key. |
| [isDoubleClickAppForSelf](arkts-basicservices-settings-isdoubleclickappforself-f.md) | 1. Checks whether the application started by double-pressing the Down key is the application itself. 2. This API is triggered to check whether double-pressing the Down key starts the application itself. |

<!--Del-->
### Functions(System API)

| Name | Description |
| --- | --- |
| [setValue](arkts-basicservices-settings-setvalue-f-sys.md) | Saves a character string name and its value to the database. |
| [setValue](arkts-basicservices-settings-setvalue-f-sys.md) | Saves a character string name and its value to the database. |
<!--DelEnd-->
