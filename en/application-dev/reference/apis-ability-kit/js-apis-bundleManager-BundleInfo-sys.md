# BundleInfo (System API)
<!--Kit: Ability Kit-->
<!--Subsystem: BundleManager-->
<!--Owner: @wanghang904-->
<!--Designer: @hanfeng6-->
<!--Tester: @memghaiyang-->
<!--Adviser: @HelloCrease-->
<!-- md-trans-meta sourceCommit=4a7b6a005161311b24552d806cf588adf3a53fa0 translatedAt=2026-09-03T11:10:07.982Z pushedAt=2026-09-05T10:47:30.557Z -->

The module defines the bundle information. Applications can obtain bundle information of a specific application through [bundleManager.getBundleInfo](js-apis-bundleManager.md#bundlemanagergetbundleinfo14), with [bundleFlags](js-apis-bundleManager.md#bundleflag) set to the information to be contained in the returned [BundleInfo](js-apis-bundleManager-bundleInfo.md).

> **NOTE**
>
> The initial APIs of this module are supported since API version 20. Newly added APIs will be marked with a superscript to indicate their earliest API version.
>
> This page contains only the system APIs of this module. For details about other public APIs, see ([BundleInfo](js-apis-bundleManager-bundleInfo.md)).

## Modules to Import

```ts
import { bundleManager } from '@kit.AbilityKit';
```

## BundleInfo

Defines the bundle information.

**Since:** 26.0.0

**System capability**: SystemCapability.BundleManager.BundleFramework.Core

**System API**: This is a system API.

**Model restriction:** This API can be used only in the stage model.

<!--Table: 20%; 20%; 8%; 8%; 44%-->
| Name                              | Type                                                         | Read-only | Optional | Description                                                  |
| --------------------------------- | ------------------------------------------------------------ | --------- | -------- | ------------------------------------------------------------ |
| sandboxCreatorBundleName          | string                                                       | Yes       | Yes      | Bundle name of the creator of the sandbox clone. |

## DynamicIconInfo

Describes the information about the dynamic icon of an application.

**System capability**: SystemCapability.BundleManager.BundleFramework.Core

**System API**: This is a system API.

| Name     | Type          | Read-Only| Optional| Description                       |
| --------- | -------------- | ---- | ---- | --------------------------- |
| bundleName    | string    | Yes  | No  | Bundle name of the application associated with the dynamic icon.|
| moduleName    | string    | Yes  | No  | Module name of the application associated with the dynamic icon.|
| userId    | number    | Yes  | No  | User ID of the application associated with the dynamic icon.|
| appIndex    | number    | Yes  | No  | Index of the application clone associated with the dynamic icon.|


## BundleOptions

Describes the bundle options used to set or query application information.

**System capability**: SystemCapability.BundleManager.BundleFramework.Core

**System API**: This is a system API.

| Name     | Type          | Read-Only| Optional| Description               |
| --------- | -------------- | ---- | ---- | ------------------- |
| userId | number         | No  | Yes  | User ID. By default, the user is the current caller.            |
| appIndex | number         | No  | Yes  | Index of an application clone. The default value is **0**, indicating the main application.   |
| bundleName<sup>23+</sup> | string         | No   | Yes   | Application bundle name. Default Value: Empty String.<br/>**Model Restriction:** This API can be used only in the stage model.    |
| moduleName<sup>23+</sup> | string         | No   | Yes   | Name of the module to which the ability belongs. Default Value: Empty String.<br/>**Model Restriction:** This API can be used only in the stage model.    |
| abilityName<sup>23+</sup> | string         | No   | Yes   | Ability name. Default Value: Empty String.<br/>**Model Restriction:** This API can be used only in the stage model.    |


## AppClonePreference

App clone preference, used to configure the selection policy between the main app and the clone app at app startup.

**Since:** 26.0.0

**System API**: This is a system API.

**System capability**: SystemCapability.BundleManager.BundleFramework.Core

**Model restriction:** This API can be used only in the stage model.

| Name      | Type           | Readable | Optional | Description                        |
| --------- | -------------- | ---- | ---- | --------------------------- |
| mode | [AppClonePreferenceMode](js-apis-bundleManager-sys.md#appclonepreferencemode)         | No   | No   | Mode of the app clone preference settings. |
| appIndex | number         | No   | Yes   | Index of the app clone.<br>This parameter is mandatory when **mode** is set to **AppClonePreferenceMode.CLONE_APP**, and is used to specify a specific clone app. The value is an integer ranging from 1 to 5 (the system supports a maximum of 5 clones).   |