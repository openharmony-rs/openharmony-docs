# @ohos.app.ability.wantConstant (wantConstant) (System API)

<!--Kit: Ability Kit-->
<!--Subsystem: Ability-->
<!--Owner: @linjunjie6-->
<!--Designer: @li-weifeng2024-->
<!--Tester: @liangchengguang-->
<!--Adviser: @HelloCrease-->
<!-- md-trans-meta sourceCommit=b3bc27a342923ac4fafa55153b55c4f3b627330f translatedAt=2026-09-03T10:40:28.619Z pushedAt=2026-09-05T10:47:30.457Z -->

The wantConstant module provides the methods for operating Want constants and describes the meanings of the Flags.

> **NOTE**
>
> The initial APIs of this module are supported since API version 9. Newly added APIs will be marked with a superscript to indicate their earliest API version.
>
> This topic describes only the system APIs of this module. For details about the public APIs, see [@ohos.app.ability.wantConstant (Want Constant)](js-apis-app-ability-wantConstant.md).

## Modules to Import

```ts
import { wantConstant } from '@kit.AbilityKit';
```

## Params

Defines **Params** (specifying the action that can be performed) in the Want.

**System capability**: SystemCapability.Ability.AbilityBase

| Name                   | Value                                | Description                                                                          |
| ----------------------- | ---------------------------------- | ------------------------------------------------------------------------------ |
| DLP_PARAMS_SANDBOX      | ohos.dlp.params.sandbox            | Action of obtaining the sandbox flag.<br>**System API**: This is a system API.|
| DLP_PARAMS_BUNDLE_NAME  | ohos.dlp.params.bundleName         | Action of obtaining the DLP bundle name.<br>**System API**: This is a system API.|
| DLP_PARAMS_MODULE_NAME  | ohos.dlp.params.moduleName         | Action of obtaining the DLP module name.<br>**System API**: This is a system API.|
| DLP_PARAMS_ABILITY_NAME | ohos.dlp.params.abilityName        | Indicates the operation on the parameter of the DLP Ability name. <br>**System API**: This API is a system API. |
| DLP_PARAMS_INDEX        | ohos.dlp.params.index              | Action of obtaining the DLP index.<br>**System API**: This is a system API.|
| HIDE_SENSITIVE_TYPE<sup>15+</sup>     | ohos.media.params.hideSensitiveType | Indicates the type of hidden sensitive information. <br>**System API**: This API is a system API. |
| ASSERT_FAULT_SESSION_ID<sup>12+</sup>  | ohos.ability.params.asssertFaultSessionId      | Session ID of the AssertFault.<br>**System API**: This is a system API.|
| UI_EXTENSION_ROOT_TOKEN | ohos.param.uiExtension.rootHostToken | Indicates the original host token of the UIExtensionAbility. <br>**Model restriction**: This API can be used only in the stage model.<br>**System API**: This API is a system API.<br>**Since**: 26.0.0.|