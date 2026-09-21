# getLastLocation

## Modules to Import

```TypeScript
import { geolocation } from '@kit.LocationKit';
```

## getLastLocation

```TypeScript
function getLastLocation(callback: AsyncCallback<Location>): void
```

Obtain last known location

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [getLastLocation](arkts-location-geolocationmanager-getlastlocation-f.md)

**Required permissions:** ohos.permission.LOCATION

**System capability:** SystemCapability.Location.Location.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[Location](arkts-location-geolocation-location-i.md)&gt; | Yes | Indicates the callback for reporting the location result. |

**Examples**

```TypeScript
import geolocation from '@ohos.geolocation';
geolocation.getLastLocation((err, data) => {
    if (err) {
        console.info('getLastLocation: err=' + JSON.stringify(err));
    }
    if (data) {
        console.info('getLastLocation: data=' + JSON.stringify(data));
    }
});
```


<a id="getlastlocation-1"></a>

## getLastLocation

```TypeScript
function getLastLocation(): Promise<Location>
```

Obtain last known location

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [getLastLocation](arkts-location-geolocationmanager-getlastlocation-f.md)

**Required permissions:** ohos.permission.LOCATION

**System capability:** SystemCapability.Location.Location.Core

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[Location](arkts-location-geolocation-location-i.md)&gt; | The promise returned by the function. |

**Examples**

```TypeScript
import geolocation from '@ohos.geolocation';
geolocation.getLastLocation().then((result) => {
    console.info('getLastLocation: result: ' + JSON.stringify(result));
});
```
