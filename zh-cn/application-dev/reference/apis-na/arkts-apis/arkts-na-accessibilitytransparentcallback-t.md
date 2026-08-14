# AccessibilityTransparentCallback

```TypeScript
export type AccessibilityTransparentCallback = (event: TouchEvent) => void
```

Defines the callback type used in accessibility hover transparent event.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unnamed-export type AccessibilityTransparentCallback = (event: TouchEvent) => void--><!--Device-unnamed-export type AccessibilityTransparentCallback = (event: TouchEvent) => void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | [TouchEvent](arkts-na-common-touchevent-i.md) | 是 | The value of event contains information about original accessibility hover event. |

