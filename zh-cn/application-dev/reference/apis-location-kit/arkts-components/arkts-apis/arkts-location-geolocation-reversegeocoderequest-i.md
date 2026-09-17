# ReverseGeoCodeRequest

逆地理编码请求参数。

@interface ReverseGeoCodeRequest

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [ReverseGeoCodeRequest](arkts-location-geolocationmanager-reversegeocoderequest-i.md)

**需要权限：** ohos.permission.LOCATION

**系统能力：** SystemCapability.Location.Location.Geocoder

## 导入模块

```TypeScript
import { geolocation } from '@kit.LocationKit';
```

## latitude

```TypeScript
latitude: number
```

表示纬度信息，正值表示北纬，负值表示南纬。取值范围为-90到90。

**类型：** number

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [latitude](arkts-location-geolocationmanager-reversegeocoderequest-i.md#latitude)

**系统能力：** SystemCapability.Location.Location.Geocoder

## locale

```TypeScript
locale?: string
```

指定位置描述信息的语言，“zh”代表中文，“en”代表英文。

**类型：** string

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [locale](arkts-location-geolocationmanager-reversegeocoderequest-i.md#locale)

**系统能力：** SystemCapability.Location.Location.Geocoder

## longitude

```TypeScript
longitude: number
```

表示经度信息，正值表示东经，负值表示西经。取值范围为-180到180。

**类型：** number

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [longitude](arkts-location-geolocationmanager-reversegeocoderequest-i.md#longitude)

**系统能力：** SystemCapability.Location.Location.Geocoder

## maxItems

```TypeScript
maxItems?: number
```

指定返回位置信息的最大个数。取值范围为大于等于0，推荐该值小于10。

**类型：** number

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [maxItems](arkts-location-geolocationmanager-reversegeocoderequest-i.md#maxitems)

**系统能力：** SystemCapability.Location.Location.Geocoder
