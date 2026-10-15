# @ohos.uiAppearance(UI Appearance)

This module provides basic capabilities for obtaining system appearance configurations, including color mode (dark/ light) settings, font size scale factors, and font weight scale factors. It is applicable to scenarios where the application UI style needs to be dynamically adjusted based on the system appearance configuration (such as dark/ light mode switching), as well as adapting to the system font size and font weight scale settings. This helps applications maintain consistency with the system appearance and improves user experience.

**Since:** 20

<!--Device-unnamed-declare namespace uiAppearance--><!--Device-unnamed-declare namespace uiAppearance-End-->

**System capability:** SystemCapability.ArkUI.UiAppearance

## Modules to Import

```TypeScript
import { uiAppearance } from '@kit.ArkUI';
```

## Summary

### Functions

| Name | Description |
| --- | --- |
| [getDarkMode](arkts-arkui-uiappearance-getdarkmode-f.md#getdarkmode) | Obtains the current system color mode configuration. This API is applicable to scenarios where the application UI theme needs to be dynamically adapted based on the system appearance mode, such as implementing automatic switching between dark and light theme styles within the application. |
| [getFontScale](arkts-arkui-uiappearance-getfontscale-f.md#getfontscale) | Obtains the current font size scale factor. This scale is the ratio of the font size configured by the user in system settings to the default font size. For the value range, refer to the system font size settings. You can adjust the font size within the application based on this scale factor to accommodate the user's font size preferences. |
| [getFontWeightScale](arkts-arkui-uiappearance-getfontweightscale-f.md#getfontweightscale) | Obtains the current font weight scale factor. This scale is the ratio of the font weight configured by the user in system settings to the default font weight. For the value range, refer to the system font weight settings. You can adjust the font weight within the application based on this scale factor to accommodate the user's font weight preferences. |

<!--Del-->
### Functions(System API)

| Name | Description |
| --- | --- |
| [setDarkMode](arkts-arkui-uiappearance-setdarkmode-f-sys.md#setdarkmode1) | Sets the system color mode. This API uses an asynchronous callback to return the result. |
| [setDarkMode](arkts-arkui-uiappearance-setdarkmode-f-sys.md#setdarkmode2) | Sets the system color mode. This API uses a promise to return the result. |
| [setFontScale](arkts-arkui-uiappearance-setfontscale-f-sys.md#setfontscale) | Sets the system font scale. |
| [setFontWeightScale](arkts-arkui-uiappearance-setfontweightscale-f-sys.md#setfontweightscale) | Sets the system font weight scale. |
<!--DelEnd-->

### Enums

| Name | Description |
| --- | --- |
| [DarkMode](arkts-arkui-uiappearance-darkmode-e.md) | Enumerates the color modes, used to configure the dark or light mode of the system. |
