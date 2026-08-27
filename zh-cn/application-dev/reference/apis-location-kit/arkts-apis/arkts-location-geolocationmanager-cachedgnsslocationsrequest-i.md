# CachedGnssLocationsRequest

请求订阅GNSS缓存位置上报功能接口的配置参数。

**起始版本：** 9

**系统能力：** SystemCapability.Location.Location.Gnss

## 导入模块

```TypeScript
```

## reportingPeriodSec

```TypeScript
reportingPeriodSec: number
```

表示GNSS缓存位置上报的周期，单位是毫秒。取值范围为大于0。

**类型：** number

**起始版本：** 9

**系统能力：** SystemCapability.Location.Location.Gnss

## wakeUpCacheQueueFull

```TypeScript
wakeUpCacheQueueFull: boolean
```

true表示GNSS芯片底层缓存队列满之后会主动唤醒AP芯片，并把缓存位置上报给应用。false表示GNSS芯片底层缓存队列满之后不会主动唤醒AP芯片，会把缓存位置直接丢弃。

**类型：** boolean

**起始版本：** 9

**系统能力：** SystemCapability.Location.Location.Gnss
