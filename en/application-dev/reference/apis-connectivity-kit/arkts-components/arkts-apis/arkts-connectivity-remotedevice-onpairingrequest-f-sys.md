# onPairingRequest (System API)

## Modules to Import

```TypeScript
import { remoteDevice } from '@kit.ConnectivityKit';
```

## onPairingRequest

```TypeScript
function onPairingRequest(callback: Callback<PairingRequestParam>): void
```

Subscribes to pairing request events from remote NearLink devices.

This event is accessible only to system applications that granted the ohos.permission.NEARLINK_ACCESS permission. If the application is granted the ohos.permission.GET_NEARLINK_PEER_MAC permission, the callback returns the real device address; otherwise, a random device address is returned.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Communication.NearLink.Base

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[PairingRequestParam](arkts-connectivity-remotedevice-pairingrequestparam-i.md)&gt; | Yes | Callback used to listen for the pairing request event. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported because the chip does not support it. |
| [36100099](../errorcode-nearlink-service.md#36100099-operation-failed) | Operation failed. |
