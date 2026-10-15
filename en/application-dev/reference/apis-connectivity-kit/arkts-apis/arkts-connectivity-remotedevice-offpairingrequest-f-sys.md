# offPairingRequest (System API)

## Modules to Import

```TypeScript
import { remoteDevice } from '@kit.ConnectivityKit';
```

## offPairingRequest

```TypeScript
function offPairingRequest(callback?: Callback<PairingRequestParam>): void
```

Unsubscribes from pairing request events from remote NearLink devices. Before calling this API, you may call [isNearLinkSupported](arkts-connectivity-manager-isnearlinksupported-f.md) to check whether the device supports NearLink.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.2.0.

<!--Device-remoteDevice-function offPairingRequest(callback?: Callback<PairingRequestParam>): void--><!--Device-remoteDevice-function offPairingRequest(callback?: Callback<PairingRequestParam>): void-End-->

**System capability:** SystemCapability.Communication.NearLink.Base

**System API:** This is a system API.

**See also:** [onPairingRequest](arkts-connectivity-remotedevice-onpairingrequest-f-sys.md) Subscribes to the pairing request event.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[PairingRequestParam](arkts-connectivity-remotedevice-pairingrequestparam-i.md)&gt; | No | Callback used to listen for the pairing request event. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Possible causes:         1. The hardware does not support the capability;         2. The chip does not support the capability;         3. A dependent service feature is not supported. |
| [36100099](../errorcode-nearlink-service.md#36100099-operation-failed) | Operation failed. |
