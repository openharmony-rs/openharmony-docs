# addFusionFence (System API)

## Modules to Import

```TypeScript
import { geoLocationManager } from '@kit.LocationKit';
```

## addFusionFence

```TypeScript
function addFusionFence(fenceRequestParams: FusionFenceRequestParams): Promise<void>
```

Add a fusion fence.

**Since:** 26.0.0

**Required permissions:** ohos.permission.LOCATION

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Location.Location.Geofence

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| fenceRequestParams | [FusionFenceRequestParams](arkts-location-geolocationmanager-fusionfencerequestparams-i-sys.md) | Yes | Indicates the fusion fence request parameters. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Failed to call ${geoLocationManager.addFusionFence} due to limited device. |
| [3301000](../errorcode-geoLocationManager.md#3301000-location-service-unavailable) | The location service is unavailable. |
| [3301100](../errorcode-geoLocationManager.md#3301100-positioning-failed-because-the-location-switch-is-turned-off) | The location switch is off. |
| [3501603](../errorcode-geoLocationManager.md#3501603-failed-to-add-a-beacon-fence-because-of-duplication) | Duplicate fusion fence identifier. |
| [3301601](../errorcode-geoLocationManager.md#3301601-failed-to-add-a-geofence-because-the-maximum-number-is-exceeded) | The number of geofences exceeds the maximum. |
