# onRangingStateChange

## Modules to Import

```TypeScript
import { ranging } from '@kit.ConnectivityKit';
```

## onRangingStateChange

```TypeScript
function onRangingStateChange(callback: Callback<RangingStateChangeInfo>): void
```

Registers a callback to receive ranging state change notifications.

Notifies state changes for both active ranging and passive ranging operations.

**Since:** 26.0.0

**Required permissions:** ohos.permission.ACCESS_NEARLINK

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Communication.FusionConnectivity.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[RangingStateChangeInfo](arkts-connectivity-ranging-rangingstatechangeinfo-i.md)&gt; | Yes | Callback used to listen for the ranging state. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. |
| [34900099](../errorcode-fusionConnectivity.md#34900099-operation-failed) | Internal system error. For example, Internal object is invalid. |
