# @ohos.bundle.shortcutManager(shortcutManager Module)

This module provides system applications with the capabilities of adding, deleting, and querying shortcuts, including adding, deleting, and querying [ShortcutInfo](arkts-ability-shortcutinfo-i.md) information.

**Since:** 20

<!--Device-unnamed-declare namespace shortcutManager--><!--Device-unnamed-declare namespace shortcutManager-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Launcher

## Modules to Import

```TypeScript
import { shortcutManager } from '@kit.AbilityKit';
```

## Summary

### Functions

| Name | Description |
| --- | --- |
| [getAllShortcutInfoForSelf](arkts-ability-shortcutmanager-getallshortcutinfoforself-f.md#getallshortcutinfoforself) | Obtains all the shortcut information defined in the [configuration](../../../quick-start/module-configuration-file.md#shortcuts) file of the current application. This API uses a promise to return the result. |
| [isShortcutSupported](arkts-ability-shortcutmanager-isshortcutsupported-f.md#isshortcutsupported) | Checks whether the current device supports shortcuts. |
| [setShortcutVisibleForSelf](arkts-ability-shortcutmanager-setshortcutvisibleforself-f.md#setshortcutvisibleforself) | Sets whether to display the specified shortcut for the current application. This API uses a promise to return the result. |

<!--Del-->
### Functions(System API)

| Name | Description |
| --- | --- |
| [addDesktopShortcutInfo](arkts-ability-shortcutmanager-adddesktopshortcutinfo-f-sys.md#adddesktopshortcutinfo) | Adds a shortcut for the given user. This API uses a promise to return the result. |
| [addDynamicShortcutInfos](arkts-ability-shortcutmanager-adddynamicshortcutinfos-f-sys.md#adddynamicshortcutinfos) | Adds dynamic shortcuts for the given user. |
| [deleteDesktopShortcutInfo](arkts-ability-shortcutmanager-deletedesktopshortcutinfo-f-sys.md#deletedesktopshortcutinfo) | Deletes a shortcut for the given user. This API uses a promise to return the result. |
| [deleteDynamicShortcutInfos](arkts-ability-shortcutmanager-deletedynamicshortcutinfos-f-sys.md#deletedynamicshortcutinfos) | Deletes dynamic shortcuts. |
| [getAllDesktopShortcutInfo](arkts-ability-shortcutmanager-getalldesktopshortcutinfo-f-sys.md#getalldesktopshortcutinfo) | Obtains the information about all shortcuts of the given user. |
| [getShortcutInfoByAbility](arkts-ability-shortcutmanager-getshortcutinfobyability-f-sys.md#getshortcutinfobyability) | Queries the shortcut information of a specified UIAbility under a specified user. |
| [setShortcutsEnabled](arkts-ability-shortcutmanager-setshortcutsenabled-f-sys.md#setshortcutsenabled) | Enables or disables the specified static shortcuts. This API uses a promise to return the result. |
| [updateDesktopShortcutInfo](arkts-ability-shortcutmanager-updatedesktopshortcutinfo-f-sys.md#updatedesktopshortcutinfo) | Updates the shortcut information of the specified user. This API uses a promise to return the result. |
<!--DelEnd-->

### Types

| Name | Description |
| --- | --- |
| [ParameterItem](arkts-ability-shortcutmanager-parameteritem-t.md) | Defines the custom data in the shortcut configuration. |
| [ShortcutInfo](arkts-ability-shortcutmanager-shortcutinfo-t.md) | Defines the shortcut information defined in the [module.json5](../../../quick-start/module-configuration-file.md#shortcuts) file of the application. |
| [ShortcutWant](arkts-ability-shortcutmanager-shortcutwant-t.md) | Defines the target [wants](../../../quick-start/module-configuration-file.md#wants) defined in the shortcut configuration. |
