# HoverCallback

```TypeScript
declare type HoverCallback = (isHover: boolean, event: HoverEvent) => void
```

hover事件的回调类型。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| isHover | boolean | 是 | 是否处于hover状态，true表示处于hover状态，false表示不在hover状态。 |
| event | HoverEvent | 是 | 获取鼠标或手写笔悬浮的位置坐标。 |

