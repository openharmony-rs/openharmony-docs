# EventProcess

```TypeScript
type EventProcess = (event: string, args: Record<string, Object>) => void
```

The general process funcation with an event and arguments.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-avSession-type EventProcess = (event: string, args: Record<string, Object>) => void--><!--Device-avSession-type EventProcess = (event: string, args: Record<string, Object>) => void-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | string | 是 | 请求事件。  |
| args | Record&lt;string, Object&gt; | 是 | arguments associated with event  |

