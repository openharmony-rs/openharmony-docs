# flushCachedGnssLocations

## Modules to Import

```TypeScript
import { geolocation } from '@kit.LocationKit';
```

## flushCachedGnssLocations

```TypeScript
function flushCachedGnssLocations(callback: AsyncCallback<boolean>): void
```

All prepared GNSS locations are returned to the application through the callback function, and the bottom-layer buffer is cleared.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [flushCachedGnssLocations](arkts-location-geolocationmanager-flushcachedgnsslocations-f.md)

**Required permissions:** ohos.permission.LOCATION

**System capability:** SystemCapability.Location.Location.Gnss

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;boolean&gt; | Yes | Indicates the callback for reporting the result. |

**Examples**

```TypeScript
import geolocation from '@ohos.geolocation';
geolocation.flushCachedGnssLocations((err, result) => {
    if (err) {
        console.info('flushCachedGnssLocations: err=' + JSON.stringify(err));
    }
    if (result) {
        console.info('flushCachedGnssLocations: result=' + JSON.stringify(result));
    }
});
```

```TypeScript
import geolocation from '@ohos.geolocation';
geolocation.flushCachedGnssLocations().then((result) => {
    console.info('promise, flushCachedGnssLocations: ' + JSON.stringify(result));
});
```


## flushCachedGnssLocations

```TypeScript
function flushCachedGnssLocations(): Promise<boolean>
```

All prepared GNSS locations are returned to the application through the callback function, and the bottom-layer buffer is cleared.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [flushCachedGnssLocations](arkts-location-geolocationmanager-flushcachedgnsslocations-f.md)

**Required permissions:** ohos.permission.LOCATION

**System capability:** SystemCapability.Location.Location.Gnss

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;boolean&gt; | The promise returned by the function. |

**Examples**

See [flushCachedGnssLocations](#flushcachedgnsslocations)
