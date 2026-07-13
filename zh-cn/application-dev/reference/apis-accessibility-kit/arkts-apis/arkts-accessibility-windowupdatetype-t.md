# WindowUpdateType

```TypeScript
type WindowUpdateType = 'add' | 'remove' | 'bounds' | 'active' | 'focus'
```

窗口变化类型。

**起始版本：** 7

**元服务API：** 从API版本23开始，该接口支持在元服务API中使用。

**卡片能力：** 从API版本23开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

| 类型 | 说明 |
| --- | --- |
| 'add' | 表示添加窗口的窗口变化事件，值固定为'add'字符串。 |
| 'remove' | 表示一个窗口被删除的窗口变化事件，值固定为'remove'字符串。 |
| 'bounds' | 表示窗口边界已更改的窗口变化事件，值固定为'bounds'字符串。 |
| 'active' | 表示窗口变为活动或不活动的窗口变化事件，值固定为'active'字符串。 |
| 'focus' | 表示窗口焦点发生变化的窗口变化事件，值固定为'focus'字符串。 |

