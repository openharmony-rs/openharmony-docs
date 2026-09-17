# getCurrentLocation

## Modules to Import

```TypeScript
import { geolocation } from '@kit.LocationKit';
```

## getCurrentLocation

```TypeScript
function getCurrentLocation(request: CurrentLocationRequest, callback: AsyncCallback<Location>): void
```

Obtain current location

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [getCurrentLocation](arkts-location-geolocationmanager-getcurrentlocation-f.md)

**Required permissions:** ohos.permission.LOCATION

**System capability:** SystemCapability.Location.Location.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| request | [CurrentLocationRequest](arkts-location-geolocation-currentlocationrequest-i.md) | Yes | Indicates the location request parameters. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[Location](arkts-location-geolocation-location-i.md)&gt; | Yes | Indicates the callback for reporting the location result. |

**Examples**

```TypeScript
import geolocation from '@ohos.geolocation';
import BusinessError from "@ohos.base"
let requestInfo:geolocation.CurrentLocationRequest = {'priority': 0x203, 'scenario': 0x300,'maxAccuracy': 0};
let locationChange = (err:BusinessError.BusinessError, location:geolocation.Location) => {
    if (err) {
        console.info('locationChanger: err=' + JSON.stringify(err));
    }
    if (location) {
        console.info('locationChanger: location=' + JSON.stringify(location));
    }
};
geolocation.getCurrentLocation(requestInfo, locationChange);
```

```TypeScript
import geolocation from '@ohos.geolocation';
import BusinessError from "@ohos.base"
let locationChange = (err:BusinessError.BusinessError, location:geolocation.Location):void => {
    if (err) {
        console.info('locationChanger: err=' + JSON.stringify(err));
    }
    if (location) {
        console.info('locationChanger: location=' + JSON.stringify(location));
    }
};
geolocation.getCurrentLocation(locationChange);
```

```TypeScript
import geolocation from '@ohos.geolocation';
let requestInfo:geolocation.CurrentLocationRequest = {'priority': 0x203, 'scenario': 0x300,'maxAccuracy': 0};
geolocation.getCurrentLocation(requestInfo).then((result) => {
    console.info('current location: ' + JSON.stringify(result));
});
```


## getCurrentLocation

```TypeScript
function getCurrentLocation(callback: AsyncCallback<Location>): void
```

Obtain current location

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [getCurrentLocation](arkts-location-geolocationmanager-getcurrentlocation-f.md)

**Required permissions:** ohos.permission.LOCATION

**System capability:** SystemCapability.Location.Location.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[Location](arkts-location-geolocation-location-i.md)&gt; | Yes | Indicates the callback for reporting the location result. |

**Examples**

See [getCurrentLocation](#getcurrentlocation)


## getCurrentLocation

```TypeScript
function getCurrentLocation(request?: CurrentLocationRequest): Promise<Location>
```

Obtain current location

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [getCurrentLocation](arkts-location-geolocationmanager-getcurrentlocation-f.md)

**Required permissions:** ohos.permission.LOCATION

**System capability:** SystemCapability.Location.Location.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| request | [CurrentLocationRequest](arkts-location-geolocation-currentlocationrequest-i.md) | No | Indicates the location request parameters. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[Location](arkts-location-geolocation-location-i.md)&gt; | The promise returned by the function. |

**Examples**

See [getCurrentLocation](#getcurrentlocation)
