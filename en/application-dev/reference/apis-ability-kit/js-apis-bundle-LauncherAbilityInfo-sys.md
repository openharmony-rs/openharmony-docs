# LauncherAbilityInfo (System API)
<!--Kit: Ability Kit-->
<!--Subsystem: BundleManager-->
<!--Owner: @wanghang904-->
<!--Designer: @hanfeng6-->
<!--Tester: @memghaiyang-->
<!--Adviser: @HelloCrease-->
<!-- md-trans-meta sourceCommit=1bd317f06f1afd85920306c4a4cf71333749080f translatedAt=2026-09-03T11:06:21.184Z pushedAt=2026-09-05T10:47:30.532Z -->

The LauncherAbilityInfo module provides information about the launcher ability, which is obtained through [innerBundleManager.getLauncherAbilityInfos](js-apis-Bundle-InnerBundleManager-sys.md#innerbundlemanagergetlauncherabilityinfosdeprecated).

> **NOTE**
>
> The initial APIs of this module are supported since API version 8. Newly added APIs will be marked with a superscript to indicate their earliest API version.
>
> This module is no longer maintained since API version 9. You are advised to use [bundleManager-LauncherAbilityInfo](js-apis-bundleManager-launcherAbilityInfo.md) instead.
>
> This module is a system API.

## LauncherAbilityInfo<sup>(deprecated)</sup>

> **NOTE**
>
> This API has been supported since API version 8 and deprecated since API version 9. You are advised to use [bundleManager-LauncherAbilityInfo](js-apis-bundleManager-launcherAbilityInfo.md) instead.

**System capability**: SystemCapability.BundleManager.BundleFramework

**System API**: This is a system API.

| Name           | Type                                                | Read-Only| Optional| Description                                  |
| --------------- | ---------------------------------------------------- | ---- | ---- | -------------------------------------- |
| applicationInfo | [ApplicationInfo](js-apis-bundle-ApplicationInfo.md) | Yes  | No  | Application information of the launcher ability.|
| elementName     | [ElementName](js-apis-bundle-ElementName.md)         | Yes  | No  | Element name of the launcher ability.   |
| labelId         | number                                               | Yes  | No  | ID of the launcher ability label.            |
| iconId          | number                                               | Yes  | No  | ID of the launcher ability icon.            |
| userId          | number                                               | Yes  | No  | User ID of the launcher ability.            |
| installTime     | number                                               | Yes  | No  | Timestamp when the launcher ability was installed, in milliseconds.       |