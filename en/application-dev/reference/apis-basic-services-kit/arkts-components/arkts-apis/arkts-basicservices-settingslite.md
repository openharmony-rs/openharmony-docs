# @ohos.settingsLite

Defines the lite settings capability for wearables.

**Since:** 24

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Applications.Settings.Core.Lite

## Modules to Import

```TypeScript
import { settingsLite } from '@kit.BasicServicesKit';
```

## Summary

### Functions

| Name | Description |
| --- | --- |
| [isDoubleClickAppForSelf](arkts-basicservices-settingslite-isdoubleclickappforself-f.md) | 1. Checks whether the application started by double-pressing the function key is the application itself. 2. This API is triggered to check whether double-pressing the function key starts the application itself. |
| [openDoubleClickSettingsPage](arkts-basicservices-settingslite-opendoubleclicksettingspage-f.md) | Opens the settings page for double-pressing the function key. |
| [openNfcSettingsPage](arkts-basicservices-settingslite-opennfcsettingspage-f.md) | Opens the NFC settings page. |
| [openPinSettingPage](arkts-basicservices-settingslite-openpinsettingpage-f.md) | Opens the password settings page. |

### Interfaces

| Name | Description |
| --- | --- |
| [ClickCallback](arkts-basicservices-settingslite-clickcallback-i.md) | Defines a callback used to return whether the application started by double-pressing the function key is the application itself. |
