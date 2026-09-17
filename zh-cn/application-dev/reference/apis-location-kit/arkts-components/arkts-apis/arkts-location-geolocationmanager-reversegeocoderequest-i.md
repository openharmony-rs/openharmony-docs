# ReverseGeoCodeRequest

逆地理编码请求参数。

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

## latitude

```TypeScript
latitude: number
```

表示纬度信息，正值表示北纬，负值表示南纬。取值范围为-90到90。仅支持WGS84坐标系。

**类型：** number

**起始版本：** 9

**系统能力：** SystemCapability.Location.Location.Geocoder

## locale

```TypeScript
locale?: string
```

指定位置描述信息的语言，“zh”代表中文，“en”代表英文。默认值从设置中的“语言和地区”获取。

**类型：** string

**起始版本：** 9

**系统能力：** SystemCapability.Location.Location.Geocoder

## longitude

```TypeScript
longitude: number
```

表示经度信息，正值表示东经，负值表示西经。取值范围为-180到180。仅支持WGS84坐标系。

**类型：** number

**起始版本：** 9

**系统能力：** SystemCapability.Location.Location.Geocoder

## maxItems

```TypeScript
maxItems?: number
```

指定返回位置信息的最大个数。取值范围为大于等于0，推荐该值小于10。默认值是1。

**类型：** number

**起始版本：** 9

**系统能力：** SystemCapability.Location.Location.Geocoder
