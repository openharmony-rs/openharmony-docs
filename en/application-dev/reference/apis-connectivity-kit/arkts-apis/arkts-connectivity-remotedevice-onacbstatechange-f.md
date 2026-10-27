# onAcbStateChange

## Modules to Import

```TypeScript
import { remoteDevice } from '@kit.ConnectivityKit';
```

## onAcbStateChange

```TypeScript
function onAcbStateChange(callback: Callback<AcbStateParam>): void
```

Subscribes to the logical link connection status change event. This API uses an asynchronous callback to return the result. This API is applicable when corresponding processing needs to be triggered when a logical link is established or disconnected, for example, checking whether the link is ready before data transfer or clearing resources after disconnection. Unlike [remoteDevice.onConnectionStateChange](arkts-connectivity-remotedevice-onconnectionstatechange-f.md#onconnectionstatechange-1) which listens for the connection status change at the device level, this API listens for the connection status change at the logical link level.

The app must have the **ohos.permission.ACCESS_NEARLINK** permission to receive this event. Before calling this API, you may call [isNearLinkSupported](arkts-connectivity-manager-isnearlinksupported-f.md) to check whether the device supports NearLink.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.1.0.

<!--Device-remoteDevice-function onAcbStateChange(callback: Callback<AcbStateParam>): void--><!--Device-remoteDevice-function onAcbStateChange(callback: Callback<AcbStateParam>): void-End-->

**System capability:** SystemCapability.Communication.NearLink.Base

**See also:** [offAcbStateChange](arkts-connectivity-remotedevice-offacbstatechange-f.md#offacbstatechange-1) Unsubscribes from the logical link connection status change event.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[AcbStateParam](arkts-connectivity-remotedevice-acbstateparam-i.md)&gt; | Yes | Callback used to return the result of the logical link connection status change event. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Possible causes:         1. The hardware does not support the capability;         2. The chip does not support the capability;         3. A dependent service feature is not supported. |
| [36100099](../errorcode-nearlink-service.md#36100099-operation-failed) | Operation failed. |
