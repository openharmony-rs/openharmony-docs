# MultiAppMode (System API)

<!--Kit: Ability Kit-->
<!--Subsystem: Ability-->
<!--Owner: @wendel-->
<!--Designer: @wendel-->
<!--Tester: @liangchengguang-->
<!--Adviser: @HelloCrease-->
<!-- md-trans-meta sourceCommit=a914ec5c20531defc3768aa8242b62bbe2d1d08f translatedAt=2026-09-03T12:01:10.255Z pushedAt=2026-09-05T10:47:30.850Z -->

Enumerates whether an application supports the multi-app mode, including three types: no multi-app support, multi-instance mode, and app clone mode.

> **NOTE**
> 
> The initial APIs of this module are supported since API version 12. Newly added APIs will be marked with a superscript to indicate their earliest API version.
>
> The APIs of this module can be used only in the stage model.
>
> The APIs provided by this module are system APIs.

## How to Use

Call the [getRunningMultiAppInfo](js-apis-app-ability-appManager-sys.md#appmanagergetrunningmultiappinfo12) method of appManager to obtain the MultiAppMode attribute.

## MultiAppMode

**System API**: This is a system API.

**System capability:** SystemCapability.Ability.AbilityRuntime.AbilityCore

| Name| Value|Description|
| -------- |----|-------- |
| NOT_SUPPORTED | 0 | The application does not support the multi-app mode.|
| MULTI_INSTANCE<sup>14+</sup>  | 1 | The application supports the multi-instance mode. When an application is set to this mode, users can open multiple instances of the application on the same device at the same time. Each instance runs independently and has its own runtime environment and resources.<br>**Note:** Only PC/2-in-1 devices are supported. |
| APP_CLONE | 2 | The application supports the app clone mode. The app clone mode allows creating an independent clone instance for the application. Each instance has an independent data space, which is suitable for scenarios where user data needs to be isolated. |