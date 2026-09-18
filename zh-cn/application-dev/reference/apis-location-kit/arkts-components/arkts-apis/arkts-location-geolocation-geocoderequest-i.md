# GeoCodeRequest

地理编码请求参数。

@interface GeoCodeRequest

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [GeoCodeRequest](arkts-location-geolocationmanager-geocoderequest-i.md)

**需要权限：** ohos.permission.LOCATION

**系统能力：** SystemCapability.Location.Location.Geocoder

## 导入模块

```TypeScript
import { geolocation } from '@kit.LocationKit';
```

## description

```TypeScript
description: string
```

表示位置信息描述，如“上海市浦东新区xx路xx号”。

**类型：** string

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [description](arkts-location-geolocationmanager-geocoderequest-i.md#description)

**系统能力：** SystemCapability.Location.Location.Geocoder

## locale

```TypeScript
locale?: string
```

表示位置描述信息的语言，“zh”代表中文，“en”代表英文。

**类型：** string

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [locale](arkts-location-geolocationmanager-geocoderequest-i.md#locale)

**系统能力：** SystemCapability.Location.Location.Geocoder

## maxItems

```TypeScript
maxItems?: number
```

表示返回位置信息的最大个数。取值范围为大于等于0，推荐该值小于10。

**类型：** number

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [maxItems](arkts-location-geolocationmanager-geocoderequest-i.md#maxitems)

**系统能力：** SystemCapability.Location.Location.Geocoder

## maxLatitude

```TypeScript
maxLatitude?: number
```

表示最大纬度信息。取值范围为-90到90。

**类型：** number

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [maxLatitude](arkts-location-geolocationmanager-geocoderequest-i.md#maxlatitude)

**系统能力：** SystemCapability.Location.Location.Geocoder

## maxLongitude

```TypeScript
maxLongitude?: number
```

表示最大经度信息。取值范围为-180到180。

**类型：** number

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [maxLongitude](arkts-location-geolocationmanager-geocoderequest-i.md#maxlongitude)

**系统能力：** SystemCapability.Location.Location.Geocoder

## minLatitude

```TypeScript
minLatitude?: number
```

表示最小纬度信息，与下面三个参数一起，表示一个经纬度范围。取值范围为-90到90。

**类型：** number

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [minLatitude](arkts-location-geolocationmanager-geocoderequest-i.md#minlatitude)

**系统能力：** SystemCapability.Location.Location.Geocoder

## minLongitude

```TypeScript
minLongitude?: number
```

表示最小经度信息。取值范围为-180到180。

**类型：** number

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [minLongitude](arkts-location-geolocationmanager-geocoderequest-i.md#minlongitude)

**系统能力：** SystemCapability.Location.Location.Geocoder
