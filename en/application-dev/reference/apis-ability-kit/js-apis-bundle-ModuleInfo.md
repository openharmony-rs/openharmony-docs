# ModuleInfo
<!--Kit: Ability Kit-->
<!--Subsystem: BundleManager-->
<!--Owner: @wanghang904-->
<!--Designer: @hanfeng6-->
<!--Tester: @memghaiyang-->
<!--Adviser: @HelloCrease-->
<!-- md-trans-meta sourceCommit=1bd317f06f1afd85920306c4a4cf71333749080f translatedAt=2026-09-03T11:06:58.395Z pushedAt=2026-09-05T10:47:30.534Z -->

The ModuleInfo module provides module information of an application.

> **NOTE**
>
> The initial APIs of this module are supported since API version 7. Newly added APIs will be marked with the superscript to indicate their earliest API version.
>
> This module is no longer maintained since API version 9. You are advised to use [bundleManager-HapModuleInfo](js-apis-bundleManager-hapModuleInfo.md) instead.

## ModuleInfo<sup>(deprecated)</sup>

> **NOTE**
>
> This API has been supported since API version 7 and deprecated since API version 9. You are advised to use [bundleManager-HapModuleInfo](js-apis-bundleManager-hapModuleInfo.md#hapmoduleinfo-1) instead.

**System capability**: SystemCapability.BundleManager.BundleFramework
| Name           | Type  | Read-Only| Optional| Description    |
| --------------- | ------ | ---- | ---- | -------- |
| moduleName      | string | Yes  | No  | Module name.|
| moduleSourceDir | string | Yes | No | Installation directory. Do not concatenate paths to access resource files. Use [@ohos.resourceManager (Resource Management)](../apis-localization-kit/js-apis-resource-manager.md) to access resources. |