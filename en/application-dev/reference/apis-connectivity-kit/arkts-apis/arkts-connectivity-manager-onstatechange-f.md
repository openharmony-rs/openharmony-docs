# onStateChange

## Modules to Import

```TypeScript
import { manager } from '@kit.ConnectivityKit';
```

## onStateChange

```TypeScript
function onStateChange(callback: Callback<NearlinkState>): void
```

Subscribes to the NearLink status change event. This API uses an asynchronous callback to return the result. Before calling this API, you may call [isNearLinkSupported](arkts-connectivity-manager-isnearlinksupported-f.md) to check whether the device supports NearLink.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.2.0.

<!--Device-manager-function onStateChange(callback: Callback<NearlinkState>): void--><!--Device-manager-function onStateChange(callback: Callback<NearlinkState>): void-End-->

**System capability:** SystemCapability.Communication.NearLink.Base

**See also:** [offStateChange](arkts-connectivity-manager-offstatechange-f.md) Unsubscribes from the NearLink status change event.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[NearlinkState](arkts-connectivity-manager-nearlinkstate-e.md)&gt; | Yes | Callback used to return the NearLink status. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Possible causes:         1. The hardware does not support the capability;         2. The chip does not support the capability;         3. A dependent service feature is not supported. |
| [36100099](../errorcode-nearlink-service.md#36100099-operation-failed) | Operation failed. |
