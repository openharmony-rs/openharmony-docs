# AccessibilityCallback

```TypeScript
export type AccessibilityCallback = (isHover: boolean, event: AccessibilityHoverEvent) => void
```

Defines the callback type used in accessibility hover events. The value of isHover indicates whether the touch is hovering over the component. The value of event contains information about AccessibilityHoverEvent.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unnamed-export type AccessibilityCallback = (isHover: boolean, event: AccessibilityHoverEvent) => void--><!--Device-unnamed-export type AccessibilityCallback = (isHover: boolean, event: AccessibilityHoverEvent) => void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| isHover | boolean | 是 |  |
| event | [AccessibilityHoverEvent](arkts-na-common-accessibilityhoverevent-i.md) | 是 |  |

