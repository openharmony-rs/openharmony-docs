# GnssFence (System API)

```TypeScript
export interface GnssFence
```

Indicates GNSS fence information.

**Since:** 26.0.0

<!--Device-geoLocationManager-export interface GnssFence--><!--Device-geoLocationManager-export interface GnssFence-End-->

**System capability:** SystemCapability.Location.Location.Geofence

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { geoLocationManager } from '@kit.LocationKit';
```

## circularFence

```TypeScript
circularFence?: Geofence
```

Indicates circular fence.

**Type:** [Geofence](arkts-location-geolocationmanager-geofence-i.md)

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-GnssFence-circularFence?: Geofence--><!--Device-GnssFence-circularFence?: Geofence-End-->

**System capability:** SystemCapability.Location.Location.Geofence

**System API:** This is a system API.

## gnssFenceType

```TypeScript
gnssFenceType: number
```

Indicates GNSS fence type. The value range of this field is as follows: [GnssFenceType](arkts-location-geolocationmanager-gnssfencetype-e-sys.md). The value range is all integers.

**Type:** number

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-GnssFence-gnssFenceType: int--><!--Device-GnssFence-gnssFenceType: int-End-->

**System capability:** SystemCapability.Location.Location.Geofence

**System API:** This is a system API.

## polygon

```TypeScript
polygon?: Array<Point>
```

Indicates polygonal fence.

**Type:** Array&lt;[Point](arkts-location-geolocationmanager-point-i.md)&gt;

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-GnssFence-polygon?: Array<Point>--><!--Device-GnssFence-polygon?: Array<Point>-End-->

**System capability:** SystemCapability.Location.Location.Geofence

**System API:** This is a system API.
