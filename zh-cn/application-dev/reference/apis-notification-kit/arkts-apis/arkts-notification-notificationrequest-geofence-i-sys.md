# Geofence（系统接口）

地理围栏的配置信息。

**起始版本：** 23

<!--Device-unnamed-export interface Geofence--><!--Device-unnamed-export interface Geofence-End-->

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

## coordinateSystemType

```TypeScript
coordinateSystemType:CoordinateSystemType
```

中心点坐标系类型。

**类型：** CoordinateSystemType

**起始版本：** 23

<!--Device-Geofence-coordinateSystemType:CoordinateSystemType--><!--Device-Geofence-coordinateSystemType:CoordinateSystemType-End-->

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

## delayTime

```TypeScript
delayTime?:number
```

围栏延迟时间，单位：秒，进入围栏后触发围栏的延迟时间，取值范围：[0, 300]。默认值为0。

**类型：** number

**起始版本：** 23

<!--Device-Geofence-delayTime?:int--><!--Device-Geofence-delayTime?:int-End-->

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

## latitude

```TypeScript
latitude:number
```

地理围栏中心点纬度，取值范围：[-90, 90]。

**类型：** number

**起始版本：** 23

<!--Device-Geofence-latitude:double--><!--Device-Geofence-latitude:double-End-->

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

## longitude

```TypeScript
longitude:number
```

地理围栏中心点经度，取值范围：[-180, 180]。

**类型：** number

**起始版本：** 23

<!--Device-Geofence-longitude:double--><!--Device-Geofence-longitude:double-End-->

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

## monitorEvent

```TypeScript
monitorEvent:MonitorEvent
```

围栏触发条件类型。

**类型：** MonitorEvent

**起始版本：** 23

<!--Device-Geofence-monitorEvent:MonitorEvent--><!--Device-Geofence-monitorEvent:MonitorEvent-End-->

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

## radius

```TypeScript
radius:number
```

围栏半径，单位：米，取值范围：[200, 2000]。

**类型：** number

**起始版本：** 23

<!--Device-Geofence-radius:double--><!--Device-Geofence-radius:double-End-->

**系统能力：** SystemCapability.Notification.Notification

**系统接口：** 此接口为系统接口。

