# SubscribeLocationOption

持续定位请求的配置参数。

**起始版本：** 3

**废弃版本：** 9

**替代接口：** [LocationRequest](arkts-location-geolocationmanager-locationrequest-i.md)

**需要权限：** ohos.permission.LOCATION

**系统能力：** SystemCapability.Location.Location.Lite

## 导入模块

```TypeScript
import { Geolocation, GeolocationResponse, GetLocationOption, GetLocationTypeOption, GetLocationTypeResponse, SubscribeLocationOption } from '@kit.LocationKit';
```

## fail

```TypeScript
fail?: (data: string, code: number) => void
```

接口调用失败的回调函数。

**起始版本：** 3

**废弃版本：** 9

**模型约束：** 此接口仅可在FA模型下使用。

**系统能力：** SystemCapability.Location.Location.Lite

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| data | string | 是 |  |
| code | number | 是 |  |

## success

```TypeScript
success: (data: GeolocationResponse) => void
```

位置信息发生变化的回调函数。

**起始版本：** 3

**废弃版本：** 9

**模型约束：** 此接口仅可在FA模型下使用。

**系统能力：** SystemCapability.Location.Location.Lite

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| data | [GeolocationResponse](arkts-location-system-geolocation-geolocationresponse-i.md) | 是 |  |

## coordType

```TypeScript
coordType?: string
```

坐标系的类型，可通过getSupportedCoordTypes获取可选值，默认值为wgs84。

**类型：** string

**起始版本：** 3

**废弃版本：** 9

**模型约束：** 此接口仅可在FA模型下使用。

**系统能力：** SystemCapability.Location.Location.Lite
