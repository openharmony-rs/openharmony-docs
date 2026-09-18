# getSkillInfos

## Modules to Import

```TypeScript
import { skillManager } from '@kit.AbilityKit';
```

## getSkillInfos

```TypeScript
function getSkillInfos(bundleName: string, flags: number, userId?: number): Promise<Array<SkillInfo>>
```

Obtains all SkillInfo of a specified application based on bundleName. To query information for other local accounts, the permission ohos.permission.INTERACT_ACROSS_LOCAL_ACCOUNTS must additionally be granted.

**Since:** 26.0.0

**Required permissions:** ohos.permission.MANAGE_SKILL_PRIVILEGE or ohos.permission.MANAGE_SKILL

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| bundleName | string | Yes | Indicates the bundle name of the application. |
| flags | number | Yes | [SkillInfoFlag](arkts-ability-skillmanager-skillinfoflag-e.md) - Indicates the flag used to specify information contained in the SkillInfo objects that will be returned. |
| userId | number | No | Indicates the user ID. If not provided, the user ID of the caller is used. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;Array&lt;[SkillInfo](arkts-ability-skillmanager-skillinfo-t.md)&gt;&gt; | Returns the list of SkillInfo objects. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [17700001](../errorcode-bundle.md#17700001-bundle-name-does-not-exist) | The specified bundleName is not found. |
| [17700004](../errorcode-bundle.md#17700004-user-id-does-not-exist) | The specified user ID is not found. |
