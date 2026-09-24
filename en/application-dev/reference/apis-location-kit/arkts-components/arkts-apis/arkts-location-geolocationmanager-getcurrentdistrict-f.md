# getCurrentDistrict

## Modules to Import

```TypeScript
import { geoLocationManager } from '@kit.LocationKit';
```

## getCurrentDistrict

```TypeScript
function getCurrentDistrict(params?: DistrictRequestParams): Promise<DistrictInfo>
```

Obtains the information about the district where the current device is located.

**Since:** 26.0.0

**Required permissions:** ohos.permission.APPROXIMATELY_LOCATION

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.Location.Location.Geocoder

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| params | [DistrictRequestParams](arkts-location-geolocationmanager-districtrequestparams-i.md) | No | Indicates request parameters for obtaining the district information. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[DistrictInfo](arkts-location-geolocationmanager-districtinfo-i.md)&gt; | Promise used to return ${DistrictInfo}. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Failed to call ${geoLocationManager.getCurrentDistrict} due to limited device capabilities. |
| [3301000](../errorcode-geoLocationManager.md#3301000-location-service-unavailable) | The location service is unavailable. |
| [3301100](../errorcode-geoLocationManager.md#3301100-positioning-failed-because-the-location-switch-is-turned-off) | The location switch is off. |
| [3301500](../errorcode-geoLocationManager.md#3301500-area-information-query-failed) | Failed to query the area information because the reverse geocoding server returns an error. |
