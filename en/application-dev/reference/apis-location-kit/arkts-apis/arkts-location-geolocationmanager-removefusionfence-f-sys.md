# removeFusionFence (System API)

## Modules to Import

```TypeScript
import { geoLocationManager } from '@kit.LocationKit';
```

## removeFusionFence

```TypeScript
function removeFusionFence(identifier: string): Promise<void>
```

Remove a fusion fence.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Location.Location.Geofence

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| identifier | string | Yes | Indicates identifier of the fusion fence. The string format should be a valid unique identifier (e.g., GUID or specific alphanumeric pattern). |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Failed to call ${geoLocationManager.removeFusionFence} due to limited device. |
| [3301000](../errorcode-geoLocationManager.md#3301000-location-service-unavailable) | The location service is unavailable. |
| [3301602](../errorcode-geoLocationManager.md#3301602-failed-to-delete-a-geofence-due-to-an-incorrect-id) | Failed to delete a fusion fence due to an incorrect identifier. |
