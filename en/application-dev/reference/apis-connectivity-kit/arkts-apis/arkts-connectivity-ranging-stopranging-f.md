# stopRanging

## Modules to Import

```TypeScript
import { ranging } from '@kit.ConnectivityKit';
```

## stopRanging

```TypeScript
function stopRanging(callback: Callback<RangingResult>, params?: RangingParams): void
```

Stops ongoing ranging operations. If no target device is specified, stops ranging for all devices associated with the callback. If a target device is specified, only stops ranging for that specific device. This method also releases all occupied resources. For proper resource management, stopRanging must be called after startRanging to avoid resource leaks. State changes are notified via the onRangingStateChange callback.

**Since:** 26.0.0

**Required permissions:** ohos.permission.ACCESS_NEARLINK

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Communication.FusionConnectivity.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[RangingResult](arkts-connectivity-ranging-rangingresult-i.md)&gt; | Yes | Callback used to return the ranging result. |
| params | [RangingParams](arkts-connectivity-ranging-rangingparams-i.md) | No | Parameters for ranging include deviceId and ranging types. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. |
| [34900050](../errorcode-fusionConnectivity.md#34900050-device-has-not-initiated-ranging) | The device has not initiated ranging. |
| [34900052](../errorcode-fusionConnectivity.md#34900052-specified-ranging-service-unsupported) | The specified type of ranging service is not supported. |
| [34900054](../errorcode-fusionConnectivity.md#34900054-invalid-parameters) | The parameter value does not meet specifications. |
| [34900099](../errorcode-fusionConnectivity.md#34900099-operation-failed) | Internal system error. For example, Internal object is invalid. |
