# ShortcutInfo
<!--Kit: Ability Kit-->
<!--Subsystem: BundleManager-->
<!--Owner: @wanghang904-->
<!--Designer: @hanfeng6-->
<!--Tester: @memghaiyang-->
<!--Adviser: @HelloCrease-->
<!-- md-trans-meta sourceCommit=1bd317f06f1afd85920306c4a4cf71333749080f translatedAt=2026-09-03T11:08:07.102Z pushedAt=2026-09-05T10:47:30.544Z -->

The module defines shortcut information configured in the configuration file. For the [FA model](../../application-models/ability-terminology.md#fa-model), the information is configured in the [config.json](../../quick-start/application-configuration-file-overview-fa.md) file. For the [stage model](../../application-models/ability-terminology.md#stage-model), the information is configured in the configuration file under **resources/base/profile** in the development view.

> **NOTE**
>
> The initial APIs of this module are supported since API version 7. Newly added APIs will be marked with a superscript to indicate their earliest API version.
>
> This module is no longer maintained since API version 9. You are advised to use [bundleManager-ShortcutInfo](js-apis-bundleManager-shortcutInfo.md) instead.

## ShortcutInfo<sup>(deprecated)</sup>

> **NOTE**
>
> This API has been supported since API version 7 and deprecated since API version 9. You are advised to use [bundleManager-ShortcutInfo](js-apis-bundleManager-shortcutInfo.md#shortcutinfo-1) instead.

**System capability**: SystemCapability.BundleManager.BundleFramework

| Name                   | Type                                      | Read-Only| Optional| Description                        |
| ----------------------- | ------------------------------------------ | ---- | ---- | ---------------------------- |
| id                      | string                                     | Yes   | No   | ID of the application to which the shortcut belongs.     |
| bundleName              | string                                     | Yes  | No  | Name of the bundle that contains the shortcut.|
| hostAbility             | string                                     | Yes  | No  | Local ability information of the shortcut.   |
| icon                    | string                                     | Yes  | No  | Icon of the shortcut.              |
| iconId<sup>8+</sup>     | number                                     | Yes   | No   | Icon ID of the shortcut.             |
| label                   | string                                     | Yes  | No  | Name of the shortcut.              |
| labelId<sup>8+</sup>    | number                                     | Yes   | No   | Name ID of the shortcut.             |
| disableMessage          | string                                     | Yes  | No  | Message displayed when the shortcut is disabled.          |
| wants                   | Array&lt;<!--Del-->[<!--DelEnd-->ShortcutWant<!--Del-->](js-apis-bundle-ShortcutInfo-sys.md#shortcutwantdeprecated)<!--DelEnd-->&gt; | Yes  | No  | Want list for the shortcut.        |
| isStatic                | boolean                                    | Yes  | Yes  | Whether the shortcut is static. **true** if static, **false** otherwise.         |
| isHomeShortcut          | boolean                                    | Yes  | Yes  | Whether the shortcut is a home shortcut. **true** if the shortcut is a home shortcut, **false** otherwise.|
| isEnabled               | boolean                                    | Yes  | Yes  | Whether the shortcut is enabled. **true** if enabled, **false** otherwise.            |