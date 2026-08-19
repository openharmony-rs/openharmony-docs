# TimeZoneCityItem（系统接口）

时区城市的组合信息。

**起始版本：** 23

<!--Device-i18n-export interface TimeZoneCityItem--><!--Device-i18n-export interface TimeZoneCityItem-End-->

**系统能力：** SystemCapability.Global.I18n

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { i18n } from '@kit.LocalizationKit';
```

## cityDisplayName

```TypeScript
cityDisplayName: string
```

城市ID在系统区域下显示的名称。

**类型：** string

**起始版本：** 23

<!--Device-TimeZoneCityItem-cityDisplayName: string--><!--Device-TimeZoneCityItem-cityDisplayName: string-End-->

**系统能力：** SystemCapability.Global.I18n

**系统接口：** 此接口为系统接口。

## cityId

```TypeScript
cityId: string
```

城市ID，例如Shanghai。

**类型：** string

**起始版本：** 23

<!--Device-TimeZoneCityItem-cityId: string--><!--Device-TimeZoneCityItem-cityId: string-End-->

**系统能力：** SystemCapability.Global.I18n

**系统接口：** 此接口为系统接口。

## latitude

```TypeScript
latitude: double
```

以十进制度数表示的时区城市纬度信息(°)。

**类型：** double

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-TimeZoneCityItem-latitude: double--><!--Device-TimeZoneCityItem-latitude: double-End-->

**系统能力：** SystemCapability.Global.I18n

**系统接口：** 此接口为系统接口。

## longitude

```TypeScript
longitude: double
```

时区城市的经度信息，十进制度数(°)。

**类型：** double

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-TimeZoneCityItem-longitude: double--><!--Device-TimeZoneCityItem-longitude: double-End-->

**系统能力：** SystemCapability.Global.I18n

**系统接口：** 此接口为系统接口。

## offset

```TypeScript
offset: int
```

时区ID的偏移量，单位为毫秒（ms）。

**类型：** int

**起始版本：** 23

<!--Device-TimeZoneCityItem-offset: int--><!--Device-TimeZoneCityItem-offset: int-End-->

**系统能力：** SystemCapability.Global.I18n

**系统接口：** 此接口为系统接口。

## rawOffset

```TypeScript
rawOffset?: int
```

时区ID的固定偏移量，单位为毫秒（ms）。

**类型：** int

**起始版本：** 23

<!--Device-TimeZoneCityItem-rawOffset?: int--><!--Device-TimeZoneCityItem-rawOffset?: int-End-->

**系统能力：** SystemCapability.Global.I18n

**系统接口：** 此接口为系统接口。

## zoneDisplayName

```TypeScript
zoneDisplayName: string
```

时区ID在系统区域下显示的名称。

**类型：** string

**起始版本：** 23

<!--Device-TimeZoneCityItem-zoneDisplayName: string--><!--Device-TimeZoneCityItem-zoneDisplayName: string-End-->

**系统能力：** SystemCapability.Global.I18n

**系统接口：** 此接口为系统接口。

## zoneId

```TypeScript
zoneId: string
```

时区ID，例如Asia/Shanghai。

**类型：** string

**起始版本：** 23

<!--Device-TimeZoneCityItem-zoneId: string--><!--Device-TimeZoneCityItem-zoneId: string-End-->

**系统能力：** SystemCapability.Global.I18n

**系统接口：** 此接口为系统接口。

