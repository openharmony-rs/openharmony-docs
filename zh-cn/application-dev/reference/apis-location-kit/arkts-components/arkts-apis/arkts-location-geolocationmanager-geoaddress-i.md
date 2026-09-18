# GeoAddress

地理编码地址信息。

**起始版本：** 9

**系统能力：** SystemCapability.Location.Location.Geocoder

## 导入模块

```TypeScript
import { geoLocationManager } from '@kit.LocationKit';
```

## addressUrl

```TypeScript
addressUrl?: string
```

表示位置信息附件的网址信息。

**类型：** string

**起始版本：** 9

**系统能力：** SystemCapability.Location.Location.Geocoder

## administrativeArea

```TypeScript
administrativeArea?: string
```

表示国家以下的一级行政区，一般是省/州。

**类型：** string

**起始版本：** 9

**系统能力：** SystemCapability.Location.Location.Geocoder

## countryCode

```TypeScript
countryCode?: string
```

表示国家码信息。

**类型：** string

**起始版本：** 9

**系统能力：** SystemCapability.Location.Location.Geocoder

## countryName

```TypeScript
countryName?: string
```

表示国家信息。

**类型：** string

**起始版本：** 9

**系统能力：** SystemCapability.Location.Location.Geocoder

## descriptions

```TypeScript
descriptions?: Array<string>
```

表示附加的描述信息。目前包含城市编码cityCode（Array下标为0）和区划编码adminCode（Array下标为1），例如["025","320114001"]。

**类型：** Array&lt;string&gt;

**起始版本：** 9

**系统能力：** SystemCapability.Location.Location.Geocoder

## descriptionsSize

```TypeScript
descriptionsSize?: number
```

表示附加的描述信息数量。取值范围为大于等于0，推荐该值小于10。

**类型：** number

**起始版本：** 9

**系统能力：** SystemCapability.Location.Location.Geocoder

## latitude

```TypeScript
latitude?: number
```

表示纬度信息，正值表示北纬，负值表示南纬。取值范围为-90到90。仅支持WGS84坐标系。

**类型：** number

**起始版本：** 9

**系统能力：** SystemCapability.Location.Location.Geocoder

## locale

```TypeScript
locale?: string
```

表示位置描述信息的语言，“zh”代表中文，“en”代表英文。

**类型：** string

**起始版本：** 9

**系统能力：** SystemCapability.Location.Location.Geocoder

## locality

```TypeScript
locality?: string
```

表示城市信息，一般是市。

**类型：** string

**起始版本：** 9

**系统能力：** SystemCapability.Location.Location.Geocoder

## longitude

```TypeScript
longitude?: number
```

表示经度信息，正值表示东经，负值表示西经。取值范围为-180到180。仅支持WGS84坐标系。

**类型：** number

**起始版本：** 9

**系统能力：** SystemCapability.Location.Location.Geocoder

## phoneNumber

```TypeScript
phoneNumber?: string
```

表示联系方式信息。

**类型：** string

**起始版本：** 9

**系统能力：** SystemCapability.Location.Location.Geocoder

## placeName

```TypeScript
placeName?: string
```

表示详细地址信息。

**类型：** string

**起始版本：** 9

**系统能力：** SystemCapability.Location.Location.Geocoder

## postalCode

```TypeScript
postalCode?: string
```

表示邮政编码信息。

**类型：** string

**起始版本：** 9

**系统能力：** SystemCapability.Location.Location.Geocoder

## premises

```TypeScript
premises?: string
```

表示门牌号信息。

**类型：** string

**起始版本：** 9

**系统能力：** SystemCapability.Location.Location.Geocoder

## roadName

```TypeScript
roadName?: string
```

表示路名信息。

**类型：** string

**起始版本：** 9

**系统能力：** SystemCapability.Location.Location.Geocoder

## subAdministrativeArea

```TypeScript
subAdministrativeArea?: string
```

表示国家以下的二级行政区，一般是市。

**类型：** string

**起始版本：** 9

**系统能力：** SystemCapability.Location.Location.Geocoder

## subLocality

```TypeScript
subLocality?: string
```

表示子城市信息，一般是区/县。

**类型：** string

**起始版本：** 9

**系统能力：** SystemCapability.Location.Location.Geocoder

## subRoadName

```TypeScript
subRoadName?: string
```

表示子路名信息。

**类型：** string

**起始版本：** 9

**系统能力：** SystemCapability.Location.Location.Geocoder
