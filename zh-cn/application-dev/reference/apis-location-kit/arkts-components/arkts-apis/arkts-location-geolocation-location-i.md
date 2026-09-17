# Location

位置信息。

@interface Location

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [Location](arkts-location-geolocationmanager-location-i.md)

**需要权限：** ohos.permission.LOCATION

**系统能力：** SystemCapability.Location.Location.Core

## 导入模块

```TypeScript
import { geolocation } from '@kit.LocationKit';
```

## accuracy

```TypeScript
accuracy: number
```

表示精度信息，单位米。

**类型：** number

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [accuracy](arkts-location-geolocationmanager-location-i.md#accuracy)

**需要权限：** ohos.permission.LOCATION

**系统能力：** SystemCapability.Location.Location.Core

## additions

```TypeScript
additions?: Array<string>
```

附加信息。

**类型：** Array&lt;string&gt;

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [additions](arkts-location-geolocationmanager-location-i.md#additions)

**需要权限：** ohos.permission.LOCATION

**系统能力：** SystemCapability.Location.Location.Core

## additionSize

```TypeScript
additionSize?: number
```

附加信息数量。取值范围为大于等于0。

**类型：** number

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [additionSize](arkts-location-geolocationmanager-location-i.md#additionsize)

**需要权限：** ohos.permission.LOCATION

**系统能力：** SystemCapability.Location.Location.Core

## altitude

```TypeScript
altitude: number
```

表示高度信息，单位米。

**类型：** number

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [altitude](arkts-location-geolocationmanager-location-i.md#altitude)

**需要权限：** ohos.permission.LOCATION

**系统能力：** SystemCapability.Location.Location.Core

## direction

```TypeScript
direction: number
```

表示航向信息。单位是“度”，取值范围为0到360。

**类型：** number

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [direction](arkts-location-geolocationmanager-location-i.md#direction)

**需要权限：** ohos.permission.LOCATION

**系统能力：** SystemCapability.Location.Location.Core

## latitude

```TypeScript
latitude: number
```

表示纬度信息，正值表示北纬，负值表示南纬。取值范围为-90到90。

**类型：** number

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [latitude](arkts-location-geolocationmanager-location-i.md#latitude)

**需要权限：** ohos.permission.LOCATION

**系统能力：** SystemCapability.Location.Location.Core

## longitude

```TypeScript
longitude: number
```

表示经度信息，正值表示东经，负值表是西经。取值范围为-180到180。

**类型：** number

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [longitude](arkts-location-geolocationmanager-location-i.md#longitude)

**需要权限：** ohos.permission.LOCATION

**系统能力：** SystemCapability.Location.Location.Core

## speed

```TypeScript
speed: number
```

表示速度信息，单位米每秒。

**类型：** number

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [speed](arkts-location-geolocationmanager-location-i.md#speed)

**需要权限：** ohos.permission.LOCATION

**系统能力：** SystemCapability.Location.Location.Core

## timeSinceBoot

```TypeScript
timeSinceBoot: number
```

表示位置时间戳，开机时间格式。

**类型：** number

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [timeSinceBoot](arkts-location-geolocationmanager-location-i.md#timesinceboot)

**需要权限：** ohos.permission.LOCATION

**系统能力：** SystemCapability.Location.Location.Core

## timeStamp

```TypeScript
timeStamp: number
```

表示位置时间戳，UTC格式。

**类型：** number

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [timeStamp](arkts-location-geolocationmanager-location-i.md#timestamp)

**需要权限：** ohos.permission.LOCATION

**系统能力：** SystemCapability.Location.Location.Core
