# AccessibilityFocusCallback

```TypeScript
export type AccessibilityFocusCallback = (isFocus: boolean) => void
```

Defines the callback type used in accessibility focus. The value of isFocus indicates whether the current component is focused

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unnamed-export type AccessibilityFocusCallback = (isFocus: boolean) => void--><!--Device-unnamed-export type AccessibilityFocusCallback = (isFocus: boolean) => void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| isFocus | boolean | 是 | if component is focused,isFocus will be true. else isFocus is false. |

