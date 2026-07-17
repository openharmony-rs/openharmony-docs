# EventData

发送事件时传递的数据。

**起始版本：** 7

<!--Device-emitter-export interface EventData--><!--Device-emitter-export interface EventData-End-->

**系统能力：** SystemCapability.Notification.Emitter

## 导入模块

```TypeScript
import { emitter } from '@kit.BasicServicesKit';
```

## data

```TypeScript
data?: { [key: string]: any }
```

发送事件时传递的数据，支持数据类型包括Array、ArrayBuffer、Boolean、DataView、Date、Error、Map、Number、Object、Primitive（除了symbol）、RegExp、Set、String、TypedArray，数据大小最大为16M。

**类型：** { [key: string]: any }

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-EventData-data?: { [key: string]: any }--><!--Device-EventData-data?: { [key: string]: any }-End-->

**系统能力：** SystemCapability.Notification.Emitter

