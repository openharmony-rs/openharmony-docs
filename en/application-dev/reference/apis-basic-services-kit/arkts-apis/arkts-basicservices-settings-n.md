# settings

```TypeScript
declare namespace settings
```

This module provides settings data access abilities.

**Since:** 18

<!--Device-unnamed-declare namespace settings--><!--Device-unnamed-declare namespace settings-End-->

**System capability:** SystemCapability.Applications.Settings.Core

## Modules to Import

```TypeScript
import { settings } from '@kit.BasicServicesKit';
```

## Summary

### Namespaces

| Name | Description |
| --- | --- |
| [date](arkts-basicservices-settings-date-n.md) | Provides methods for setting time and date formats. |
| [display](arkts-basicservices-settings-display-n.md) | Provides methods for setting the display effect, including the font size, screen brightness, screen rotation, animation factor, and display color. |
| [domainName](arkts-basicservices-settings-domainname-n.md) | Provide domain name for query. |
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
| [getValue](arkts-basicservices-settings-getvalue-f.md#getvalue) | Get value from settingsdata |
| [getValue](arkts-basicservices-settings-getvalue-f.md#getvalue) | Get value from settingsdata |
| [getValue](arkts-basicservices-settings-getvalue-f.md#getvalue) | Get value from settingsdata [USER_SECURE] domain need ohos.permission.MANAGE_SECURE_SETTINGS permission. |
| [getValueSync](arkts-basicservices-settings-getvaluesync-f.md#getvaluesync) | Get value from settingsdata(synchronous method) |
| [getValueSync](arkts-basicservices-settings-getvaluesync-f.md#getvaluesync) | Get value from settingsdata(synchronous method). [USER_SECURE] domain need ohos.permission.MANAGE_SECURE_SETTINGS permission. |
| [isDoubleClickAppForSelf](arkts-basicservices-settings-isdoubleclickappforself-f.md#isdoubleclickappforself) | 1. Checks whether the application started by double-pressing the Down key is the application itself. 2. This API is triggered to check whether double-pressing the Down key starts the application itself. |
| [openAboutDeviceSettingsPage](arkts-basicservices-settings-openaboutdevicesettingspage-f.md#openaboutdevicesettingspage) | Open the about device settings page. |
| [openAppDetailSettingsPage](arkts-basicservices-settings-openappdetailsettingspage-f.md#openappdetailsettingspage) | Open the app detail settings page. |
| [openBiometricsSettingsPage](arkts-basicservices-settings-openbiometricssettingspage-f.md#openbiometricssettingspage) | Open the biometrics and password settings page. |
| [openDisplaySettingsPage](arkts-basicservices-settings-opendisplaysettingspage-f.md#opendisplaysettingspage) | Open the display settings page. |
| [openDoubleClickSettingsPage](arkts-basicservices-settings-opendoubleclicksettingspage-f.md#opendoubleclicksettingspage) | 1. Opens the settings page for double-pressing the Down key. 2. This API is used to set the default application started by double-pressing the Down key. |
| [openInputMethodDetail](arkts-basicservices-settings-openinputmethoddetail-f.md#openinputmethoddetail) | Open the input method detail page. |
| [openInputMethodSettings](arkts-basicservices-settings-openinputmethodsettings-f.md#openinputmethodsettings) | Open the input method settings page. |
| [openMobileNetworkSettingsPage](arkts-basicservices-settings-openmobilenetworksettingspage-f.md#openmobilenetworksettingspage) | Open the mobile network settings page. |
| [openNetworkManagerSettings](arkts-basicservices-settings-opennetworkmanagersettings-f.md#opennetworkmanagersettings) | Open the network manager settings page. |
| [openNfcSettingsPage](arkts-basicservices-settings-opennfcsettingspage-f.md#opennfcsettingspage) | Open the NFC settings page. |
| [openScreenRefreshRateSettingsPage](arkts-basicservices-settings-openscreenrefreshratesettingspage-f.md#openscreenrefreshratesettingspage) | Open the screen refresh rate settings page. |
| [openSoundSettingsPage](arkts-basicservices-settings-opensoundsettingspage-f.md#opensoundsettingspage) | Open the sound settings page. |
| [registerKeyObserver](arkts-basicservices-settings-registerkeyobserver-f.md#registerkeyobserver) | Monitor registration key(synchronous method) [USER_SECURE] domain need ohos.permission.MANAGE_SECURE_SETTINGS permission. |
| [setValue](arkts-basicservices-settings-setvalue-f.md#setvalue) | Set settingsdata value. |
| [setValue](arkts-basicservices-settings-setvalue-f.md#setvalue) | Set settingsdata value. |
| [setValue](arkts-basicservices-settings-setvalue-f.md#setvalue) | Set settingsdata value. [DEVICE_SHARED, USER_PROPERTY] domain need ohos.permission.MANAGE_SETTINGS permission. [USER_SECURE] domain need ohos.permission.MANAGE_SECURE_SETTINGS permission. |
| [setValueSync](arkts-basicservices-settings-setvaluesync-f.md#setvaluesync) | Set settingsdata value(synchronous method) |
| [setValueSync](arkts-basicservices-settings-setvaluesync-f.md#setvaluesync) | Set settingsdata value(synchronous method). [DEVICE_SHARED, USER_PROPERTY] domain need ohos.permission.MANAGE_SETTINGS permission. [USER_SECURE] domain need ohos.permission.MANAGE_SECURE_SETTINGS permission. |
| [unregisterKeyObserver](arkts-basicservices-settings-unregisterkeyobserver-f.md#unregisterkeyobserver) | Monitor unregister key(synchronous method) [USER_SECURE] domain need ohos.permission.MANAGE_SECURE_SETTINGS permission. |
| [canShowFloating](arkts-basicservices-settings-canshowfloating-f.md#canshowfloating) | Checks whether a specified application can show as a floating window. |
| [canShowFloating](arkts-basicservices-settings-canshowfloating-f.md#canshowfloating) | Checks whether a specified application can show as a floating window. |
| [enableAirplaneMode](arkts-basicservices-settings-enableairplanemode-f.md#enableairplanemode) | Enables or disables airplane mode. |
| [enableAirplaneMode](arkts-basicservices-settings-enableairplanemode-f.md#enableairplanemode) | Enables or disables airplane mode. |
| [getURI](arkts-basicservices-settings-geturi-f.md#geturi) | Constructs a URI for a specific name-value pair for monitoring data of the ability that uses the Data template. |
| [getURI](arkts-basicservices-settings-geturi-f.md#geturi) | Constructs a URI for a specific name-value pair for monitoring data of the ability that uses the Data template. |
| [getUriSync](arkts-basicservices-settings-geturisync-f.md#geturisync) | Get settingsdata uri (synchronous method) |
| [getValue](arkts-basicservices-settings-getvalue-f.md#getvalue) | Obtains the value of a specified character string in the database. |
| [getValue](arkts-basicservices-settings-getvalue-f.md#getvalue) | Obtains the value of a specified character string in the database. |
| [getValueSync](arkts-basicservices-settings-getvaluesync-f.md#getvaluesync) | Get value from settingsdata(synchronous method) |
| [setValueSync](arkts-basicservices-settings-setvaluesync-f.md#setvaluesync) | Set settingsdata value(synchronous method) |

<!--Del-->
### Functions(System API)

| Name | Description |
| --- | --- |
| [setValue](arkts-basicservices-settings-setvalue-f-sys.md#setvalue) | Saves a character string name and its value to the database. |
| [setValue](arkts-basicservices-settings-setvalue-f-sys.md#setvalue) | Saves a character string name and its value to the database. |
<!--DelEnd-->
