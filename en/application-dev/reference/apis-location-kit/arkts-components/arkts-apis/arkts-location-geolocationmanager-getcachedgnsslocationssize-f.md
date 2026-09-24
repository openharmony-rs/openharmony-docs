# getCachedGnssLocationsSize

## Modules to Import

```TypeScript
import { geoLocationManager } from '@kit.LocationKit';
```

## getCachedGnssLocationsSize

```TypeScript
function getCachedGnssLocationsSize(callback: AsyncCallback<number>): void
```

Obtain the number of cached GNSS locations reported at a time.

**Since:** 9

**Required permissions:** ohos.permission.APPROXIMATELY_LOCATION

**System capability:** SystemCapability.Location.Location.Gnss

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;number&gt; | Yes | Indicates the callback for reporting the cached GNSS locations size. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Failed to call ${geoLocationManager.getCachedGnssLocationsSize} due to limited device capabilities. |
| [3301000](../errorcode-geoLocationManager.md#3301000-location-service-unavailable) | The location service is unavailable. |
| [3301100](../errorcode-geoLocationManager.md#3301100-positioning-failed-because-the-location-switch-is-turned-off) | The location switch is off. |

**Examples**

```TypeScript
import { geoLocationManager } from '@kit.LocationKit';

try {
  geoLocationManager.getCachedGnssLocationsSize((err, size) => {
    if (err) {
      console.error('getCachedGnssLocationsSize: err=' + JSON.stringify(err));
    }
    if (size) {
      console.info('getCachedGnssLocationsSize: size=' + JSON.stringify(size));
    }
  });
} catch (err) {
  console.error("errCode:" + err.code + ", message:" + err.message);
}
```


<a id="getcachedgnsslocationssize-1"></a>

## getCachedGnssLocationsSize

```TypeScript
function getCachedGnssLocationsSize(): Promise<number>
```

Obtain the number of cached GNSS locations.

**Since:** 9

**Required permissions:** ohos.permission.APPROXIMATELY_LOCATION

**System capability:** SystemCapability.Location.Location.Gnss

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;number&gt; | The promise returned by the function. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Failed to call ${geoLocationManager.getCachedGnssLocationsSize} due to limited device capabilities. |
| [3301000](../errorcode-geoLocationManager.md#3301000-location-service-unavailable) | The location service is unavailable. |
| [3301100](../errorcode-geoLocationManager.md#3301100-positioning-failed-because-the-location-switch-is-turned-off) | The location switch is off. |

**Examples**

```TypeScript
import { geoLocationManager } from '@kit.LocationKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  geoLocationManager.getCachedGnssLocationsSize().then((result) => {
    console.info('promise, getCachedGnssLocationsSize: ' + JSON.stringify(result));
  })
    .catch((error: BusinessError) => {
      console.error('promise, getCachedGnssLocationsSize: error=' + JSON.stringify(error));
    });
} catch (err) {
  console.error("errCode:" + err.code + ", message:" + err.message);
}
```
