# isLocationEnabled

## Modules to Import

```TypeScript
import { geolocation } from '@kit.LocationKit';
```

## isLocationEnabled

```TypeScript
function isLocationEnabled(callback: AsyncCallback<boolean>): void
```

Obtain current location switch status

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [isLocationEnabled](arkts-location-geolocationmanager-islocationenabled-f.md)

**Required permissions:** ohos.permission.LOCATION

**System capability:** SystemCapability.Location.Location.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;boolean&gt; | Yes | Indicates the callback for reporting the location switch result. |

**Examples**

```TypeScript
import geolocation from '@ohos.geolocation';
geolocation.isLocationEnabled((err, data) => {
    if (err) {
        console.info('isLocationEnabled: err=' + JSON.stringify(err));
    }
    if (data) {
        console.info('isLocationEnabled: data=' + JSON.stringify(data));
    }
});
```

```TypeScript
import geolocation from '@ohos.geolocation';
geolocation.isLocationEnabled().then((result) => {
    console.info('promise, isLocationEnabled: ' + JSON.stringify(result));
});
```


## isLocationEnabled

```TypeScript
function isLocationEnabled(): Promise<boolean>
```

Obtain current location switch status

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [isLocationEnabled](arkts-location-geolocationmanager-islocationenabled-f.md)

**Required permissions:** ohos.permission.LOCATION

**System capability:** SystemCapability.Location.Location.Core

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;boolean&gt; | The promise returned by the function. |

**Examples**

See [isLocationEnabled](#islocationenabled)
