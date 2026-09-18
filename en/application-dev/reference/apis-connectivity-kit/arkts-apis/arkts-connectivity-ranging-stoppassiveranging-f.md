# stopPassiveRanging

## Modules to Import

```TypeScript
import { ranging } from '@kit.ConnectivityKit';
```

## stopPassiveRanging

```TypeScript
function stopPassiveRanging(handle: number, capabilityType: RangingTypes): void
```

Stops passive ranging mode.

Stops the passive ranging broadcast and cleans up associated resources based on the specified handle and ranging capability type.

**Since:** 26.0.0

**Required permissions:** ohos.permission.ACCESS_NEARLINK

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Communication.FusionConnectivity.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| handle | number | Yes | Indicates the handle number of ranging monitoring. |
| capabilityType | [RangingTypes](arkts-connectivity-ranging-rangingtypes-e.md) | Yes | Indicates the capability type for ranging. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. |
| [34900052](../errorcode-fusionConnectivity.md#34900052-specified-ranging-service-unsupported) | The specified type of ranging service is not supported. |
| [34900054](../errorcode-fusionConnectivity.md#34900054-invalid-parameters) | The parameter value does not meet specifications. |
| [34900099](../errorcode-fusionConnectivity.md#34900099-operation-failed) | Internal system error. For example, Internal object is invalid. |
