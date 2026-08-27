# Geofence

GNSS围栏的配置参数。目前只支持圆形围栏。

**起始版本：** 9

**系统能力：** SystemCapability.Location.Location.Geofence

## 导入模块

```TypeScript
```

## coordinateSystemType

```TypeScript
coordinateSystemType?: CoordinateSystemType
```

表示地理围栏圆心坐标的坐标系。APP应先使用[getGeofenceSupportedCoordTypes](arkts-location-geolocationmanager-getgeofencesupportedcoordtypes-f.md)查询支持的坐标系，然后传入正确的圆 心坐标。

**类型：** CoordinateSystemType

**起始版本：** 12

**系统能力：** SystemCapability.Location.Location.Geofence

## expiration

```TypeScript
expiration: number
```

围栏存活的时间，单位是毫秒。取值范围为大于0。

**类型：** number

**起始版本：** 9

**系统能力：** SystemCapability.Location.Location.Geofence

## latitude

```TypeScript
latitude: number
```

表示纬度。取值范围为-90到90。

**类型：** number

**起始版本：** 9

**系统能力：** SystemCapability.Location.Location.Geofence

## longitude

```TypeScript
longitude: number
```

表示经度。取值范围为-180到180。

**类型：** number

**起始版本：** 9

**系统能力：** SystemCapability.Location.Location.Geofence

## radius

```TypeScript
radius: number
```

表示圆形围栏的半径。单位是米，取值范围为大于0。

**类型：** number

**起始版本：** 9

**系统能力：** SystemCapability.Location.Location.Geofence
