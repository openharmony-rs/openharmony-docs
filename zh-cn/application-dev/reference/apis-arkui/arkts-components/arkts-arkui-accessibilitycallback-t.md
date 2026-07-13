# AccessibilityCallback

```TypeScript
declare type AccessibilityCallback = (isHover: boolean, event: AccessibilityHoverEvent) => void
```

Defines the callback type used in accessibility hover events.
The value of isHover indicates whether the touch is hovering over the component.
The value of event contains information about AccessibilityHoverEvent.

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| isHover | boolean | 是 |  |
| event | AccessibilityHoverEvent | 是 |  |

