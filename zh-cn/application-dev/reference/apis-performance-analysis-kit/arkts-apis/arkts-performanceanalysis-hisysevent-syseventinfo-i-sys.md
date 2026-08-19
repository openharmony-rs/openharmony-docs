# SysEventInfo（系统接口）

系统事件信息对象接口。

**起始版本：** 23

<!--Device-hiSysEvent-interface SysEventInfo--><!--Device-hiSysEvent-interface SysEventInfo-End-->

**系统能力：** SystemCapability.HiviewDFX.HiSysEvent

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { hiSysEvent } from '@kit.PerformanceAnalysisKit';
```

## domain

```TypeScript
domain: string
```

事件领域。

**类型：** string

**起始版本：** 23

<!--Device-SysEventInfo-domain: string--><!--Device-SysEventInfo-domain: string-End-->

**系统能力：** SystemCapability.HiviewDFX.HiSysEvent

**系统接口：** 此接口为系统接口。

## eventType

```TypeScript
eventType: EventType
```

事件类型。

**类型：** EventType

**起始版本：** 23

<!--Device-SysEventInfo-eventType: EventType--><!--Device-SysEventInfo-eventType: EventType-End-->

**系统能力：** SystemCapability.HiviewDFX.HiSysEvent

**系统接口：** 此接口为系统接口。

## name

```TypeScript
name: string
```

事件名称。

**类型：** string

**起始版本：** 23

<!--Device-SysEventInfo-name: string--><!--Device-SysEventInfo-name: string-End-->

**系统能力：** SystemCapability.HiviewDFX.HiSysEvent

**系统接口：** 此接口为系统接口。

## params

```TypeScript
params?: Record<string, boolean | int | double | string | bigint | boolean[] | int[] | double[] | string[] | bigint[]> | null | undefined
```

事件参数。

**类型：** Record&lt;string, boolean \| int \| double \| string \| bigint \| boolean[] \| int[] \| double[] \| string[] \| bigint[]&gt; \| null \| undefined

**起始版本：** 23

<!--Device-SysEventInfo-params?: Record<string, boolean | int | double | string | bigint | boolean[] | int[] | double[] | string[] | bigint[]> | null | undefined--><!--Device-SysEventInfo-params?: Record<string, boolean | int | double | string | bigint | boolean[] | int[] | double[] | string[] | bigint[]> | null | undefined-End-->

**系统能力：** SystemCapability.HiviewDFX.HiSysEvent

**系统接口：** 此接口为系统接口。

