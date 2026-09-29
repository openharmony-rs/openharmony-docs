# GeoAddress

```TypeScript
export interface GeoAddress
```

地理编码地址信息。

@interface GeoAddress

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [GeoAddress](arkts-location-geolocationmanager-geoaddress-i.md)

**需要权限：** ohos.permission.LOCATION

<!--Device-geolocation-export interface GeoAddress--><!--Device-geolocation-export interface GeoAddress-End-->

**系统能力：** SystemCapability.Location.Location.Geocoder

## 导入模块

```TypeScript
import { geolocation } from '@kit.LocationKit';
```

## addressUrl

```TypeScript
addressUrl?: string
```

表示位置信息附件的网址信息。

**类型：** string

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [addressUrl](arkts-location-geolocationmanager-geoaddress-i.md#addressurl)

**需要权限：** ohos.permission.LOCATION

<!--Device-GeoAddress-addressUrl?: string--><!--Device-GeoAddress-addressUrl?: string-End-->

**系统能力：** SystemCapability.Location.Location.Geocoder

## administrativeArea

```TypeScript
administrativeArea?: string
```

表示省份区域信息。

**类型：** string

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [administrativeArea](arkts-location-geolocationmanager-geoaddress-i.md#administrativearea)

**需要权限：** ohos.permission.LOCATION

<!--Device-GeoAddress-administrativeArea?: string--><!--Device-GeoAddress-administrativeArea?: string-End-->

**系统能力：** SystemCapability.Location.Location.Geocoder

## countryCode

```TypeScript
countryCode?: string
```

表示国家码信息。

**类型：** string

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [countryCode](arkts-location-geolocationmanager-geoaddress-i.md#countrycode)

**需要权限：** ohos.permission.LOCATION

<!--Device-GeoAddress-countryCode?: string--><!--Device-GeoAddress-countryCode?: string-End-->

**系统能力：** SystemCapability.Location.Location.Geocoder

## countryName

```TypeScript
countryName?: string
```

表示国家信息。

**类型：** string

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [countryName](arkts-location-geolocationmanager-geoaddress-i.md#countryname)

**需要权限：** ohos.permission.LOCATION

<!--Device-GeoAddress-countryName?: string--><!--Device-GeoAddress-countryName?: string-End-->

**系统能力：** SystemCapability.Location.Location.Geocoder

## descriptions

```TypeScript
descriptions?: Array<string>
```

表示附加的描述信息。

**类型：** Array&lt;string&gt;

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [descriptions](arkts-location-geolocationmanager-geoaddress-i.md#descriptions)

**需要权限：** ohos.permission.LOCATION

<!--Device-GeoAddress-descriptions?: Array<string>--><!--Device-GeoAddress-descriptions?: Array<string>-End-->

**系统能力：** SystemCapability.Location.Location.Geocoder

## descriptionsSize

```TypeScript
descriptionsSize?: number
```

表示附加的描述信息数量。取值范围为大于等于0，推荐该值小于10。

**类型：** number

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [descriptionsSize](arkts-location-geolocationmanager-geoaddress-i.md#descriptionssize)

**需要权限：** ohos.permission.LOCATION

<!--Device-GeoAddress-descriptionsSize?: number--><!--Device-GeoAddress-descriptionsSize?: number-End-->

**系统能力：** SystemCapability.Location.Location.Geocoder

## latitude

```TypeScript
latitude?: number
```

表示纬度信息，正值表示北纬，负值表示南纬。取值范围为-90到90。

**类型：** number

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [latitude](arkts-location-geolocationmanager-geoaddress-i.md#latitude)

**需要权限：** ohos.permission.LOCATION

<!--Device-GeoAddress-latitude?: number--><!--Device-GeoAddress-latitude?: number-End-->

**系统能力：** SystemCapability.Location.Location.Geocoder

## locale

```TypeScript
locale?: string
```

表示位置描述信息的语言，“zh”代表中文，“en”代表英文。

**类型：** string

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [locale](arkts-location-geolocationmanager-geoaddress-i.md#locale)

**需要权限：** ohos.permission.LOCATION

<!--Device-GeoAddress-locale?: string--><!--Device-GeoAddress-locale?: string-End-->

**系统能力：** SystemCapability.Location.Location.Geocoder

## locality

```TypeScript
locality?: string
```

表示城市信息。

**类型：** string

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [locality](arkts-location-geolocationmanager-geoaddress-i.md#locality)

**需要权限：** ohos.permission.LOCATION

<!--Device-GeoAddress-locality?: string--><!--Device-GeoAddress-locality?: string-End-->

**系统能力：** SystemCapability.Location.Location.Geocoder

## longitude

```TypeScript
longitude?: number
```

表示经度信息，正值表示东经，负值表是西经。取值范围为-180到180。

**类型：** number

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [longitude](arkts-location-geolocationmanager-geoaddress-i.md#longitude)

**需要权限：** ohos.permission.LOCATION

<!--Device-GeoAddress-longitude?: number--><!--Device-GeoAddress-longitude?: number-End-->

**系统能力：** SystemCapability.Location.Location.Geocoder

## phoneNumber

```TypeScript
phoneNumber?: string
```

表示联系方式信息。

**类型：** string

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [phoneNumber](arkts-location-geolocationmanager-geoaddress-i.md#phonenumber)

**需要权限：** ohos.permission.LOCATION

<!--Device-GeoAddress-phoneNumber?: string--><!--Device-GeoAddress-phoneNumber?: string-End-->

**系统能力：** SystemCapability.Location.Location.Geocoder

## placeName

```TypeScript
placeName?: string
```

表示地区信息。

**类型：** string

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [placeName](arkts-location-geolocationmanager-geoaddress-i.md#placename)

**需要权限：** ohos.permission.LOCATION

<!--Device-GeoAddress-placeName?: string--><!--Device-GeoAddress-placeName?: string-End-->

**系统能力：** SystemCapability.Location.Location.Geocoder

## postalCode

```TypeScript
postalCode?: string
```

表示邮政编码信息。

**类型：** string

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [postalCode](arkts-location-geolocationmanager-geoaddress-i.md#postalcode)

**需要权限：** ohos.permission.LOCATION

<!--Device-GeoAddress-postalCode?: string--><!--Device-GeoAddress-postalCode?: string-End-->

**系统能力：** SystemCapability.Location.Location.Geocoder

## premises

```TypeScript
premises?: string
```

表示门牌号信息。

**类型：** string

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [premises](arkts-location-geolocationmanager-geoaddress-i.md#premises)

**需要权限：** ohos.permission.LOCATION

<!--Device-GeoAddress-premises?: string--><!--Device-GeoAddress-premises?: string-End-->

**系统能力：** SystemCapability.Location.Location.Geocoder

## roadName

```TypeScript
roadName?: string
```

表示路名信息。

**类型：** string

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [roadName](arkts-location-geolocationmanager-geoaddress-i.md#roadname)

**需要权限：** ohos.permission.LOCATION

<!--Device-GeoAddress-roadName?: string--><!--Device-GeoAddress-roadName?: string-End-->

**系统能力：** SystemCapability.Location.Location.Geocoder

## subAdministrativeArea

```TypeScript
subAdministrativeArea?: string
```

表示子区域信息。

**类型：** string

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [subAdministrativeArea](arkts-location-geolocationmanager-geoaddress-i.md#subadministrativearea)

**需要权限：** ohos.permission.LOCATION

<!--Device-GeoAddress-subAdministrativeArea?: string--><!--Device-GeoAddress-subAdministrativeArea?: string-End-->

**系统能力：** SystemCapability.Location.Location.Geocoder

## subLocality

```TypeScript
subLocality?: string
```

表示子城市信息。

**类型：** string

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [subLocality](arkts-location-geolocationmanager-geoaddress-i.md#sublocality)

**需要权限：** ohos.permission.LOCATION

<!--Device-GeoAddress-subLocality?: string--><!--Device-GeoAddress-subLocality?: string-End-->

**系统能力：** SystemCapability.Location.Location.Geocoder

## subRoadName

```TypeScript
subRoadName?: string
```

表示子路名信息。

**类型：** string

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [subRoadName](arkts-location-geolocationmanager-geoaddress-i.md#subroadname)

**需要权限：** ohos.permission.LOCATION

<!--Device-GeoAddress-subRoadName?: string--><!--Device-GeoAddress-subRoadName?: string-End-->

**系统能力：** SystemCapability.Location.Location.Geocoder
