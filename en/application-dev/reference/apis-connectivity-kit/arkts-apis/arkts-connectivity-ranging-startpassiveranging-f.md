# startPassiveRanging

## Modules to Import

```TypeScript
import { ranging } from '@kit.ConnectivityKit';
```

## startPassiveRanging

```TypeScript
function startPassiveRanging(capabilityType: RangingTypes): Promise<number>
```

Starts passive ranging mode.

Upon successful startup, returns a handle identifier for the passive ranging session and begins broadcasting ranging packets.

The returned handle can be used to stop the passive ranging broadcast via stopPassiveRanging.

**Since:** 26.0.0

**Required permissions:** ohos.permission.ACCESS_NEARLINK

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Communication.FusionConnectivity.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| capabilityType | [RangingTypes](arkts-connectivity-ranging-rangingtypes-e.md) | Yes | Indicates the capability type for ranging. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;number&gt; | Promise used to return the handle for starts ranging listening. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. |
| [34900052](../errorcode-fusionConnectivity.md#34900052-specified-ranging-service-unsupported) | The specified type of ranging service is not supported. |
| [34900053](../errorcode-fusionConnectivity.md#34900053-ranging-service-disabled) | The ranging service is disabled. |
| [34900099](../errorcode-fusionConnectivity.md#34900099-operation-failed) | Internal system error. For example, Internal object is invalid. |
