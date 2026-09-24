# getCurrentLocation

## Modules to Import

```TypeScript
import { geoLocationManager } from '@kit.LocationKit';
```

## getCurrentLocation

```TypeScript
function getCurrentLocation(request: CurrentLocationRequest | SingleLocationRequest,
  callback: AsyncCallback<Location>): void
```

Obtain current location.

**Since:** 9

**Required permissions:** ohos.permission.APPROXIMATELY_LOCATION

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Location.Location.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| request | [CurrentLocationRequest](arkts-location-geolocationmanager-currentlocationrequest-i.md) &#124; [SingleLocationRequest](arkts-location-geolocationmanager-singlelocationrequest-i.md) | Yes | Indicates the location request parameters.<br>**Since:** 12 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[Location](arkts-location-geolocationmanager-location-i.md)&gt; | Yes | Indicates the callback for reporting the location result. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Failed to call ${geoLocationManager.getCurrentLocation} due to limited device capabilities. |
| [3301000](../errorcode-geoLocationManager.md#3301000-location-service-unavailable) | The location service is unavailable. |
| [3301100](../errorcode-geoLocationManager.md#3301100-positioning-failed-because-the-location-switch-is-turned-off) | The location switch is off. |
| [3301200](../errorcode-geoLocationManager.md#3301200-failed-to-obtain-the-positioning-result) | Failed to obtain the geographical location. |

**Examples**

```TypeScript
import { geoLocationManager } from '@kit.LocationKit';
import { BusinessError } from '@kit.BasicServicesKit';
// Method 1: Use CurrentLocationRequest as the input parameter.
let requestInfo: geoLocationManager.CurrentLocationRequest = {
  'priority': geoLocationManager.LocationRequestPriority.FIRST_FIX,
  'scenario': geoLocationManager.LocationRequestScenario.UNSET,
  'maxAccuracy': 0
};
let locationChange = (err: BusinessError, location: geoLocationManager.Location): void => {
  if (err) {
    console.error('locationChange: err=' + JSON.stringify(err));
  }
  if (location) {
    console.info('locationChange: location=' + JSON.stringify(location));
  }
};

try {
  geoLocationManager.getCurrentLocation(requestInfo, locationChange);
} catch (err) {
  console.error("errCode:" + err.code + ", message:" + err.message);
}

// Method 2: Use SingleLocationRequest as the input parameter.
let request: geoLocationManager.SingleLocationRequest = {
  'locatingTimeoutMs': 10000,
  'locatingPriority': geoLocationManager.LocatingPriority.PRIORITY_ACCURACY
};
let locationCallback = (err: BusinessError, location: geoLocationManager.Location): void => {
  if (err) {
    console.error('locationChange: err=' + JSON.stringify(err));
  }
  if (location) {
    console.info('locationChange: location=' + JSON.stringify(location));
  }
};

try {
  geoLocationManager.getCurrentLocation(request, locationCallback);
} catch (err) {
  console.error("errCode:" + err.code + ", message:" + err.message);
}
```


<a id="getcurrentlocation-1"></a>

## getCurrentLocation

```TypeScript
function getCurrentLocation(callback: AsyncCallback<Location>): void
```

Obtain current location.

**Since:** 9

**Required permissions:** ohos.permission.APPROXIMATELY_LOCATION

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Location.Location.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[Location](arkts-location-geolocationmanager-location-i.md)&gt; | Yes | Indicates the callback for reporting the location result. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Failed to call ${geoLocationManager.getCurrentLocation} due to limited device capabilities. |
| [3301000](../errorcode-geoLocationManager.md#3301000-location-service-unavailable) | The location service is unavailable. |
| [3301100](../errorcode-geoLocationManager.md#3301100-positioning-failed-because-the-location-switch-is-turned-off) | The location switch is off. |
| [3301200](../errorcode-geoLocationManager.md#3301200-failed-to-obtain-the-positioning-result) | Failed to obtain the geographical location. |

**Examples**

```TypeScript
import { geoLocationManager } from '@kit.LocationKit';
import { BusinessError } from '@kit.BasicServicesKit';

let locationChange = (err: BusinessError, location: geoLocationManager.Location) => {
  if (err) {
    console.error('locationChange: err=' + JSON.stringify(err));
  }
  if (location) {
    console.info('locationChange: location=' + JSON.stringify(location));
  }
};

try {
  geoLocationManager.getCurrentLocation(locationChange);
} catch (err) {
  console.error("errCode:" + err.code + ", message:" + err.message);
}
```


<a id="getcurrentlocation-2"></a>

## getCurrentLocation

```TypeScript
function getCurrentLocation(request?: CurrentLocationRequest | SingleLocationRequest):
  Promise<Location>
```

Obtain current location.

**Since:** 9

**Required permissions:** ohos.permission.APPROXIMATELY_LOCATION

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Location.Location.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| request | [CurrentLocationRequest](arkts-location-geolocationmanager-currentlocationrequest-i.md) &#124; [SingleLocationRequest](arkts-location-geolocationmanager-singlelocationrequest-i.md) | No | Indicates the location request parameters.<br>**Since:** 12 |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[Location](arkts-location-geolocationmanager-location-i.md)&gt; | The promise returned by the function. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Failed to call ${geoLocationManager.getCurrentLocation} due to limited device capabilities. |
| [3301000](../errorcode-geoLocationManager.md#3301000-location-service-unavailable) | The location service is unavailable. |
| [3301100](../errorcode-geoLocationManager.md#3301100-positioning-failed-because-the-location-switch-is-turned-off) | The location switch is off. |
| [3301200](../errorcode-geoLocationManager.md#3301200-failed-to-obtain-the-positioning-result) | Failed to obtain the geographical location. |

**Examples**

```TypeScript
import { geoLocationManager } from '@kit.LocationKit';
import { BusinessError } from '@kit.BasicServicesKit';

// Method 1: Use CurrentLocationRequest as the input parameter.
let requestInfo: geoLocationManager.CurrentLocationRequest = {
  'priority': geoLocationManager.LocationRequestPriority.FIRST_FIX,
  'scenario': geoLocationManager.LocationRequestScenario.UNSET,
  'maxAccuracy': 0
};
try {
  geoLocationManager.getCurrentLocation(requestInfo).then((result) => {
    console.info('current location: ' + JSON.stringify(result));
  })
    .catch((error: BusinessError) => {
      console.error('promise, getCurrentLocation: error=' + JSON.stringify(error));
    });
} catch (err) {
  console.error("errCode:" + err.code + ", message:" + err.message);
}

// Method 2: Use SingleLocationRequest as the input parameter.
let request: geoLocationManager.SingleLocationRequest = {
  'locatingTimeoutMs': 10000,
  'locatingPriority': geoLocationManager.LocatingPriority.PRIORITY_ACCURACY
};
try {
  geoLocationManager.getCurrentLocation(request).then((result) => {
    console.info('current location: ' + JSON.stringify(result));
  })
    .catch((error: BusinessError) => {
      console.error('promise, getCurrentLocation: error=' + JSON.stringify(error));
    });
} catch (err) {
  console.error("errCode:" + err.code + ", message:" + err.message);
}
```
