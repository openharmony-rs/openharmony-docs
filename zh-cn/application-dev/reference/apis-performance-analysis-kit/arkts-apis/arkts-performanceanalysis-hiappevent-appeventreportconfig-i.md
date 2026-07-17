# AppEventReportConfig

数据处理者可以上报事件的描述配置。

**起始版本：** 11

<!--Device-hiAppEvent-interface AppEventReportConfig--><!--Device-hiAppEvent-interface AppEventReportConfig-End-->

**系统能力：** SystemCapability.HiviewDFX.HiAppEvent

## 导入模块

```TypeScript
import { hiAppEvent } from '@kit.PerformanceAnalysisKit';
```

## domain

```TypeScript
domain?: string
```

事件领域。默认为空字符串，事件领域名称支持数字、字母、下划线字符，需要以字母开头且不能以下划线结尾，长度非空且不超过32个字符。

**类型：** string

**起始版本：** 11

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-AppEventReportConfig-domain?: string--><!--Device-AppEventReportConfig-domain?: string-End-->

**系统能力：** SystemCapability.HiviewDFX.HiAppEvent

## isRealTime

```TypeScript
isRealTime?: boolean
```

是否实时上报事件。默认值为false，配置值为true表示实时上报事件，false表示不实时上报事件。

**类型：** boolean

**起始版本：** 11

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-AppEventReportConfig-isRealTime?: boolean--><!--Device-AppEventReportConfig-isRealTime?: boolean-End-->

**系统能力：** SystemCapability.HiviewDFX.HiAppEvent

## name

```TypeScript
name?: string
```

事件名称。默认为空字符串，首字符必须为字母字符或$字符，中间字符必须为数字字符、字母字符或下划线字符，结尾字符必须为数字字符或字母字符，长度非空且不超过48个字符。

**类型：** string

**起始版本：** 11

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-AppEventReportConfig-name?: string--><!--Device-AppEventReportConfig-name?: string-End-->

**系统能力：** SystemCapability.HiviewDFX.HiAppEvent

