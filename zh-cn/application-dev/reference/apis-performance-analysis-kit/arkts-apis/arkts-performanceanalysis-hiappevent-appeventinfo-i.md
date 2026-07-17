# AppEventInfo

提供事件信息的参数选项。

**起始版本：** 9

<!--Device-hiAppEvent-interface AppEventInfo--><!--Device-hiAppEvent-interface AppEventInfo-End-->

**系统能力：** SystemCapability.HiviewDFX.HiAppEvent

## 导入模块

```TypeScript
import { hiAppEvent } from '@kit.PerformanceAnalysisKit';
```

## domain

```TypeScript
domain: string
```

事件领域。事件领域名称支持数字、字母、下划线字符，需要以字母开头且不能以下划线结尾，长度非空且不超过32个字符。

**类型：** string

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-AppEventInfo-domain: string--><!--Device-AppEventInfo-domain: string-End-->

**系统能力：** SystemCapability.HiviewDFX.HiAppEvent

## eventType

```TypeScript
eventType: EventType
```

事件类型。

**类型：** EventType

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-AppEventInfo-eventType: EventType--><!--Device-AppEventInfo-eventType: EventType-End-->

**系统能力：** SystemCapability.HiviewDFX.HiAppEvent

## name

```TypeScript
name: string
```

事件名称。首字符必须为字母字符或$字符，中间字符必须为数字字符、字母字符或下划线字符，结尾字符必须为数字字符或字母字符，长度非空且不超过48个字符。

**类型：** string

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-AppEventInfo-name: string--><!--Device-AppEventInfo-name: string-End-->

**系统能力：** SystemCapability.HiviewDFX.HiAppEvent

## params

```TypeScript
params: object
```

事件参数对象，包含每个事件参数的参数名和参数值。**系统事件中params包含的字段已由各系统事件定义，具体字段含义在各类系统事件指南的介绍中，例如[崩溃事件介绍](../../../../dfx/hiappevent-watcher-crash-events.md)。** 针对应用事件，[Write](arkts-performanceanalysis-hiappevent-write-f.md#write-1)打点写入的参数由开发者定义，其规格如下：

- 参数名为string类型，首字符必须为字母字符或`$`字符，中间字符必须为数字字符、字母字符或下划线字符，结尾字符必须为数字字符或字母字符，长度非空且不超过32个字符。如testName、$123_name等。  
- 参数值支持string、number、boolean、数组类型。string类型参数长度需在8*1024个字符以内，超出后会和对应的参数名一同被丢弃；number类型参数取值需在Number.MIN_SAFE_INTEGER~Number.MAX_SAFE_INTEGER范围内，超出可能会产生不确定值；数组类型参数中的元素类型只能全为string、number、boolean中的一种，且元素个数需在100以内，超出部分即从第101个元素开始会被丢弃。  
- 参数个数需在32个以内，超出的参数会做丢弃处理。

**类型：** object

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-AppEventInfo-params: object--><!--Device-AppEventInfo-params: object-End-->

**系统能力：** SystemCapability.HiviewDFX.HiAppEvent

