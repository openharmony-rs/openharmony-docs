# SingleLocationRequest

单次定位的请求参数。

**起始版本：** 12

**系统能力：** SystemCapability.Location.Location.Core

## 导入模块

```TypeScript
```

## locatingPriority

```TypeScript
locatingPriority: LocatingPriority
```

表示优先级信息。取值范围见[LocatingPriority](arkts-location-geolocationmanager-locatingpriority-e.md)的定义。

**类型：** [LocatingPriority](arkts-location-geolocationmanager-locatingpriority-e.md)

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Location.Location.Core

## locatingTimeoutMs

```TypeScript
locatingTimeoutMs: number
```

表示超时时间，单位是毫秒，最小为1000毫秒。取值范围为大于等于1000。

**类型：** number

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
