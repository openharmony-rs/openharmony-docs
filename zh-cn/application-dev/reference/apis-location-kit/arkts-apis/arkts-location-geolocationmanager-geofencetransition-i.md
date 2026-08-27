# GeofenceTransition

地理围栏事件信息；包含地理围栏ID和具体的地理围栏事件。

**起始版本：** 12

**系统能力：** SystemCapability.Location.Location.Geofence

## 导入模块

```TypeScript
```

## beaconFence

```TypeScript
beaconFence?: BeaconFence
```

beacon围栏的参数配置。仅beacon围栏使用。从API version 20开始，支持该字段。

**类型：** [BeaconFence](arkts-location-geolocationmanager-beaconfence-i.md)

**起始版本：** 20

**系统能力：** SystemCapability.Location.Location.Geofence

## geofenceId

```TypeScript
geofenceId: number
```

表示地理围栏ID。

**类型：** number

**起始版本：** 12

**系统能力：** SystemCapability.Location.Location.Geofence

## transitionEvent

```TypeScript
transitionEvent: GeofenceTransitionEvent
```

表示当前发生的地理围栏事件。

**类型：** [GeofenceTransitionEvent](arkts-location-geolocationmanager-geofencetransitionevent-e.md)

**起始版本：** 12

**系统能力：** SystemCapability.Location.Location.Geofence
