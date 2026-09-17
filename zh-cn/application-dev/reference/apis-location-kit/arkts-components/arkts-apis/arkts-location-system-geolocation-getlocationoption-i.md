# GetLocationOption

单次定位请求的配置参数。

**起始版本：** 3

**废弃版本：** 9

**替代接口：** [CurrentLocationRequest](arkts-location-geolocationmanager-currentlocationrequest-i.md)

**需要权限：** ohos.permission.LOCATION

**系统能力：** SystemCapability.Location.Location.Lite

## 导入模块

```TypeScript
import { Geolocation, GeolocationResponse, GetLocationOption, GetLocationTypeOption, GetLocationTypeResponse, SubscribeLocationOption } from '@kit.LocationKit';
```

## complete

```TypeScript
complete?: () => void
```

接口调用结束的回调函数。

**起始版本：** 3

**废弃版本：** 9

**替代接口：** callback

**模型约束：** 此接口仅可在FA模型下使用。

**系统能力：** SystemCapability.Location.Location.Lite

## fail

```TypeScript
fail?: (data: string, code: number) => void
```

接口调用失败的回调函数。data为错误信息，code为错误码。

**起始版本：** 3

**废弃版本：** 9

**替代接口：** callback

**模型约束：** 此接口仅可在FA模型下使用。

**系统能力：** SystemCapability.Location.Location.Lite

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| data | string | 是 |  |
| code | number | 是 |  |

## success

```TypeScript
success?: (data: GeolocationResponse) => void
```

接口调用成功的回调函数。

**起始版本：** 3

**废弃版本：** 9

**替代接口：** callback

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

坐标系的类型，可通过getSupportedCoordTypes获取可选值，缺省值为wgs84。

**类型：** string

**起始版本：** 3

**废弃版本：** 9

**模型约束：** 此接口仅可在FA模型下使用。

**系统能力：** SystemCapability.Location.Location.Lite

## timeout

```TypeScript
timeout?: number
```

超时时间，单位为ms，默认值为30000。设置超时，是为了防止出现权限被系统拒绝、定位信号弱或者定位设置不当，导致请求阻塞的情况。超时后会使用fail回调函数。取值范围为32位正整数。如果设置值小于等于0，系统按默认值处理。

**类型：** number

**起始版本：** 3

**废弃版本：** 9

**替代接口：** [timeoutMs](arkts-location-geolocationmanager-currentlocationrequest-i.md#timeoutms)

**模型约束：** 此接口仅可在FA模型下使用。

**系统能力：** SystemCapability.Location.Location.Lite
