# getPostProcessingTrack

## Modules to Import

```TypeScript
import { geoLocationManager } from '@kit.LocationKit';
```

## getPostProcessingTrack

```TypeScript
function getPostProcessingTrack(sportsType: SportsType): Promise<Array<Location>>
```

Obtain post-processing trajectory information under specific sport mode. Only [SKIING](arkts-location-geolocationmanager-sportstype-e.md#skiing) is supported currently.

Before calling this API, you need to call on('locationChange') and set the input parameter [sportsType](arkts-location-geolocationmanager-continuouslocationrequest-i.md#sportstype) to the specific sport mode to start tracking.

Returns data within 24 hours since tracking started; Subsequent calls return only new records.

**Since:** 26.0.0

**Required permissions:** ohos.permission.LOCATION

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.Location.Location.Gnss

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| sportsType | [SportsType](arkts-location-geolocationmanager-sportstype-e.md) | Yes | Indicate the type of sports. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;Array&lt;[Location](arkts-location-geolocationmanager-location-i.md)&gt;&gt; | Promise used to return `Array&lt;Location&gt;`. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Failed to call ${geoLocationManager.getPostProcessingTrack} due to limited device capabilities. |
| [3301000](../errorcode-geoLocationManager.md#3301000-location-service-unavailable) | The location service is unavailable. |
| [3301100](../errorcode-geoLocationManager.md#3301100-positioning-failed-because-the-location-switch-is-turned-off) | The location switch is off. |
| [3301200](../errorcode-geoLocationManager.md#3301200-failed-to-obtain-the-positioning-result) | Failed to obtain the post processing track because sports type is not supported. |
