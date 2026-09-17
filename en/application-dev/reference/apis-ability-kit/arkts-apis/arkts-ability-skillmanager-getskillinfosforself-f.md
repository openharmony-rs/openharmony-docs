# getSkillInfosForSelf

## Modules to Import

```TypeScript
import { skillManager } from '@kit.AbilityKit';
```

## getSkillInfosForSelf

```TypeScript
function getSkillInfosForSelf(flags: number): Promise<Array<SkillInfo>>
```

Obtains all SkillInfo objects of the calling application.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| flags | number | Yes | [SkillInfoFlag](arkts-ability-skillmanager-skillinfoflag-e.md) - Indicates the flag used to specify information contained in the SkillInfo objects that will be returned. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;Array&lt;[SkillInfo](arkts-ability-skillmanager-skillinfo-t.md)&gt;&gt; | Returns the list of SkillInfo objects. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [17700101](../errorcode-bundle.md#17700101-bundle-manager-service-abnormal) | Bundle manager service is exception. Possible causes: 1. Failed to connect to the system service. 2. IPC data transmission failed. 3. Failed to obtain the object constructor. |
