# @ohos.bundle.launcherBundleManager

The module providers APIs for launcher applications (applications with icons on the home screen) to obtain the [launcher ability information](arkts-ability-launcherabilityinfo-i.md).

**Since:** 9

**System capability:** SystemCapability.BundleManager.BundleFramework.Launcher

## Modules to Import

```TypeScript
import { launcherBundleManager } from '@kit.AbilityKit';
```

## Summary

### Functions

| Name | Description |
| --- | --- |
| [getLauncherAbilityInfoSync](arkts-ability-launcherbundlemanager-getlauncherabilityinfosync-f.md) | Obtains the [launcher ability information](arkts-ability-launcherabilityinfo-i.md) based on the given bundle name and user ID. |

<!--Del-->
### Functions(System API)

| Name | Description |
| --- | --- |
| [getAllLauncherAbilityInfo](arkts-ability-launcherbundlemanager-getalllauncherabilityinfo-f-sys.md) | Obtains the [launcher ability information](arkts-ability-launcherabilityinfo-i.md) of all applications based on the given user ID. This API uses an asynchronous callback to return the result. |
| [getAllLauncherAbilityInfo](arkts-ability-launcherbundlemanager-getalllauncherabilityinfo-f-sys.md) | Obtains the [launcher ability information](arkts-ability-launcherabilityinfo-i.md) of all applications based on the given user ID. This API uses a promise to return the result. |
| [getLauncherAbilityInfo](arkts-ability-launcherbundlemanager-getlauncherabilityinfo-f-sys.md) | Obtains the [launcher ability information](arkts-ability-launcherabilityinfo-i.md) based on the given bundle name and user ID. This API uses an asynchronous callback to return the result. |
| [getLauncherAbilityInfo](arkts-ability-launcherbundlemanager-getlauncherabilityinfo-f-sys.md) | Obtains the [launcher ability information](arkts-ability-launcherabilityinfo-i.md) based on the given bundle name and user ID. This API uses a promise to return the result. |
| [getShortcutInfo](arkts-ability-launcherbundlemanager-getshortcutinfo-f-sys.md) | Obtains the shortcut information of the current user based on the given bundle name of a main application. To obtain shortcut information about an application clone, use [getShortcutInfoByAppIndex](arkts-ability-launcherbundlemanager-getshortcutinfobyappindex-f-sys.md). This API uses an asynchronous callback to return the result. |
| [getShortcutInfo](arkts-ability-launcherbundlemanager-getshortcutinfo-f-sys.md) | Obtains the shortcut information of the current user based on the given bundle name of a main application. To obtain shortcut information about an application clone, use [getShortcutInfoByAppIndex](arkts-ability-launcherbundlemanager-getshortcutinfobyappindex-f-sys.md). This API uses a promise to return the result. |
| [getShortcutInfoByAppIndex](arkts-ability-launcherbundlemanager-getshortcutinfobyappindex-f-sys.md) | Obtains the shortcut information of the current user based on the index of an application clone. |
| [getShortcutInfoSync](arkts-ability-launcherbundlemanager-getshortcutinfosync-f-sys.md) | Obtains the shortcut information of the current user based on the given bundle name of a main application. To obtain shortcut information about an application clone, use [getShortcutInfoByAppIndex](arkts-ability-launcherbundlemanager-getshortcutinfobyappindex-f-sys.md). |
| [getShortcutInfoSync](arkts-ability-launcherbundlemanager-getshortcutinfosync-f-sys.md) | Obtains the shortcut information of the specified user based on the given bundle name of a main application. To obtain shortcut information about an application clone, use [getShortcutInfoByAppIndex](arkts-ability-launcherbundlemanager-getshortcutinfobyappindex-f-sys.md). |
| [startShortcut](arkts-ability-launcherbundlemanager-startshortcut-f-sys.md) | Starts an ability based on the specified shortcut information. This API uses a promise to return the result. |
| [startShortcutWithReason](arkts-ability-launcherbundlemanager-startshortcutwithreason-f-sys.md) | Starts an ability based on the specified shortcut information, and carries the reason for the shortcut launch. This API uses a promise to return the result. |
<!--DelEnd-->

### Types

| Name | Description |
| --- | --- |
| [LauncherAbilityInfo](arkts-ability-launcherbundlemanager-launcherabilityinfo-t.md) | Defines the information about the launcher ability. |
| [ParameterItem](arkts-ability-launcherbundlemanager-parameteritem-t.md) | Defines the custom data in the shortcut configuration. |
| [ShortcutInfo](arkts-ability-launcherbundlemanager-shortcutinfo-t.md) | Defines the shortcut information defined in the [module.json5](../../../quick-start/module-configuration-file.md#shortcuts) file of the application. |
| [ShortcutWant](arkts-ability-launcherbundlemanager-shortcutwant-t.md) | Defines the target [wants](../../../quick-start/module-configuration-file.md#wants) defined in the shortcut configuration. |
