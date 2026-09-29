# Geofence

```TypeScript
export interface Geofence
```

Circular fence information.

**Since:** 9

<!--Device-geoLocationManager-export interface Geofence--><!--Device-geoLocationManager-export interface Geofence-End-->

**System capability:** SystemCapability.Location.Location.Geofence

## Modules to Import

```TypeScript
import { geoLocationManager } from '@kit.LocationKit';
```

## coordinateSystemType

```TypeScript
coordinateSystemType?: CoordinateSystemType
```

Coordinate system type.

**Type:** [CoordinateSystemType](arkts-location-geolocationmanager-coordinatesystemtype-e.md)

**Since:** 12

<!--Device-Geofence-coordinateSystemType?: CoordinateSystemType--><!--Device-Geofence-coordinateSystemType?: CoordinateSystemType-End-->

**System capability:** SystemCapability.Location.Location.Geofence

## expiration

```TypeScript
expiration: number
```

Expiration of the circular fence.

**Type:** number

**Since:** 9

<!--Device-Geofence-expiration: double--><!--Device-Geofence-expiration: double-End-->

**System capability:** SystemCapability.Location.Location.Geofence

## latitude

```TypeScript
latitude: number
```

Latitude of the center point of the circular fence.

**Type:** number

**Since:** 9

<!--Device-Geofence-latitude: double--><!--Device-Geofence-latitude: double-End-->

**System capability:** SystemCapability.Location.Location.Geofence

## longitude

```TypeScript
longitude: number
```

Longitude of the center point of the circular fence.

**Type:** number

**Since:** 9

<!--Device-Geofence-longitude: double--><!--Device-Geofence-longitude: double-End-->

**System capability:** SystemCapability.Location.Location.Geofence

## radius

```TypeScript
radius: number
```

Radius of the circular fence.

**Type:** number

**Since:** 9

<!--Device-Geofence-radius: double--><!--Device-Geofence-radius: double-End-->

**System capability:** SystemCapability.Location.Location.Geofence
