# getSkillInfoForSelf

## Modules to Import

```TypeScript
import { skillManager } from '@kit.AbilityKit';
```

## getSkillInfoForSelf

```TypeScript
function getSkillInfoForSelf(moduleName: string, skillName: string, flags: number): Promise<SkillInfo>
```

Obtains SkillInfo of the calling application based on moduleName and skillName.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| moduleName | string | Yes | Indicates the module name of the skill. |
| skillName | string | Yes | Indicates the name of the skill. |
| flags | number | Yes | [SkillInfoFlag](arkts-ability-skillmanager-skillinfoflag-e.md) - Indicates the flag used to specify information contained in the SkillInfo object that will be returned. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[SkillInfo](arkts-ability-skillmanager-skillinfo-t.md)&gt; | Returns the SkillInfo object of the specified skill. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [17700002](../errorcode-bundle.md#17700002-module-name-does-not-exist) | The specified module is not found. |
| [17700093](../errorcode-bundle.md#17700093-the-specified-skillname-does-not-exist) | The specified skillName is not found. |
