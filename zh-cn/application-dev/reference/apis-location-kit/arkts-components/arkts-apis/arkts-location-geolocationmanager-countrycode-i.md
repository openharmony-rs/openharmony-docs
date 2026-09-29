# CountryCode

```TypeScript
export interface CountryCode
```

国家码信息，包含国家码字符串和国家码的来源信息。

**起始版本：** 9

<!--Device-geoLocationManager-export interface CountryCode--><!--Device-geoLocationManager-export interface CountryCode-End-->

**系统能力：** SystemCapability.Location.Location.Core

## 导入模块

```TypeScript
import { geoLocationManager } from '@kit.LocationKit';
```

## country

```TypeScript
country: string
```

表示国家码字符串。

**类型：** string

**起始版本：** 9

<!--Device-CountryCode-country: string--><!--Device-CountryCode-country: string-End-->

**系统能力：** SystemCapability.Location.Location.Core

## type

```TypeScript
type: CountryCodeType
```

表示国家码信息来源。

**类型：** [CountryCodeType](arkts-location-geolocationmanager-countrycodetype-e.md)

**起始版本：** 9

<!--Device-CountryCode-type: CountryCodeType--><!--Device-CountryCode-type: CountryCodeType-End-->

**系统能力：** SystemCapability.Location.Location.Core
