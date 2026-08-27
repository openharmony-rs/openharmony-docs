# GeofenceRequest

请求添加GNSS围栏消息中携带的参数，包括定位场景和围栏信息。@interface GeofenceRequest

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [GeofenceRequest](arkts-location-geolocationmanager-geofencerequest-i.md)

**需要权限：** ohos.permission.LOCATION

**系统能力：** SystemCapability.Location.Location.Geofence

## 导入模块

```TypeScript
import { geolocation } from '@kit.LocationKit';
```

## geofence

```TypeScript
geofence: Geofence
```

用于接收地理围栏事件上报（进出围栏）。

**类型：** Geofence

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [geofence](arkts-location-geolocationmanager-geofencerequest-i.md#geofence)

**系统能力：** SystemCapability.Location.Location.Geofence

## priority

```TypeScript
priority: LocationRequestPriority
```

设置事件类型。type为“fenceStatusChange”，表示订阅围栏事件上报。

**类型：** LocationRequestPriority

**起始版本：** 8

**废弃版本：** 9

**替代接口：** priority

**系统能力：** SystemCapability.Location.Location.Geofence

## scenario

```TypeScript
scenario: LocationRequestScenario
```

围栏的配置参数。

**类型：** LocationRequestScenario

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [scenario](arkts-location-geolocationmanager-geofencerequest-i.md#scenario)

**系统能力：** SystemCapability.Location.Location.Geofence
