# LocationRequest

位置信息请求参数。

**起始版本：** 9

**系统能力：** SystemCapability.Location.Location.Core

## 导入模块

```TypeScript
```

## distanceInterval

```TypeScript
distanceInterval?: number
```

表示上报位置信息的距离间隔。单位是米，默认值为0，取值范围为大于等于0。等于0时对位置上报距离间隔无限制。

**类型：** number

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Location.Location.Core

## maxAccuracy

```TypeScript
maxAccuracy?: number
```

应用向系统请求位置信息时要求的精度值，单位为米。该参数仅在精确位置功能场景（即同时授权了ohos.permission.APPROXIMATELY_LOCATION和ohos.permission.LOCATION 权限）下有 效，模糊位置功能生效场景（即仅授权了ohos.permission.APPROXIMATELY_LOCATION 权限）下该字段无意义。该参数生效的情况下，系统会对比GNSS或网络定位服务上报的位置信息与应用的位置信息申请。当位置信息[Location](arkts-location-geolocationmanager-location-i.md)中的精度值（accuracy）小于等于 应用要求的精度值（maxAccuracy）时，位置信息会返回给应用；否则系统将丢弃本次收到的位置信息。默认值为0，表示不限制位置信息的精度，取值范围为大于等于0。当scenario为NAVIGATION/TRAJECTORY_TRACKING/CAR_HAILING或者priority为ACCURACY时建议设置maxAccuracy为大于10的值。当scenario为DAILY_LIFE_SERVICE/NO_POWER或者priority为LOW_POWER/FIRST_FIX时建议设置maxAccuracy为大于100的值。

**类型：** number

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Location.Location.Core

## priority

```TypeScript
priority?: LocationRequestPriority
```

表示优先级信息。当scenario取值为UNSET时，priority参数生效，否则priority参数不生效；当scenario和priority均取值为UNSET时，无法发起定位请求。取值范围见 [LocationRequestPriority](arkts-location-geolocationmanager-locationrequestpriority-e.md)的定义。默认值为FIRST_FIX。

**类型：** LocationRequestPriority

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Location.Location.Core

## scenario

```TypeScript
scenario?: LocationRequestScenario
```

表示场景信息。当scenario取值为UNSET时，priority参数生效，否则priority参数不生效；当scenario和priority均取值为UNSET时，无法发起定位请求。取值范围见 [LocationRequestScenario](arkts-location-geolocationmanager-locationrequestscenario-e.md)的定义。默认值为UNSET。

**类型：** LocationRequestScenario

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Location.Location.Core

## timeInterval

```TypeScript
timeInterval?: number
```

表示上报位置信息的时间间隔，单位为秒。取值范围为大于等于0的值。默认值为对应定位模式下允许的最小时间间隔：默认值在GNSS定位时为1秒，网络定位时为20秒。当设置值小于最小间隔时，以最小时间间隔生效。设置为0时不对时间间隔进行校验，直接上报位置信息。

**类型：** number

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Location.Location.Core
