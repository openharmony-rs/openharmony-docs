# ModuleInfo
<!--Kit: Ability Kit-->
<!--Subsystem: BundleManager-->
<!--Owner: @wanghang904-->
<!--Designer: @hanfeng6-->
<!--Tester: @kongjing2-->
<!--Adviser: @Brilliantry_Rui-->

The ModuleInfo module provides module information of an application.

> **NOTE**
> 
> The initial APIs of this module are supported since API version 7. Newly added APIs will be marked with a superscript to indicate their earliest API version.
>
> The APIs of this module have been deprecated since API version 9. You are advised to use [bundleManager-HapModuleInfo](js-apis-bundleManager-hapModuleInfo.md) instead.

## ModuleInfo<sup>(deprecated)<sup>

> **NOTE**
>
> This API has been supported since API version 7 and deprecated since API version 9. You are advised to use [bundleManager-HapModuleInfo](js-apis-bundleManager-hapModuleInfo.md#hapmoduleinfo-1) instead.

**System capability**: SystemCapability.BundleManager.BundleFramework
| Name           | Type  | Read-Only| Optional| Description    |
| --------------- | ------ | ---- | ---- | -------- |
| moduleName      | string | Yes  | No  | Module name.|
| moduleSourceDir | string | Yes  | No  | Installation directory. Do not access resource files using concatenated paths. Use [@ohos.resourceManager](../apis-localization-kit/js-apis-resource-manager.md) instead.|
