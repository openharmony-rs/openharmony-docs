# Geofence

```TypeScript
export interface Geofence
```

GNSS围栏的配置参数。目前只支持圆形围栏。

**起始版本：** 9

<!--Device-geoLocationManager-export interface Geofence--><!--Device-geoLocationManager-export interface Geofence-End-->

**系统能力：** SystemCapability.Location.Location.Geofence

## 导入模块

```TypeScript
import { geoLocationManager } from '@kit.LocationKit';
```

## coordinateSystemType

```TypeScript
coordinateSystemType?: CoordinateSystemType
```

表示地理围栏圆心坐标的坐标系。

APP应先使用[getGeofenceSupportedCoordTypes](arkts-location-geolocationmanager-getgeofencesupportedcoordtypes-f.md)查询支持的坐标系，然后传入正确的圆心坐标。

**类型：** [CoordinateSystemType](arkts-location-geolocationmanager-coordinatesystemtype-e.md)

**起始版本：** 12

<!--Device-Geofence-coordinateSystemType?: CoordinateSystemType--><!--Device-Geofence-coordinateSystemType?: CoordinateSystemType-End-->

**系统能力：** SystemCapability.Location.Location.Geofence

## expiration

```TypeScript
expiration: number
```

围栏存活的时间，单位是毫秒。取值范围为大于0。

**类型：** number

**起始版本：** 9

<!--Device-Geofence-expiration: double--><!--Device-Geofence-expiration: double-End-->

**系统能力：** SystemCapability.Location.Location.Geofence

## latitude

```TypeScript
latitude: number
```

表示纬度。取值范围为-90到90。

**类型：** number

**起始版本：** 9

<!--Device-Geofence-latitude: double--><!--Device-Geofence-latitude: double-End-->

**系统能力：** SystemCapability.Location.Location.Geofence

## longitude

```TypeScript
longitude: number
```

表示经度。取值范围为-180到180。

**类型：** number

**起始版本：** 9

<!--Device-Geofence-longitude: double--><!--Device-Geofence-longitude: double-End-->

**系统能力：** SystemCapability.Location.Location.Geofence

## radius

```TypeScript
radius: number
```

表示圆形围栏的半径。单位是米，取值范围为大于0。

**类型：** number

**起始版本：** 9

<!--Device-Geofence-radius: double--><!--Device-Geofence-radius: double-End-->

**系统能力：** SystemCapability.Location.Location.Geofence
