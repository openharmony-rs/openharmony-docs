# on

## Modules to Import

```TypeScript
import { geolocation } from '@kit.LocationKit';
```

## on('locationChange')

```TypeScript
function on(type: 'locationChange', request: LocationRequest, callback: Callback<Location>): void
```

Subscribe location changed

**Since:** 7

**Deprecated since:** 9

**Substitutes:** locationChange

**Required permissions:** ohos.permission.LOCATION

**System capability:** SystemCapability.Location.Location.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'locationChange' | Yes | Indicates the location service event to be subscribed to. |
| request | [LocationRequest](arkts-location-geolocation-locationrequest-i.md) | Yes | Indicates the location request parameters. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[Location](arkts-location-geolocation-location-i.md)&gt; | Yes | Indicates the callback for reporting the location result. |


## on('locationServiceState')

```TypeScript
function on(type: 'locationServiceState', callback: Callback<boolean>): void
```

Subscribe location switch changed

**Since:** 7

**Deprecated since:** 9

**Substitutes:** locationEnabledChange

**Required permissions:** ohos.permission.LOCATION

**System capability:** SystemCapability.Location.Location.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'locationServiceState' | Yes | Indicates the location service event to be subscribed to. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;boolean&gt; | Yes | Indicates the callback for reporting the location result. |


## on('cachedGnssLocationsReporting')

```TypeScript
function on(type: 'cachedGnssLocationsReporting', request: CachedGnssLocationsRequest, callback: Callback<Array<Location>>): void
```

Subscribe to cache GNSS locations update messages

**Since:** 8

**Deprecated since:** 9

**Substitutes:** cachedGnssLocationsChange

**Required permissions:** ohos.permission.LOCATION

**System capability:** SystemCapability.Location.Location.Gnss

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'cachedGnssLocationsReporting' | Yes | Indicates the location service event to be subscribed to. |
| request | [CachedGnssLocationsRequest](arkts-location-geolocation-cachedgnsslocationsrequest-i.md) | Yes | Indicates the cached GNSS locations request parameters. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;Array&lt;[Location](arkts-location-geolocation-location-i.md)&gt;&gt; | Yes | Indicates the callback for reporting the cached GNSS locations. |


## on('gnssStatusChange')

```TypeScript
function on(type: 'gnssStatusChange', callback: Callback<SatelliteStatusInfo>): void
```

Subscribe gnss status changed

**Since:** 8

**Deprecated since:** 9

**Substitutes:** satelliteStatusChange

**Required permissions:** ohos.permission.LOCATION

**System capability:** SystemCapability.Location.Location.Gnss

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'gnssStatusChange' | Yes | Indicates the location service event to be subscribed to. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[SatelliteStatusInfo](arkts-location-geolocation-satellitestatusinfo-i.md)&gt; | Yes | Indicates the callback for reporting the gnss status change. |


## on('nmeaMessageChange')

```TypeScript
function on(type: 'nmeaMessageChange', callback: Callback<string>): void
```

Subscribe nmea message changed

**Since:** 8

**Deprecated since:** 9

**Substitutes:** nmeaMessage

**Required permissions:** ohos.permission.LOCATION

**System capability:** SystemCapability.Location.Location.Gnss

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'nmeaMessageChange' | Yes | Indicates the location service event to be subscribed to. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;string&gt; | Yes | Indicates the callback for reporting the nmea message. |


## on('fenceStatusChange')

```TypeScript
function on(type: 'fenceStatusChange', request: GeofenceRequest, want: WantAgent): void
```

Add a geofence and subscribe geo fence status changed

**Since:** 8

**Deprecated since:** 9

**Substitutes:** gnssFenceStatusChange

**Required permissions:** ohos.permission.LOCATION

**System capability:** SystemCapability.Location.Location.Geofence

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'fenceStatusChange' | Yes | Indicates the location service event to be subscribed to. |
| request | [GeofenceRequest](arkts-location-geolocation-geofencerequest-i.md) | Yes | Indicates the Geo-fence configuration parameters. |
| want | [WantAgent](../../apis-ability-kit/arkts-apis/arkts-ability-wantagent-depr-t.md) | Yes | Indicates which ability to start when the geofence event is triggered. |
