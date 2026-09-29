# Geofence (System API)

```TypeScript
export interface Geofence
```

Defines the configuration of a geofence.

**Since:** 23

<!--Device-unnamed-export interface Geofence--><!--Device-unnamed-export interface Geofence-End-->

**System capability:** SystemCapability.Notification.Notification

**System API:** This is a system API.

## coordinateSystemType

```TypeScript
coordinateSystemType:CoordinateSystemType
```

Coordinate system type of the center point.

**Type:** [CoordinateSystemType](arkts-notification-notificationrequest-coordinatesystemtype-e-sys.md)

**Since:** 23

<!--Device-Geofence-coordinateSystemType:CoordinateSystemType--><!--Device-Geofence-coordinateSystemType:CoordinateSystemType-End-->

**System capability:** SystemCapability.Notification.Notification

**System API:** This is a system API.

## delayTime

```TypeScript
delayTime?:number
```

Delay time of the geofence, in seconds. That is, the delay time before the geofence is triggered after entering the geofence. Value range: [0, 300]. Default value: **0**.

**Type:** number

**Since:** 23

<!--Device-Geofence-delayTime?:int--><!--Device-Geofence-delayTime?:int-End-->

**System capability:** SystemCapability.Notification.Notification

**System API:** This is a system API.

## latitude

```TypeScript
latitude:number
```

Latitude of the geofence center. The value ranges from -90 to 90.

**Type:** number

**Since:** 23

<!--Device-Geofence-latitude:double--><!--Device-Geofence-latitude:double-End-->

**System capability:** SystemCapability.Notification.Notification

**System API:** This is a system API.

## longitude

```TypeScript
longitude:number
```

Longitude of the geofence center. The value ranges from -180 to 180.

**Type:** number

**Since:** 23

<!--Device-Geofence-longitude:double--><!--Device-Geofence-longitude:double-End-->

**System capability:** SystemCapability.Notification.Notification

**System API:** This is a system API.

## monitorEvent

```TypeScript
monitorEvent:MonitorEvent
```

Event type for monitoring a geofence.

**Type:** [MonitorEvent](arkts-notification-notificationrequest-monitorevent-e-sys.md)

**Since:** 23

<!--Device-Geofence-monitorEvent:MonitorEvent--><!--Device-Geofence-monitorEvent:MonitorEvent-End-->

**System capability:** SystemCapability.Notification.Notification

**System API:** This is a system API.

## radius

```TypeScript
radius:number
```

Radius of the geofence, in meters. Value range: [200, 2000].

**Type:** number

**Since:** 23

<!--Device-Geofence-radius:double--><!--Device-Geofence-radius:double-End-->

**System capability:** SystemCapability.Notification.Notification

**System API:** This is a system API.
