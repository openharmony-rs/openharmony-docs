# LauncherAbilityInfo
<!--Kit: Ability Kit-->
<!--Subsystem: BundleManager-->
<!--Owner: @wanghang904-->
<!--Designer: @hanfeng6-->
<!--Tester: @memghaiyang-->
<!--Adviser: @HelloCrease-->
<!-- md-trans-meta sourceCommit=1bd317f06f1afd85920306c4a4cf71333749080f translatedAt=2026-09-03T11:15:45.877Z pushedAt=2026-09-05T10:47:30.576Z -->

The module describes the ability information of the launcher application. The information can be obtained by calling [getLauncherAbilityInfoSync](js-apis-launcherBundleManager.md#launcherbundlemanagergetlauncherabilityinfosync)<!--Del--> or [getLauncherAbilityInfo](js-apis-launcherBundleManager-sys.md#launcherbundlemanagergetlauncherabilityinfo)<!--DelEnd-->.

> **NOTE**
>
> The initial APIs of this module are supported since API version 18. Newly added APIs will be marked with a superscript to indicate their earliest API version.
>

## Modules to Import

```ts
import { launcherBundleManager } from '@kit.AbilityKit';
```

## LauncherAbilityInfo

**System capability**: SystemCapability.BundleManager.BundleFramework.Launcher

| Name           | Type                                                       | Read Only| Optional| Description                                |
| --------------- | ----------------------------------------------------------- | ---- | ---- | ------------------------------------ |
| applicationInfo | [ApplicationInfo](js-apis-bundleManager-applicationInfo.md) | Yes  | No  | Application information of the launcher ability.|
| elementName     | [ElementName](js-apis-bundleManager-elementName.md)         | Yes  | No  | Element name of the launcher ability.   |
| labelId         | number                                                      | Yes  | No  | Label ID of the launcher ability.     |
| iconId          | number                                                      | Yes  | No  | Icon ID of the launcher ability.     |
| userId          | number                                                      | Yes  | No  | User ID of the launcher ability.            |
| installTime     | number                                                      | Yes  | No  | Timestamp when the launcher ability was installed, in milliseconds.|