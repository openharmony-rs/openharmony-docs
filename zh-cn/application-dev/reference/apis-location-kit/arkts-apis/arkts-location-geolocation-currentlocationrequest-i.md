# CurrentLocationRequest

当前位置信息请求参数。@interface CurrentLocationRequest

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [CurrentLocationRequest](arkts-location-geolocationmanager-currentlocationrequest-i.md)

**需要权限：** ohos.permission.LOCATION

**系统能力：** SystemCapability.Location.Location.Core

## 导入模块

```TypeScript
import { geolocation } from '@kit.LocationKit';
```

## maxAccuracy

```TypeScript
maxAccuracy?: number
```

表示精度信息，单位是米。 仅在精确位置功能场景（同时授予了ohos.permission.APPROXIMATELY_LOCATION和ohos.permission.LOCATION 权限）下有效， 模糊位置功能生效场景（仅授予了ohos.permission.APPROXIMATELY_LOCATION 权限）下该字段无意义。默认值为0，取值范围为大于等于0。 当scenario为NAVIGATION/TRAJECTORY_TRACKING/CAR_HAILING或者priority为ACCURACY时建议设置maxAccuracy为大于10的值。 当scenario为DAILY_LIFE_SERVICE/NO_POWER或者priority为LOW_POWER/FIRST_FIX时建议设置maxAccuracy为大于100的值。

**类型：** number

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [maxAccuracy](arkts-location-geolocationmanager-currentlocationrequest-i.md#maxaccuracy)

**系统能力：** SystemCapability.Location.Location.Core

## priority

```TypeScript
priority?: LocationRequestPriority
```

表示优先级信息。取值范围见[LocationRequestPriority](arkts-location-geolocation-locationrequestpriority-e.md)的定义。

**类型：** LocationRequestPriority

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [priority](arkts-location-geolocationmanager-currentlocationrequest-i.md#priority)

**系统能力：** SystemCapability.Location.Location.Core

## scenario

```TypeScript
scenario?: LocationRequestScenario
```

表示场景信息。取值范围见[LocationRequestScenario](arkts-location-geolocation-locationrequestscenario-e.md)的定义。

**类型：** LocationRequestScenario

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [scenario](arkts-location-geolocationmanager-currentlocationrequest-i.md#scenario)

**系统能力：** SystemCapability.Location.Location.Core

## timeoutMs

```TypeScript
timeoutMs?: number
```

表示超时时间，单位是毫秒，最小为1000毫秒。取值范围为大于等于1000。

**类型：** number

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [timeoutMs](arkts-location-geolocationmanager-currentlocationrequest-i.md#timeoutms)

**系统能力：** SystemCapability.Location.Location.Core
