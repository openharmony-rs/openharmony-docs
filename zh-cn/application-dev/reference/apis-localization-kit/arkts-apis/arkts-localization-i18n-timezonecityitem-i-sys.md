# TimeZoneCityItem（系统接口）

时区城市的组合信息。

**起始版本：** 10

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

**起始版本：** 10

<!--Device-TimeZoneCityItem-cityDisplayName: string--><!--Device-TimeZoneCityItem-cityDisplayName: string-End-->

**系统能力：** SystemCapability.Global.I18n

**系统接口：** 此接口为系统接口。

## cityId

```TypeScript
cityId: string
```

城市ID，例如Shanghai。

**类型：** string

**起始版本：** 10

<!--Device-TimeZoneCityItem-cityId: string--><!--Device-TimeZoneCityItem-cityId: string-End-->

**系统能力：** SystemCapability.Global.I18n

**系统接口：** 此接口为系统接口。

## offset

```TypeScript
offset: number
```

时区ID的偏移量，单位为毫秒（ms）。

**类型：** number

**起始版本：** 10

<!--Device-TimeZoneCityItem-offset: int--><!--Device-TimeZoneCityItem-offset: int-End-->

**系统能力：** SystemCapability.Global.I18n

**系统接口：** 此接口为系统接口。

## rawOffset

```TypeScript
rawOffset?: number
```

时区ID的固定偏移量，单位为毫秒（ms）。

**类型：** number

**起始版本：** 10

<!--Device-TimeZoneCityItem-rawOffset?: int--><!--Device-TimeZoneCityItem-rawOffset?: int-End-->

**系统能力：** SystemCapability.Global.I18n

**系统接口：** 此接口为系统接口。

## zoneDisplayName

```TypeScript
zoneDisplayName: string
```

时区ID在系统区域下显示的名称。

**类型：** string

**起始版本：** 10

<!--Device-TimeZoneCityItem-zoneDisplayName: string--><!--Device-TimeZoneCityItem-zoneDisplayName: string-End-->

**系统能力：** SystemCapability.Global.I18n

**系统接口：** 此接口为系统接口。

## zoneId

```TypeScript
zoneId: string
```

时区ID，例如Asia/Shanghai。

**类型：** string

**起始版本：** 10

<!--Device-TimeZoneCityItem-zoneId: string--><!--Device-TimeZoneCityItem-zoneId: string-End-->

**系统能力：** SystemCapability.Global.I18n

**系统接口：** 此接口为系统接口。

