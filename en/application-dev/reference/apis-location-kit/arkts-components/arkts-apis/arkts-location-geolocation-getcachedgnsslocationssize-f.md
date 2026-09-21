# getCachedGnssLocationsSize

## Modules to Import

```TypeScript
import { geolocation } from '@kit.LocationKit';
```

## getCachedGnssLocationsSize

```TypeScript
function getCachedGnssLocationsSize(callback: AsyncCallback<number>): void
```

Obtain the number of cached GNSS locations reported at a time

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [getCachedGnssLocationsSize](arkts-location-geolocationmanager-getcachedgnsslocationssize-f.md)

**Required permissions:** ohos.permission.LOCATION

**System capability:** SystemCapability.Location.Location.Gnss

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;number&gt; | Yes | Indicates the callback for reporting the cached GNSS locations size. |

**Examples**

```TypeScript
import geolocation from '@ohos.geolocation';
geolocation.getCachedGnssLocationsSize((err, size) => {
    if (err) {
        console.info('getCachedGnssLocationsSize: err=' + JSON.stringify(err));
    }
    if (size) {
        console.info('getCachedGnssLocationsSize: size=' + JSON.stringify(size));
    }
});
```


<a id="getcachedgnsslocationssize-1"></a>

## getCachedGnssLocationsSize

```TypeScript
function getCachedGnssLocationsSize(): Promise<number>
```

Obtain the number of cached GNSS locations reported at a time

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [getCachedGnssLocationsSize](arkts-location-geolocationmanager-getcachedgnsslocationssize-f.md)

**Required permissions:** ohos.permission.LOCATION

**System capability:** SystemCapability.Location.Location.Gnss

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;number&gt; | The promise returned by the function. |

**Examples**

```TypeScript
import geolocation from '@ohos.geolocation';
geolocation.getCachedGnssLocationsSize().then((result) => {
    console.info('promise, getCachedGnssLocationsSize: ' + JSON.stringify(result));
});
```
