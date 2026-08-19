# EventData

发送事件时传递的数据。

**起始版本：** 23

<!--Device-emitter-export interface EventData--><!--Device-emitter-export interface EventData-End-->

**系统能力：** SystemCapability.Notification.Emitter

## 导入模块

```TypeScript
import { emitter } from '@kit.BasicServicesKit';
```

## data

```TypeScript
data?: Record<string, RecordData> | ESValue
```

发送事件时传递的数据，支持数据类型包括Array、ArrayBuffer、Boolean、DataView、Date、Error、Map、Number、Object、Primitive（除了symbol）、RegExp、Set 、String、TypedArray，数据大小最大为16M。

**类型：** Record&lt;string, [RecordData](arkts-basicservices-recorddata-t.md)&gt; \| ESValue

**起始版本：** 23

<!--Device-EventData-data?: Record<string, RecordData> | ESValue--><!--Device-EventData-data?: Record<string, RecordData> | ESValue-End-->

**系统能力：** SystemCapability.Notification.Emitter

