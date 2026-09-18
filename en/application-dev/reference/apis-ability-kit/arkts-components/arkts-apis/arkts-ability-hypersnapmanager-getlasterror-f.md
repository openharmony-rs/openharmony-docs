# getLastError

## Modules to Import

```TypeScript
import { hyperSnapManager } from '@kit.AbilityKit';
```

## getLastError

```TypeScript
function getLastError(errType: HyperSnapErrorType): Promise<HyperSnapErrorInfo>
```

Gets the last Hyper Snap error information of the current application for a specified scenario. Error information for each scenario is stored independently and cleared after a successful request. All error information will be cleared when the device restarts.

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| errType | [HyperSnapErrorType](arkts-ability-hypersnapmanager-hypersnaperrortype-e.md) | Yes | Hyper Snap error type. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[HyperSnapErrorInfo](arkts-ability-hypersnapmanager-hypersnaperrorinfo-i.md)&gt; | Promise used to return the error information. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [16000050](../errorcode-ability.md#16000050-internal-error) | Connect to system service failed. |
