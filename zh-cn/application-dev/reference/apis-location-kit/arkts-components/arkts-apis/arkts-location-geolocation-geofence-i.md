# Geofence

```TypeScript
export interface Geofence
```

GNSS围栏的配置参数。目前只支持圆形围栏。

@interface Geofence

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [Geofence](arkts-location-geolocationmanager-geofence-i.md)

**需要权限：** ohos.permission.LOCATION

<!--Device-geolocation-export interface Geofence--><!--Device-geolocation-export interface Geofence-End-->

**系统能力：** SystemCapability.Location.Location.Geofence

## 导入模块

```TypeScript
import { geolocation } from '@kit.LocationKit';
```

## expiration

```TypeScript
expiration: number
```

围栏存活的时间，单位是毫秒。取值范围为大于0。

**类型：** number

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [expiration](arkts-location-geolocationmanager-geofence-i.md#expiration)

<!--Device-Geofence-expiration: number--><!--Device-Geofence-expiration: number-End-->

**系统能力：** SystemCapability.Location.Location.Geofence

## latitude

```TypeScript
latitude: number
```

表示纬度。取值范围为-90到90。

**类型：** number

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [latitude](arkts-location-geolocationmanager-geofence-i.md#latitude)

<!--Device-Geofence-latitude: number--><!--Device-Geofence-latitude: number-End-->

**系统能力：** SystemCapability.Location.Location.Geofence

## longitude

```TypeScript
longitude: number
```

表示经度。取值范围为-180到180。

**类型：** number

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [longitude](arkts-location-geolocationmanager-geofence-i.md#longitude)

<!--Device-Geofence-longitude: number--><!--Device-Geofence-longitude: number-End-->

**系统能力：** SystemCapability.Location.Location.Geofence

## radius

```TypeScript
radius: number
```

表示圆形围栏的半径。单位是米，取值范围为大于0。

**类型：** number

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [radius](arkts-location-geolocationmanager-geofence-i.md#radius)

<!--Device-Geofence-radius: number--><!--Device-Geofence-radius: number-End-->

**系统能力：** SystemCapability.Location.Location.Geofence
