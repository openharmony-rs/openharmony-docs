# onReadData

## Modules to Import

```TypeScript
import { dataTransfer } from '@kit.ConnectivityKit';
```

## onReadData

```TypeScript
function onReadData(callback: Callback<DataParams>): void
```

Subscribes to the port channel data receiving event. This API uses an asynchronous callback to return the result.

The app must have the **ohos.permission.ACCESS_NEARLINK** permission to receive this event. Before calling this API, you may call [isNearLinkSupported](arkts-connectivity-manager-isnearlinksupported-f.md) to check whether the device supports NearLink.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.1.0.

<!--Device-dataTransfer-function onReadData(callback: Callback<DataParams>): void--><!--Device-dataTransfer-function onReadData(callback: Callback<DataParams>): void-End-->

**System capability:** SystemCapability.Communication.NearLink.Base

**See also:** [offReadData](arkts-connectivity-datatransfer-offreaddata-f.md#offreaddata-1) Unsubscribes from the data receiving event of the port channel.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[DataParams](arkts-connectivity-datatransfer-dataparams-i.md)&gt; | Yes | Callback used to return the parameters for data received by the port channel. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Possible causes:         1. The hardware does not support the capability;         2. The chip does not support the capability;         3. A dependent service feature is not supported. |
| [36100099](../errorcode-nearlink-service.md#36100099-operation-failed) | Operation failed. |
