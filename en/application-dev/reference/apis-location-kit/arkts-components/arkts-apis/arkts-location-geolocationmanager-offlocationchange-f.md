# offLocationChange

## Modules to Import

```TypeScript
import { geoLocationManager } from '@kit.LocationKit';
```

## offLocationChange

```TypeScript
function offLocationChange(callback?: Callback<Location>): void
```

Unsubscribe location changed.

**Since:** 26.0.0

**Required permissions:** 
- API version 25 and later: N/A
- API versions 23 to 24: ohos.permission.APPROXIMATELY_LOCATION

**System capability:** 
- API version 23 and later: SystemCapability.Location.Location.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[Location](arkts-location-geolocationmanager-location-i.md)&gt; | No | Indicates the callback for reporting the location result.<br>**Since:** 23 |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. Introduced in API 9 and will not be threw above API 24.<br>**Applicable version:** 23 - 24 |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Failed to call &#36;{geoLocationManager.offLocationChange} due to limited device capabilities.<br>**Applicable version:** 23 and later |
| [3301000](../errorcode-geoLocationManager.md#3301000-location-service-unavailable) | The location service is unavailable.<br>**Applicable version:** 23 and later |
