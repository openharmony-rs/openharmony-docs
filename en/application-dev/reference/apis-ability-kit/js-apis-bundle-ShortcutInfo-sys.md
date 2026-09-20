# shortcutInfo (System API)
<!--Kit: Ability Kit-->
<!--Subsystem: BundleManager-->
<!--Owner: @wanghang904-->
<!--Designer: @hanfeng6-->
<!--Tester: @memghaiyang-->
<!--Adviser: @HelloCrease-->
<!-- md-trans-meta sourceCommit=1bd317f06f1afd85920306c4a4cf71333749080f translatedAt=2026-09-03T11:07:31.696Z pushedAt=2026-09-05T10:47:30.540Z -->

The module defines shortcut information configured in the configuration file. For the [FA model](../../application-models/ability-terminology.md#fa-model), the shortcut information is configured in the [config.json](../../quick-start/application-configuration-file-overview-fa.md) file. For the stage model, the information is configured in the configuration file under **resources/base/profile** in the development view.

> **NOTE**
>
> The initial APIs of this module are supported since API version 7. Newly added APIs will be marked with a superscript to indicate their earliest API version.
>
> Since API version 9, this module is no longer maintained. You are advised to use [ShortcutInfo](js-apis-bundleManager-shortcutInfo.md) instead.
>
> This module is a System API.

## ShortcutWant<sup>(deprecated)</sup>

> **NOTE**
>
> This API is supported since API version 7 and deprecated since API version 9. You are advised to use [ShortcutWant](js-apis-bundleManager-shortcutInfo.md#shortcutwant) instead.

 **System capability**: SystemCapability.BundleManager.BundleFramework

 **System API**: This is a system API and cannot be called by third-party applications.

| Name                     | Type  | Read-Only| Optional| Description                |
| ------------------------- | ------ | ---- | ---- | -------------------- |
| targetBundle              | string | Yes  | No  | Target bundle of the shortcut.|
| targetClass               | string | Yes  | No  | Target class required by the shortcut.|
