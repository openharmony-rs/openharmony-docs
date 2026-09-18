# GeoCodeRequest

地理编码请求参数。

**起始版本：** 9

**系统能力：** SystemCapability.Location.Location.Geocoder

## 导入模块

```TypeScript
import { geoLocationManager } from '@kit.LocationKit';
```

## country

```TypeScript
country?: string
```

限制查询结果在指定的国家内，采用ISO 3166-1 alpha-2 。“CN”代表中国。默认值从设置中的“语言和地区”获取。

**类型：** string

**起始版本：** 12

**系统能力：** SystemCapability.Location.Location.Geocoder

## description

```TypeScript
description: string
```

表示位置信息描述，如“上海市浦东新区xx路xx号”，字符串长度不超过100。

**类型：** string

**起始版本：** 9

**系统能力：** SystemCapability.Location.Location.Geocoder

## locale

```TypeScript
locale?: string
```

表示位置描述信息的语言，“zh”代表中文，“en”代表英文。默认值从设置中的“语言和地区”获取。

**类型：** string

**起始版本：** 9

**系统能力：** SystemCapability.Location.Location.Geocoder

## maxItems

```TypeScript
maxItems?: number
```

表示返回位置信息的最大个数。取值范围为大于等于0，推荐该值小于10。默认值是1。

**类型：** number

**起始版本：** 9

**系统能力：** SystemCapability.Location.Location.Geocoder

## maxLatitude

```TypeScript
maxLatitude?: number
```

表示最大纬度信息。取值范围为-90到90。仅支持WGS84坐标系。默认值是0。

**类型：** number

**起始版本：** 9

**系统能力：** SystemCapability.Location.Location.Geocoder

## maxLongitude

```TypeScript
maxLongitude?: number
```

表示最大经度信息。取值范围为-180到180。仅支持WGS84坐标系。默认值是0。

**类型：** number

**起始版本：** 9

**系统能力：** SystemCapability.Location.Location.Geocoder

## minLatitude

```TypeScript
minLatitude?: number
```

表示最小纬度信息，与下面三个参数一起，表示一个经纬度范围。取值范围为-90到90。仅支持WGS84坐标系。默认值是0。如果该参数有值时，下面三个参数必填。

**类型：** number

**起始版本：** 9

**系统能力：** SystemCapability.Location.Location.Geocoder

## minLongitude

```TypeScript
minLongitude?: number
```

表示最小经度信息。取值范围为-180到180。仅支持WGS84坐标系。默认值是0。

**类型：** number

**起始版本：** 9

**系统能力：** SystemCapability.Location.Location.Geocoder
