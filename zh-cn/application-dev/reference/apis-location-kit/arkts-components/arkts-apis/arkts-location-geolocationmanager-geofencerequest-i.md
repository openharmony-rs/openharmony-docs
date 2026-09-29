# GeofenceRequest

```TypeScript
export interface GeofenceRequest
```

请求添加GNSS围栏消息中携带的参数，包括定位场景和围栏信息。

**起始版本：** 9

<!--Device-geoLocationManager-export interface GeofenceRequest--><!--Device-geoLocationManager-export interface GeofenceRequest-End-->

**系统能力：** SystemCapability.Location.Location.Geofence

## 导入模块

```TypeScript
import { geoLocationManager } from '@kit.LocationKit';
```

## geofence

```TypeScript
geofence: Geofence
```

表示围栏信息。

**类型：** [Geofence](arkts-location-geolocationmanager-geofence-i.md)

**起始版本：** 9

<!--Device-GeofenceRequest-geofence: Geofence--><!--Device-GeofenceRequest-geofence: Geofence-End-->

**系统能力：** SystemCapability.Location.Location.Geofence

## scenario

```TypeScript
scenario: LocationRequestScenario
```

表示定位场景。

**类型：** [LocationRequestScenario](arkts-location-geolocationmanager-locationrequestscenario-e.md)

**起始版本：** 9

<!--Device-GeofenceRequest-scenario: LocationRequestScenario--><!--Device-GeofenceRequest-scenario: LocationRequestScenario-End-->

**系统能力：** SystemCapability.Location.Location.Geofence
