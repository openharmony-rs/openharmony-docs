# @ohos.bundle.shortcutManager

This module provides the application's management capabilities for shortcuts, including setting whether a shortcut is displayed. Through shortcuts, users can quickly launch specific features of an app from the home screen, improving the app's ease of use and user retention. Typical usage scenarios include: providing users with quick access to frequently used features, dynamically adjusting the display of shortcuts based on user habits, etc.

**Since:** 20

**System capability:** SystemCapability.BundleManager.BundleFramework.Launcher

## Modules to Import

```TypeScript
import { shortcutManager } from '@kit.AbilityKit';
```

## Summary

### Functions

| Name | Description |
| --- | --- |
| [getAllShortcutInfoForSelf](arkts-ability-shortcutmanager-getallshortcutinfoforself-f.md) | Obtains all the shortcut information defined in the [configuration](../../../quick-start/module-configuration-file.md#shortcuts) file of the current application. This API uses a promise to return the result. |
| [isShortcutSupported](arkts-ability-shortcutmanager-isshortcutsupported-f.md) | Checks whether the current device supports shortcuts. |
| [setShortcutVisibleForSelf](arkts-ability-shortcutmanager-setshortcutvisibleforself-f.md) | Sets whether to display the specified shortcut for the current application. This API uses a promise to return the result. |

<!--Del-->
### Functions(System API)

| Name | Description |
| --- | --- |
| [addDesktopShortcutInfo](arkts-ability-shortcutmanager-adddesktopshortcutinfo-f-sys.md) | Adds a shortcut for the given user. This API uses a promise to return the result. |
| [addDynamicShortcutInfos](arkts-ability-shortcutmanager-adddynamicshortcutinfos-f-sys.md) | Adds dynamic shortcuts for the given user. |
| [deleteDesktopShortcutInfo](arkts-ability-shortcutmanager-deletedesktopshortcutinfo-f-sys.md) | Deletes a shortcut for the given user. This API uses a promise to return the result. |
| [deleteDynamicShortcutInfos](arkts-ability-shortcutmanager-deletedynamicshortcutinfos-f-sys.md) | Deletes dynamic shortcuts. |
| [getAllDesktopShortcutInfo](arkts-ability-shortcutmanager-getalldesktopshortcutinfo-f-sys.md) | Obtains the information about all shortcuts of the given user. |
| [getShortcutInfoByAbility](arkts-ability-shortcutmanager-getshortcutinfobyability-f-sys.md) | Obtains shortcut info by bundleName, moduleName, abilityName, userId and appIndex. If you need to obtains shortcut info under the current user, ohos.permission.GET_BUNDLE_INFO_PRIVILEGED needs to be applied for. If you need to obtains shortcut info under other users, ohos.permission.GET_BUNDLE_INFO_PRIVILEGED and ohos.permission.INTERACT_ACROSS_LOCAL_ACCOUNTS need to be applied for. |
| [setShortcutsEnabled](arkts-ability-shortcutmanager-setshortcutsenabled-f-sys.md) | Enables or disables the specified static shortcuts. This API uses a promise to return the result. |
| [updateDesktopShortcutInfo](arkts-ability-shortcutmanager-updatedesktopshortcutinfo-f-sys.md) | Updates a shortcut for the given user. This API uses a promise to return the result. |
<!--DelEnd-->

### Types

| Name | Description |
| --- | --- |
| [ParameterItem](arkts-ability-shortcutmanager-parameteritem-t.md) | Defines the custom data in the shortcut configuration. |
| [ShortcutInfo](arkts-ability-shortcutmanager-shortcutinfo-t.md) | Defines the shortcut information defined in the [module.json5](../../../quick-start/module-configuration-file.md#shortcuts) file of the application. |
| [ShortcutWant](arkts-ability-shortcutmanager-shortcutwant-t.md) | Defines the target [wants](../../../quick-start/module-configuration-file.md#wants) defined in the shortcut configuration. |
