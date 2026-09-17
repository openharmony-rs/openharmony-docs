# offStateChange

## Modules to Import

```TypeScript
import { manager } from '@kit.ConnectivityKit';
```

## offStateChange

```TypeScript
function offStateChange(callback?: Callback<NearlinkState>): void
```

Unsubscribes from the NearLink status change event. This API uses an asynchronous callback to return the result.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Communication.NearLink.Base

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[NearlinkState](arkts-connectivity-manager-nearlinkstate-e.md)&gt; | No | Callback used to return the NearLink status.<br>If this parameter is specified, the current callback is unregistered. If this parameter is not specified, all callbacks corresponding to the event are unregistered. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported because the chip does not support it. |
| [36100099](../errorcode-nearlink-service.md#36100099-operation-failed) | Operation failed. |
