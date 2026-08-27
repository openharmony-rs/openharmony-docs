# ContinuousLocationRequest

持续定位的请求参数。

**起始版本：** 12

**系统能力：** SystemCapability.Location.Location.Core

## 导入模块

```TypeScript
```

## interval

```TypeScript
interval: number
```

表示上报位置信息的时间间隔，单位是秒。默认值为1，取值范围为大于等于0。等于0时对位置上报时间间隔无限制。

**类型：** number

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Location.Location.Core

## locationScenario

```TypeScript
locationScenario: UserActivityScenario | PowerConsumptionScenario
```

表示定位的场景信息。取值范围见[UserActivityScenario](arkts-location-geolocationmanager-useractivityscenario-e.md)和 [PowerConsumptionScenario](arkts-location-geolocationmanager-powerconsumptionscenario-e.md)的定义。

**类型：** [UserActivityScenario](arkts-location-geolocationmanager-useractivityscenario-e.md) \| [PowerConsumptionScenario](arkts-location-geolocationmanager-powerconsumptionscenario-e.md)

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Location.Location.Core

## needPoi

```TypeScript
needPoi?: boolean
```

表示是否需要获取当前位置附近的POI信息。false代表不需要获取当前位置附近的POI信息，true代表需要获取当前位置附近的POI信息。不设置时，默认值为false。该参数仅在精确位置功能场景（即同时授权了ohos.permission.APPROXIMATELY_LOCATION和ohos.permission.LOCATION 权限）下有效，模糊位置功能生效场景（即仅授权了 ohos.permission.APPROXIMATELY_LOCATION 权限）下不返回POI信息。

**类型：** boolean

**起始版本：** 19

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Location.Location.Core

## sportsType

```TypeScript
sportsType?: SportsType
```

表示运动模式。取值范围见[SportsType](arkts-location-geolocationmanager-sportstype-e.md)定义。此参数仅在locationScenario设置为 UserActivityScenario.SPORT时有效。默认值为0，表示该参数不生效。

**类型：** [SportsType](arkts-location-geolocationmanager-sportstype-e.md)

**起始版本：** 26.0.0

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Location.Location.Core
