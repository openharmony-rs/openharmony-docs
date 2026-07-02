# @ohos.bundle.shortcutManager (shortcutManager Module)

<!--Kit: Ability Kit-->
<!--Subsystem: BundleManager-->
<!--Owner: @wanghang904-->
<!--Designer: @hanfeng6-->
<!--Tester: @kongjing2-->
<!--Adviser: @HelloCrease-->
<!-- md-trans-meta sourceCommit=7eb6f57046c125c4e13d8acd776d3cbaf09f5103 translatedAt=2026-06-22T06:57:27.090Z pushedAt=2026-06-25T06:31:35.533Z -->

This module provides the application's management capabilities for [shortcuts](../../quick-start/typical-scenario-configuration.md), including setting whether a shortcut is displayed. Through shortcuts, users can quickly launch specific features of an app from the home screen, improving the app's ease of use and user retention. Typical usage scenarios include: providing users with quick access to frequently used features, dynamically adjusting the display of shortcuts based on user habits, etc.

> **NOTE**
>
> The initial APIs of this module are supported since API version 20. Newly added APIs will be marked with a superscript to indicate their earliest API version.

## Modules to Import

```ts
import { shortcutManager } from '@kit.AbilityKit';
```

## shortcutManager.setShortcutVisibleForSelf

setShortcutVisibleForSelf(id: string, visible: boolean) : Promise\<void>

Sets whether to display the specified shortcut for the current application. This API uses a promise to return the result.

**System capability**: SystemCapability.BundleManager.BundleFramework.Launcher

**Parameters**

| Name    | Type  | Mandatory| Description        |
| ---------- | ------ | ---- | -------------- |
| id         | string | Yes  | Shortcut ID, which is the value of the **shortcutId** field under the **shortcuts** tag in the [module.json5](../../quick-start/module-configuration-file.md) file. The value is a string of up to 63 bytes.|
| visible    | boolean| Yes  | Whether to display the shortcut. **true** to display, **false** otherwise.|

**Return value**

| Type            | Description             |
| -------------- | --------------- |
| Promise\<void> | Promise that returns no value. |

**Error codes**

For details about the error codes, see [Bundle Error Codes](errorcode-bundle.md).

| ID| Error Message                                |
| -------- | ---------------------------------------- |
| 17700070 | The specified shortcut id is illegal. |

**Example**

```ts
import { shortcutManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

// Replace it with the shortcutId field under the shortcuts tag of the module.json5 file.
shortcutManager.setShortcutVisibleForSelf("shortcut_id", false)
  .then(() => {
    console.info('setShortcutVisibleForSelf success');
  }).catch((err: BusinessError) => {
  console.error(`setShortcutVisibleForSelf errData is errCode:${err.code}  message:${err.message}`);
});
```

## shortcutManager.getAllShortcutInfoForSelf

getAllShortcutInfoForSelf(): Promise\<Array\<ShortcutInfo>>

Obtains all the shortcut information defined in the [configuration](../../quick-start/module-configuration-file.md#shortcuts) file of the current application. This API uses a promise to return the result.

**System capability**: SystemCapability.BundleManager.BundleFramework.Launcher

**Return value**

| Type                                                        | Description                                                        |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| Promise<Array\<[ShortcutInfo](js-apis-bundleManager-shortcutInfo.md)>> | Promise that returns all the shortcut information defined in the configuration file.|

**Example**

```ts
import { shortcutManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

shortcutManager.getAllShortcutInfoForSelf()
  .then((data: shortcutManager.ShortcutInfo[]) => {
    console.info('getAllShortcutInfoForSelf shortcut data is' + JSON.stringify(data));
  }).catch((err: BusinessError) => {
  console.error(`getAllShortcutInfoForSelf errData is errCode:${err.code}  message:${err.message}`);
});
```

## shortcutManager.isShortcutSupported

isShortcutSupported(): boolean

Checks whether the current device supports shortcuts.

**Since:** 26.0.0

**System capability:** SystemCapability.BundleManager.BundleFramework.Launcher

**Model restriction**: This API can be used only in the stage model.

**Return value**

| Type                                                         | Description                                                         |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| boolean | Indicates whether the current device supports shortcuts.<br/>The return value **true** indicates that the current device supports shortcuts; the return value **false** indicates that the current device does not support shortcuts. |

**Example**

```ts
import { shortcutManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let data = shortcutManager.isShortcutSupported();
  console.info('isShortcutSupported data is' + JSON.stringify(data));
} catch (err) {
  let message = (err as BusinessError).message;
  console.error(`isShortcutSupported errData is errCode:${err.code}  message:${err.message}`);
}
```

## ShortcutInfo

type ShortcutInfo = _ShortcutInfo

Defines the shortcut information defined in the [module.json5](../../quick-start/module-configuration-file.md#shortcuts) file of the application.

**System capability**: SystemCapability.BundleManager.BundleFramework.Launcher

| Type                                                        | Description          |
| ------------------------------------------------------------ | -------------- |
| [_ShortcutInfo](./js-apis-bundleManager-shortcutInfo.md#shortcutinfo-1) | Shortcut information defined in the configuration file.|

## ShortcutWant

type ShortcutWant = _ShortcutWant

Defines the target [wants](../../quick-start/module-configuration-file.md#wants) defined in the shortcut configuration.

**System capability**: SystemCapability.BundleManager.BundleFramework.Launcher

| Type                                                        | Description          |
| ------------------------------------------------------------ | -------------- |
| [_ShortcutWant](./js-apis-bundleManager-shortcutInfo.md#shortcutwant) | Target [wants](../../quick-start/module-configuration-file.md#wants) defined in the shortcut configuration.|

## ParameterItem

type ParameterItem = _ParameterItem

Defines the custom data in the shortcut configuration.

**System capability**: SystemCapability.BundleManager.BundleFramework.Launcher

| Type                                                        | Description          |
| ------------------------------------------------------------ | -------------- |
| [_ParameterItem](./js-apis-bundleManager-shortcutInfo.md#parameteritem) | Custom data in the shortcut configuration.|