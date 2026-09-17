# innerBundleManager

The module provides APIs for the Home Screen application.

> **NOTE:** 
> 
> This module is deprecated since API version 9. You are advised to use
> [launcherBundleManager](arkts-ability-bundle-launcherbundlemanager.md) and
> [bundleMonitor](arkts-ability-bundle-bundlemonitor.md) instead.
> 
> The APIs provided by this module are system APIs.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [launcherBundleManager](arkts-ability-bundle-launcherbundlemanager.md)

**System capability:** SystemCapability.BundleManager.BundleFramework

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { innerBundleManager, BundleStatusCallback } from '@kit.AbilityKit';
```

## Summary

<!--Del-->
### Functions(System API)

| Name | Description |
| --- | --- |
| [getLauncherAbilityInfos](arkts-ability-innerbundlemanager-getlauncherabilityinfos-f-sys.md) | Obtains an array of the launcher ability information based on a given bundle name. This API uses an asynchronous callback to return the result. |
| [getLauncherAbilityInfos](arkts-ability-innerbundlemanager-getlauncherabilityinfos-f-sys.md) | Obtains an array of the launcher ability information based on a given bundle name. This API uses a promise to return the result. |
| [on](arkts-ability-innerbundlemanager-on-f-sys.md#onbundlestatuschange) | Registers a callback to receive bundle status changes. This API uses an asynchronous callback to return the result. |
| [on](arkts-ability-innerbundlemanager-on-f-sys.md#onbundlestatuschange) | Registers a callback to receive bundle status changes. This API uses an asynchronous callback to return the result. |
| [off](arkts-ability-innerbundlemanager-off-f-sys.md#offbundlestatuschange) | Unregisters the callback that receives bundle status changes. This API uses an asynchronous callback to return the result. |
| [off](arkts-ability-innerbundlemanager-off-f-sys.md#offbundlestatuschange) | Unregisters the callback that receives bundle status changes. This API uses an asynchronous callback to return the result. |
| [getAllLauncherAbilityInfos](arkts-ability-innerbundlemanager-getalllauncherabilityinfos-f-sys.md) | Obtains the information about all launcher abilities. This API uses an asynchronous callback to return the result. |
| [getAllLauncherAbilityInfos](arkts-ability-innerbundlemanager-getalllauncherabilityinfos-f-sys.md) | Obtains the information about all launcher abilities. This API uses a promise to return the result. |
| [getShortcutInfos](arkts-ability-innerbundlemanager-getshortcutinfos-f-sys.md) | Obtains an array of the shortcut information based on a given bundle name. This API uses an asynchronous callback to return the result. |
| [getShortcutInfos](arkts-ability-innerbundlemanager-getshortcutinfos-f-sys.md) | Obtains an array of the shortcut information based on a given bundle name. This API uses a promise to return the result. |
<!--DelEnd-->
