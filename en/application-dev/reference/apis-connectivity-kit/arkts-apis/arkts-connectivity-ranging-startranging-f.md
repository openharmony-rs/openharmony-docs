# startRanging

## Modules to Import

```TypeScript
import { ranging } from '@kit.ConnectivityKit';
```

## startRanging

```TypeScript
function startRanging(params: RangingParams, callback: Callback<RangingResult>): void
```

Initiates ranging with a specified device. If the link to the target device is already established, ranging starts directly. If not connected, this interface will:
1. Attempt to establish connection and perform pairing/encryption.
2. Query service to verify the device supports ranging. Initiate ranging upon confirmation.
Ranging state updates are notified via onRangingStateChange callback.

**Since:** 26.0.0

**Required permissions:** ohos.permission.ACCESS_NEARLINK

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Communication.FusionConnectivity.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| params | [RangingParams](arkts-connectivity-ranging-rangingparams-i.md) | Yes | Parameters for ranging. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[RangingResult](arkts-connectivity-ranging-rangingresult-i.md)&gt; | Yes | Indicates the callback for reporting the ranging result. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. |
| [34900051](../errorcode-fusionConnectivity.md#34900051-device-has-initiated-ranging) | The device has already initiated ranging. |
| [34900052](../errorcode-fusionConnectivity.md#34900052-specified-ranging-service-unsupported) | The specified type of ranging service is not supported. |
| [34900053](../errorcode-fusionConnectivity.md#34900053-ranging-service-disabled) | The ranging service is disabled. |
| [34900054](../errorcode-fusionConnectivity.md#34900054-invalid-parameters) | The parameter value does not meet specifications. |
| [34900099](../errorcode-fusionConnectivity.md#34900099-operation-failed) | Internal system error. For example, Internal object is invalid. |
