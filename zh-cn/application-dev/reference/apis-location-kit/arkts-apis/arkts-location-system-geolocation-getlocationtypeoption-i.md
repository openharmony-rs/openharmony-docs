# GetLocationTypeOption

查询定位类型接口的入参，用于存放回调函数，在查询成功或者失败时接收查询结果。

**起始版本：** 3

**废弃版本：** 9

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

**模型约束：** 此接口仅可在FA模型下使用。

**系统能力：** SystemCapability.Location.Location.Lite

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
success?: (data: GetLocationTypeResponse) => void
```

接口调用成功的回调函数。

**起始版本：** 3

**废弃版本：** 9

**模型约束：** 此接口仅可在FA模型下使用。

**系统能力：** SystemCapability.Location.Location.Lite

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| data | [GetLocationTypeResponse](arkts-location-system-geolocation-getlocationtyperesponse-i.md) | 是 |  |
