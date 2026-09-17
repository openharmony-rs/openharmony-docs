# onPairingStateChange

## Modules to Import

```TypeScript
import { remoteDevice } from '@kit.ConnectivityKit';
```

## onPairingStateChange

```TypeScript
function onPairingStateChange(callback: Callback<PairingStateParam>): void
```

Subscribes to pairing status change events. This API uses an asynchronous callback to return the result.

The app must have the **ohos.permission.ACCESS_NEARLINK** permission to receive this event.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Communication.NearLink.Base

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[PairingStateParam](arkts-connectivity-remotedevice-pairingstateparam-i.md)&gt; | Yes | Callback used to return the result of the pairing status change event. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported because the chip does not support it. |
| [36100099](../errorcode-nearlink-service.md#36100099-operation-failed) | Operation failed. |
