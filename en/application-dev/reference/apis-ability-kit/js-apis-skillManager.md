# @ohos.bundle.skillManager (skillManager Module)

<!--Kit: Ability Kit-->
<!--Subsystem: BundleManager-->
<!--Owner: @wanghang904-->
<!--Designer: @hanfeng6-->
<!--Tester: @kongjing2-->
<!--Adviser: @HelloCrease-->
<!-- md-trans-meta sourceCommit=7eb6f57046c125c4e13d8acd776d3cbaf09f5103 translatedAt=2026-06-22T06:58:03.626Z pushedAt=2026-06-25T06:33:59.463Z -->

This module provides the capability to query skill information, supporting queries for an app's own skill information, the skill information of a specified app, and the skill information of all apps. When planning tasks, the AI agent framework can use this module to query the available skills of all apps on the device and select the appropriate skills to fulfill user requests. Through skill information queries, intelligent task scheduling and capability matching optimization can be achieved, improving the task execution efficiency of AI agents and reducing the complexity of skill integration for developers.

**Since:** 26.0.0

## Modules to Import

```ts
import { skillManager } from '@kit.AbilityKit';
```

## SkillInfoFlag

Enumerates the skill information flags, which indicate the content of the skill information to be obtained.

**Since:** 26.0.0

**Model restriction**: This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

| Name                                                     | Value        | Description                                                         |
| -------------------------------------------------------- | ------------ | ------------------------------------------------------------ |
| GET_SKILL_INFO_DEFAULT                                    | 0x00000000   | Obtains the default skill information, excluding description, srcEntries, permissions, and requestPermissions. |
| GET_SKILL_INFO_WITH_DESCRIPTION                            | 0x00000001   | Used to obtain skill information that includes description. |
| GET_SKILL_INFO_WITH_SRC_ENTRIES                            | 0x00000002   | Used to obtain skill information that includes srcEntries. |
| GET_SKILL_INFO_WITH_PERMISSIONS                            | 0x00000004   | Used to obtain skill information that includes permissions. |
| GET_SKILL_INFO_WITH_REQUEST_PERMISSIONS                     | 0x00000008   | Used to obtain skill information that includes requestPermissions. |

## skillManager.getSkillInfoForSelf

getSkillInfoForSelf(moduleName: string, skillName: string, flags: number): Promise\<[SkillInfo](js-apis-bundleManager-SkillInfo.md)\>

Obtains the skill information with the specified name under the specified module in this app. This API uses a promise to return the result.

**Since:** 26.0.0

**Model restriction**: This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

**Parameters**

| Name     | Type   | Mandatory | Description                |
| ----------- | ------ | ---- | --------------------- |
| moduleName | string | Yes   | Name of the module to which the skill to query belongs. |
| skillName | string | Yes   | Name of the skill to query. |
| flags  | number | Yes   | Information contained in the returned SkillInfo. For details, see [SkillInfoFlag](js-apis-skillManager.md#skillinfoflag). |

**Return value**

| Type                                                        | Description                                  |
| ----------------------------------------------------------- | ------------------------------------- |
| Promise\<[SkillInfo](js-apis-bundleManager-SkillInfo.md)\> | Promise used to return the SkillInfo of the specified skill.|

**Error codes**

For details about the following error codes, see [Bundle Error Codes](errorcode-bundle.md).

| ID | Error Message |
| -------- | ------------------------------------- |
| 17700002 | The specified module is not found. |
| 17700093 | The specified skillName is not found. |

**Example**

```ts
import { skillManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

let moduleName = "entry";
let skillName = "mySkill";
let flags = skillManager.SkillInfoFlag.GET_SKILL_INFO_DEFAULT;
try {
  skillManager.getSkillInfoForSelf(moduleName, skillName, flags).then((data) => {
    hilog.info(0x0000, 'testTag', 'getSkillInfoForSelf succeed: Data: %{public}s', JSON.stringify(data));
  }).catch((err: BusinessError) => {
    hilog.error(0x0000, 'testTag', 'getSkillInfoForSelf failed: %{public}d  %{public}s', err.code, err.message);
  });
} catch (err) {
  let code = (err as BusinessError).code;
  let message = (err as BusinessError).message;
  hilog.error(0x0000, 'testTag', 'getSkillInfoForSelf failed: error %{public}d  %{public}s', code, message);
}
```

## skillManager.getSkillInfosForSelf

getSkillInfosForSelf(flags: number): Promise\<Array\<[SkillInfo](js-apis-bundleManager-SkillInfo.md)\>\>

Obtains all skill information of the current app. This API uses a promise to return the result.

**Since:** 26.0.0

**Model restriction**: This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

**Parameters**

| Name | Type | Mandatory | Description |
| ----------- | ------ | ---- | --------------------- |
| flags | number | Yes | Specifies the information to be included in the returned SkillInfo. For details, see [SkillInfoFlag](js-apis-skillManager.md#skillinfoflag). |

**Return value**

| Type | Description |
| ----------------------------------------------------------- | ------------------------------------- |
| Promise\<Array\<[SkillInfo](js-apis-bundleManager-SkillInfo.md)\>\> | Promise used to return an array of all skill information of the caller's app. |

**Example**

```ts
import { skillManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

let flags = skillManager.SkillInfoFlag.GET_SKILL_INFO_DEFAULT;
try {
  skillManager.getSkillInfosForSelf(flags).then((data) => {
    hilog.info(0x0000, 'testTag', 'getSkillInfosForSelf succeed: Data: %{public}s', JSON.stringify(data));
  }).catch((err: BusinessError) => {
    hilog.error(0x0000, 'testTag', 'getSkillInfosForSelf failed: %{public}d  %{public}s', err.code, err.message);
  });
} catch (err) {
  let code = (err as BusinessError).code;
  let message = (err as BusinessError).message;
  hilog.error(0x0000, 'testTag', 'getSkillInfosForSelf failed: error %{public}d  %{public}s', code, message);
}
```

## skillManager.getSkillInfo

getSkillInfo(bundleName: string, moduleName: string, skillName: string, flags: number, userId?: number): Promise\<[SkillInfo](js-apis-bundleManager-SkillInfo.md)\>

Obtains the skill information with a specified name under a specified module of a specified app. This API uses a promise to return the result.

**Since:** 26.0.0

**Required permissions:** ohos.permission.MANAGE_SKILL_PRIVILEGE or ohos.permission.MANAGE_SKILL

> **NOTE**
>
> ohos.permission.INTERACT_ACROSS_LOCAL_ACCOUNTS is also required for cross-user queries.

**Model restriction**: This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

**Parameters**

| Name     | Type   | Mandatory | Description                |
| ----------- | ------ | ---- | --------------------- |
| bundleName | string | Yes   | Bundle name of the app to query. |
| moduleName | string | Yes   | Name of the module to which the skill to query belongs. |
| skillName | string | Yes   | Name of the skill to query. |
| flags | number | Yes   | Information contained in the returned SkillInfo. For details, see [SkillInfoFlag](js-apis-skillManager.md#skillinfoflag). |
| userId | number | No   | User ID to query, which can be obtained through [getOsAccountLocalId](../apis-basic-services-kit/js-apis-osAccount.md#getosaccountlocalid9).<br/>Default value: the user to which the caller resides.<br/>Value range: greater than or equal to 0. |

**Return value**

| Type                                                        | Description                                  |
| ----------------------------------------------------------- | ------------------------------------- |
| Promise\<[SkillInfo](js-apis-bundleManager-SkillInfo.md)\> | Promise used to return the SkillInfo of the specified skill.|

**Error codes**

For details about the following error codes, see [Universal Error Codes](../errorcode-universal.md) and [Bundle Error Codes](errorcode-bundle.md).

| ID | Error Message                              |
| -------- | ------------------------------------- |
| 201 | Permission denied. |
| 17700001 | The specified bundleName is not found. |
| 17700002 | The specified module is not found. |
| 17700004 | The specified user ID is not found. |
| 17700093 | The specified skillName is not found. |

**Example**

```ts
import { skillManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

let bundleName = "com.example.myapplication";
let moduleName = "entry";
let skillName = "mySkill";
let flags = skillManager.SkillInfoFlag.GET_SKILL_INFO_DEFAULT;
try {
  skillManager.getSkillInfo(bundleName, moduleName, skillName, flags).then((data) => {
    hilog.info(0x0000, 'testTag', 'getSkillInfo succeed: Data: %{public}s', JSON.stringify(data));
  }).catch((err: BusinessError) => {
    hilog.error(0x0000, 'testTag', 'getSkillInfo failed: %{public}d  %{public}s', err.code, err.message);
  });
} catch (err) {
  let code = (err as BusinessError).code;
  let message = (err as BusinessError).message;
  hilog.error(0x0000, 'testTag', 'getSkillInfo failed: error %{public}d  %{public}s', code, message);
}
```

## skillManager.getSkillInfos

getSkillInfos(bundleName: string, flags: number, userId?: number): Promise\<Array\<[SkillInfo](js-apis-bundleManager-SkillInfo.md)\>\>

Obtains all skill information of a specified app. This API uses a promise to return the result.

**Since:** 26.0.0

**Required permissions:** ohos.permission.MANAGE_SKILL_PRIVILEGE or ohos.permission.MANAGE_SKILL

> **NOTE**
>
> ohos.permission.INTERACT_ACROSS_LOCAL_ACCOUNTS is also required for cross-user query.

**Model restriction**: This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

**Parameters**

| Name     | Type   | Mandatory | Description                |
| ----------- | ------ | ---- | --------------------- |
| bundleName | string | Yes   | Bundle name of the app to query. |
| flags  | number | Yes   | Information contained in the returned SkillInfo. For details, see [SkillInfoFlag](js-apis-skillManager.md#skillinfoflag). |
| userId | number | No   | User ID to query, which can be obtained through [getOsAccountLocalId](../apis-basic-services-kit/js-apis-osAccount.md#getosaccountlocalid9).<br/>Default value: the user where the caller resides.<br/>Value range: greater than or equal to 0. |

**Return value**

| Type                                                        | Description                                  |
| ----------------------------------------------------------- | ------------------------------------- |
| Promise\<Array\<[SkillInfo](js-apis-bundleManager-SkillInfo.md)\>\> | Promise used to return an array of all skill information of the specified app.|

**Error codes**

For details about the following error codes, see [Universal Error Codes](../errorcode-universal.md) and [Bundle Error Codes](errorcode-bundle.md).

| ID | Error Message                              |
| -------- | ------------------------------------- |
| 201 | Permission denied. |
| 17700001 | The specified bundleName is not found. |
| 17700004 | The specified user ID is not found. |

**Example**

```ts
import { skillManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

let bundleName = "com.example.myapplication";
let flags = skillManager.SkillInfoFlag.GET_SKILL_INFO_DEFAULT;
try {
  skillManager.getSkillInfos(bundleName, flags).then((data) => {
    hilog.info(0x0000, 'testTag', 'getSkillInfos succeed: Data: %{public}s', JSON.stringify(data));
  }).catch((err: BusinessError) => {
    hilog.error(0x0000, 'testTag', 'getSkillInfos failed: %{public}d  %{public}s', err.code, err.message);
  });
} catch (err) {
  let code = (err as BusinessError).code;
  let message = (err as BusinessError).message;
  hilog.error(0x0000, 'testTag', 'getSkillInfos failed: error %{public}d  %{public}s', code, message);
}
```

## skillManager.getAllSkillInfos

getAllSkillInfos(flags: number, userId?: number): Promise\<Array\<[SkillInfo](js-apis-bundleManager-SkillInfo.md)\>\>

Obtains all skill information of installed apps on the device. This API uses a promise to return the result.

**Since:** 26.0.0

**Required permissions:** ohos.permission.MANAGE_SKILL_PRIVILEGE or ohos.permission.MANAGE_SKILL

> **NOTE**
>
> ohos.permission.INTERACT_ACROSS_LOCAL_ACCOUNTS is also required for cross-user queries.

**Model restriction**: This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

**Parameters**

| Name     | Type   | Mandatory | Description                |
| ----------- | ------ | ---- | --------------------- |
| flags  | number | Yes   | Information contained in the returned SkillInfo. For details, see [SkillInfoFlag](js-apis-skillManager.md#skillinfoflag). |
| userId | number | No   | User ID to query, which can be obtained through [getOsAccountLocalId](../apis-basic-services-kit/js-apis-osAccount.md#getosaccountlocalid9).<br/>Default value: the user where the caller resides.<br/>Value range: greater than or equal to 0. |

**Return value**

| Type                                                        | Description                                  |
| ----------------------------------------------------------- | ------------------------------------- |
| Promise\<Array\<[SkillInfo](js-apis-bundleManager-SkillInfo.md)\>\> | Promise used to return an array of skill information for all apps.|

**Error codes**

For details about the following error codes, see [Universal Error Codes](../errorcode-universal.md) and [Bundle Error Codes](errorcode-bundle.md).

| ID | Error Message |
| -------- | ------------------------------------- |
| 201 | Permission denied. |
| 17700004 | The specified user ID is not found. |

**Example**

```ts
import { skillManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

let flags = skillManager.SkillInfoFlag.GET_SKILL_INFO_DEFAULT;
try {
  skillManager.getAllSkillInfos(flags).then((data) => {
    hilog.info(0x0000, 'testTag', 'getAllSkillInfos succeed: Data: %{public}s', JSON.stringify(data));
  }).catch((err: BusinessError) => {
    hilog.error(0x0000, 'testTag', 'getAllSkillInfos failed: %{public}d  %{public}s', err.code, err.message);
  });
} catch (err) {
  let code = (err as BusinessError).code;
  let message = (err as BusinessError).message;
  hilog.error(0x0000, 'testTag', 'getAllSkillInfos failed: error %{public}d  %{public}s', code, message);
}
```

## SkillInfo

type SkillInfo = _SkillInfo

Skill configuration information, used to define the skill capabilities of an AI agent.

**Since:** 26.0.0

**Model restriction**: This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

| Type                                                         | Description           |
| ------------------------------------------------------------ | --------------------- |
| [_SkillInfo](js-apis-bundleManager-SkillInfo.md#skillinfo-1) | App skill information. |

## SkillType

type SkillType = _SkillType

Enumerates the skill types.

**Since:** 26.0.0

**Model restriction**: This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

| Type                                                         | Description           |
| ------------------------------------------------------------ | -------------- |
| [_SkillType](js-apis-bundleManager-SkillInfo.md#skilltype) | Enumeration of skill types. |