# FusionFenceRequestParams（系统接口）

融合围栏请求信息。

**起始版本：** 26.0.0

**系统能力：** SystemCapability.Location.Location.Geofence

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
```

## cellFences

```TypeScript
cellFences?: Array<CellFence>
```

表示CELL围栏信息集合。

**类型：** Array&lt;[CellFence](arkts-location-geolocationmanager-cellfence-i-sys.md)&gt;

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Location.Location.Geofence

**系统接口：** 此接口为系统接口。

## expirationMs

```TypeScript
expirationMs: number
```

表示围栏存活时间，单位是毫秒。取值范围为大于0。

**类型：** number

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Location.Location.Geofence

**系统接口：** 此接口为系统接口。

## fenceTransitionCallback

```TypeScript
fenceTransitionCallback: Callback<FusionFenceTransition>
```

表示用于接收围栏事件的回调函数。

**类型：** [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[FusionFenceTransition](arkts-location-geolocationmanager-fusionfencetransition-i-sys.md)&gt;

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Location.Location.Geofence

**系统接口：** 此接口为系统接口。

## fenceType

```TypeScript
fenceType: number
```

表示融合围栏类型。

**类型：** number

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Location.Location.Geofence

**系统接口：** 此接口为系统接口。

## gnssFences

```TypeScript
gnssFences?: Array<GnssFence>
```

表示GNSS围栏信息集合

**类型：** Array&lt;[GnssFence](arkts-location-geolocationmanager-gnssfence-i-sys.md)&gt;

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Location.Location.Geofence

**系统接口：** 此接口为系统接口。

## identifier

```TypeScript
identifier: string
```

表示融合围栏唯一标识。

**类型：** string

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Location.Location.Geofence

**系统接口：** 此接口为系统接口。

## loiterTimeMs

```TypeScript
loiterTimeMs: number
```

表示徘徊时间，单位为毫秒。取值范围为大于0。若监听徘徊事件，当设备在围栏内徘徊时间达到该值，则上报徘徊事件。

**类型：** number

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Location.Location.Geofence

**系统接口：** 此接口为系统接口。

## monitorTransitionEvents

```TypeScript
monitorTransitionEvents: number
```

表示监听的围栏事件。

**类型：** number

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Location.Location.Geofence

**系统接口：** 此接口为系统接口。

## poiLocation

```TypeScript
poiLocation: Point
```

表示POI位置信息。

**类型：** Point

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Location.Location.Geofence

**系统接口：** 此接口为系统接口。

## poiType

```TypeScript
poiType?: string
```

表示POI类型。

**类型：** string

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Location.Location.Geofence

**系统接口：** 此接口为系统接口。

## scene

```TypeScript
scene: FusionFenceScene
```

表示融合围栏场景。

**类型：** [FusionFenceScene](arkts-location-geolocationmanager-fusionfencescene-e-sys.md)

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Location.Location.Geofence

**系统接口：** 此接口为系统接口。

## wifiFences

```TypeScript
wifiFences?: Array<WifiFence>
```

表示Wi-Fi围栏信息集合。

**类型：** Array&lt;[WifiFence](arkts-location-geolocationmanager-wififence-i-sys.md)&gt;

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Location.Location.Geofence

**系统接口：** 此接口为系统接口。
