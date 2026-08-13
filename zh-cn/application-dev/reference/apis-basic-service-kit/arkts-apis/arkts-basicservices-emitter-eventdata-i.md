# EventData

发送事件时传递的数据。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-emitter-export interface EventData--><!--Device-emitter-export interface EventData-End-->

**系统能力：** SystemCapability.Notification.Emitter

## data

```TypeScript
data?: Record<string, RecordData> | ESValue
```

发送事件时传递的数据，支持数据类型包括Array、ArrayBuffer、Boolean、DataView、Date、Error、Map、Number、Object、Primitive（除了symbol）、RegExp、Set 、String、TypedArray，数据大小最大为16M。

**类型：** Record&lt;string, [RecordData](arkts-basicservices-recorddata-t.md)&gt; \| ESValue

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-EventData-data?: Record<string, RecordData> | ESValue--><!--Device-EventData-data?: Record<string, RecordData> | ESValue-End-->

**系统能力：** SystemCapability.Notification.Emitter

