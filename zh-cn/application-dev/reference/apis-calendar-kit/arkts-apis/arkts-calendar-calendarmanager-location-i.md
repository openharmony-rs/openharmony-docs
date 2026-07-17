# Location

日程地点。

**起始版本：** 10

<!--Device-calendarManager-interface Location--><!--Device-calendarManager-interface Location-End-->

**系统能力：** SystemCapability.Applications.CalendarData

## 导入模块

```TypeScript
import { calendarManager } from '@kit.CalendarKit';
```

## latitude

```TypeScript
latitude?: number
```

地点纬度。取值范围[-90, 90]，默认为undefined。超过取值范围地图将无法正常显示。

**类型：** number

**起始版本：** 10

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-Location-latitude?: number--><!--Device-Location-latitude?: number-End-->

**系统能力：** SystemCapability.Applications.CalendarData

## location

```TypeScript
location?: string
```

日程地点。不填时，默认为undefined。

**类型：** string

**起始版本：** 10

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-Location-location?: string--><!--Device-Location-location?: string-End-->

**系统能力：** SystemCapability.Applications.CalendarData

## longitude

```TypeScript
longitude?: number
```

地点经度。取值范围[-180, 180]，默认为undefined。超过取值范围地图将无法正常显示。

**类型：** number

**起始版本：** 10

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-Location-longitude?: number--><!--Device-Location-longitude?: number-End-->

**系统能力：** SystemCapability.Applications.CalendarData

