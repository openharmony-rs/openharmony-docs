# getAddressesFromLocation

## Modules to Import

```TypeScript
import { geolocation } from '@kit.LocationKit';
```

## getAddressesFromLocation

```TypeScript
function getAddressesFromLocation(request: ReverseGeoCodeRequest, callback: AsyncCallback<Array<GeoAddress>>): void
```

Obtain address info from location

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [getAddressesFromLocation](arkts-location-geolocationmanager-getaddressesfromlocation-f.md)

**Required permissions:** ohos.permission.LOCATION

**System capability:** SystemCapability.Location.Location.Geocoder

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| request | [ReverseGeoCodeRequest](arkts-location-geolocation-reversegeocoderequest-i.md) | Yes | Indicates the reverse geocode query parameters. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;Array&lt;[GeoAddress](arkts-location-geolocation-geoaddress-i.md)&gt;&gt; | Yes | Indicates the callback for reporting the address info. |

**Examples**

```TypeScript
import geolocation from '@ohos.geolocation';
let reverseGeocodeRequest:geolocation.ReverseGeoCodeRequest = {"latitude": 31.12, "longitude": 121.11, "maxItems": 1};
geolocation.getAddressesFromLocation(reverseGeocodeRequest, (err, data) => {
    if (err) {
        console.info('getAddressesFromLocation: err=' + JSON.stringify(err));
    }
    if (data) {
        console.info('getAddressesFromLocation: data=' + JSON.stringify(data));
    }
});
```


<a id="getaddressesfromlocation-1"></a>

## getAddressesFromLocation

```TypeScript
function getAddressesFromLocation(request: ReverseGeoCodeRequest): Promise<Array<GeoAddress>>
```

Obtain address info from location

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [getAddressesFromLocation](arkts-location-geolocationmanager-getaddressesfromlocation-f.md)

**Required permissions:** ohos.permission.LOCATION

**System capability:** SystemCapability.Location.Location.Geocoder

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| request | [ReverseGeoCodeRequest](arkts-location-geolocation-reversegeocoderequest-i.md) | Yes | Indicates the reverse geocode query parameters. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;Array&lt;[GeoAddress](arkts-location-geolocation-geoaddress-i.md)&gt;&gt; | The promise returned by the function. |

**Examples**

```TypeScript
import geolocation from '@ohos.geolocation';
let reverseGeocodeRequest:geolocation.ReverseGeoCodeRequest = {"latitude": 31.12, "longitude": 121.11, "maxItems": 1};
geolocation.getAddressesFromLocation(reverseGeocodeRequest).then((data) => {
    console.info('getAddressesFromLocation: ' + JSON.stringify(data));
});
```
