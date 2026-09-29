# CachedGnssLocationsRequest

```TypeScript
export interface CachedGnssLocationsRequest
```

请求订阅GNSS缓存位置上报功能接口的配置参数。

@interface CachedGnssLocationsRequest

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [CachedGnssLocationsRequest](arkts-location-geolocationmanager-cachedgnsslocationsrequest-i.md)

**需要权限：** ohos.permission.LOCATION

<!--Device-geolocation-export interface CachedGnssLocationsRequest--><!--Device-geolocation-export interface CachedGnssLocationsRequest-End-->

**系统能力：** SystemCapability.Location.Location.Gnss

## 导入模块

```TypeScript
import { geolocation } from '@kit.LocationKit';
```

## reportingPeriodSec

```TypeScript
reportingPeriodSec: number
```

表示GNSS缓存位置上报的周期，单位是毫秒。取值范围为大于0。

**类型：** number

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [reportingPeriodSec](arkts-location-geolocationmanager-cachedgnsslocationsrequest-i.md#reportingperiodsec)

<!--Device-CachedGnssLocationsRequest-reportingPeriodSec: number--><!--Device-CachedGnssLocationsRequest-reportingPeriodSec: number-End-->

**系统能力：** SystemCapability.Location.Location.Gnss

## wakeUpCacheQueueFull

```TypeScript
wakeUpCacheQueueFull: boolean
```

GNSS芯片底层缓存队列满之后是否主动唤醒AP芯片。true表示GNSS芯片底层缓存队列满之后会主动唤醒AP芯片，并把缓存位置上报给应用。false表示GNSS芯片底层缓存队列满之后不会主动唤醒AP芯片，会把缓存位置直接丢弃。

**类型：** boolean

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [wakeUpCacheQueueFull](arkts-location-geolocationmanager-cachedgnsslocationsrequest-i.md#wakeupcachequeuefull)

<!--Device-CachedGnssLocationsRequest-wakeUpCacheQueueFull: boolean--><!--Device-CachedGnssLocationsRequest-wakeUpCacheQueueFull: boolean-End-->

**系统能力：** SystemCapability.Location.Location.Gnss
