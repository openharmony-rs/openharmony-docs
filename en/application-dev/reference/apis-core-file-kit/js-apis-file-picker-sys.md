# @ohos.file.picker (Picker) (System API)
<!--Kit: Core File Kit-->
<!--Subsystem: FileManagement-->
<!--Owner: @yangwei_814916-->
<!--Designer: @hwzhangchuang; @Dyylll-->
<!--Tester: @zsyztt; @yue-ye2; @fuwei-->
<!--Adviser: @jinqiuheng-->
<!-- md-trans-meta sourceCommit=8b6cf89b37c32b3dffd1d378ad719228fa45e034 translatedAt=2026-11-10T05:12:06.156Z pushedAt=2026-11-10T07:38:12.857Z nl=1 -->

Picker is an API module that encapsulates DocumentViewPicker, AudioViewPicker, and PhotoViewPicker, providing the capabilities of selecting and saving. Through Picker, the system file selection UI is launched, allowing users to select or save files in a secure and controllable environment. Applications can use this API without applying for any permission. Applications can choose to use the following APIs to implement file selection and saving. These APIs must be called in the UIAbility context; otherwise, the FilePicker, AudioPicker, or PhotoPicker application cannot be launched.
> **NOTE**
>
> - This module is supported since API version 9. Newly added content in later versions is marked with a superscript to indicate the initial version of the content.
> - This page contains only the system APIs of this module. For other public APIs, see [@ohos.file.picker (picker)](js-apis-file-picker.md).

## Modules to Import

```ts
import { picker } from '@kit.CoreFileKit';
```

## DocumentSelectOptions

Defines the options for selecting documents.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System API**: This is a system API.

**System capability**: SystemCapability.FileManagement.UserFileService

| Name                   | Type                                        | Read-Only | Optional | Description                                    |
| :---------------------- |---------------------------------------------| ---- | ---- |------------------------------------------|
| themeColor<sup>18+</sup>     | [CustomColors](../apis-arkui/js-apis-arkui-theme.md#customcolors) |  No  |  Yes |Theme color parameter, empty by default, following the FilePicker application color. When themeColor is set to a specific theme color attribute ([brand, fontPrimary, compBackgroundEmphasize, iconFourth](../apis-arkui/js-apis-arkui-theme.md#colors)), the launched FilePicker application displays the corresponding interface color scheme according to the passed Theme Color Parameter; when set to other attributes, no adaptation effect is produced, and the FilePicker application default color is still followed.<br> **Device behavior difference**: This parameter takes effect normally on Phone devices, while setting it on other devices produces no visual effect (without affecting the normal invocation of the Picker itself). Developers can obtain the device type through deviceInfo.deviceType for judgment. |

## DocumentSaveOptions

Defines the options for saving documents.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System API**: This is a system API.

**System capability**: SystemCapability.FileManagement.UserFileService

| Name                   | Type                                         |  Read-Only | Optional |Description                                      |
| :---------------------- |---------------------------------------------| ----- |--------| ------------------------------------------|
| themeColor<sup>18+</sup>     | [CustomColors](../apis-arkui/js-apis-arkui-theme.md#customcolors) |  No   | Yes | Theme color parameter, empty by default, following the FilePicker application color. When themeColor is set to specific theme color attributes ([fontEmphasize, compBackgroundEmphasize](../apis-arkui/js-apis-arkui-theme.md#colors)), the launched FilePicker application displays the corresponding interface color scheme according to the passed Theme Color Parameter; when set to other attributes, no adaptation effect is produced, and the FilePicker application default color is still followed.<br> **Device behavior difference**: This parameter takes effect normally on Phone devices, while setting it on other devices produces no visual effect (without affecting the normal invocation of the Picker itself). Developers can obtain the device type through deviceInfo.deviceType for judgment. |
