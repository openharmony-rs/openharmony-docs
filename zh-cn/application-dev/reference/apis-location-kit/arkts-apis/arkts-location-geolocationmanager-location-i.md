# Location

位置信息。

**起始版本：** 9

**系统能力：** SystemCapability.Location.Location.Core

## 导入模块

```TypeScript
```

## accuracy

```TypeScript
accuracy: number
```

表示精度信息，单位米。

**类型：** number

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Location.Location.Core

## additions

```TypeScript
additions?: Array<string>
```

附加信息。

**类型：** Array&lt;string&gt;

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Location.Location.Core

## additionSize

```TypeScript
additionSize?: number
```

附加信息数量。取值范围为大于等于0。

**类型：** number

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Location.Location.Core

## additionsMap

```TypeScript
additionsMap?: Map<string, string>
```

附加信息。具体内容和顺序与additions一致。

**类型：** Map&lt;string, string&gt;

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Location.Location.Core

## altitude

```TypeScript
altitude: number
```

表示高度信息，单位米。

**类型：** number

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Location.Location.Core

## altitudeAccuracy

```TypeScript
altitudeAccuracy?: number
```

表示高度信息的精度，单位米。

**类型：** number

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Location.Location.Core

## direction

```TypeScript
direction: number
```

表示航向信息。单位是“度”，取值范围为0到360。

**类型：** number

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Location.Location.Core

## directionAccuracy

```TypeScript
directionAccuracy?: number
```

表示航向信息的精度。单位是“度”，取值范围为0到360。

**类型：** number

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Location.Location.Core

## isFromMock

```TypeScript
isFromMock?: boolean
```

true：位置信息来自于位置模拟功能。false：位置信息不是来自于位置模拟功能。

**类型：** boolean

**起始版本：** 26.0.0

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Location.Location.Core

## latitude

```TypeScript
latitude: number
```

表示纬度信息，正值表示北纬，负值表示南纬。取值范围为-90到90。仅支持WGS84坐标系。

**类型：** number

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Location.Location.Core

## longitude

```TypeScript
longitude: number
```

表示经度信息，正值表示东经，负值表示西经。取值范围为-180到180。仅支持WGS84坐标系。

**类型：** number

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Location.Location.Core

## poi

```TypeScript
poi?: PoiInfo
```

表示当前位置附近的POI信息。

**类型：** [PoiInfo](arkts-location-geolocationmanager-poiinfo-i.md)

**起始版本：** 19

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Location.Location.Core

## sourceType

```TypeScript
sourceType?: LocationSourceType
```

表示定位结果的来源。

**类型：** [LocationSourceType](arkts-location-geolocationmanager-locationsourcetype-e.md)

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Location.Location.Core

## speed

```TypeScript
speed: number
```

表示速度信息，单位米每秒。

**类型：** number

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Location.Location.Core

## speedAccuracy

```TypeScript
speedAccuracy?: number
```

表示速度信息的精度，单位米每秒。

**类型：** number

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Location.Location.Core

## timeSinceBoot

```TypeScript
timeSinceBoot: number
```

表示获取位置成功的时间戳，值表示从本次开机到获取位置成功所经过的时间，单位为纳秒。

**类型：** number

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Location.Location.Core

## timeStamp

```TypeScript
timeStamp: number
```

表示位置时间戳，UTC格式，单位毫秒。

**类型：** number

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Location.Location.Core

## uncertaintyOfTimeSinceBoot

```TypeScript
uncertaintyOfTimeSinceBoot?: number
```

表示位置时间戳的不确定度。

**类型：** number

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Location.Location.Core
