# AccessibilityFocusCallback

```TypeScript
declare type AccessibilityFocusCallback = (isFocus: boolean) => void
```

Defines the callback type used in accessibility focus. The value of isFocus indicates whether the current component is focused

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本18开始，该接口支持在元服务API中使用。

**卡片能力：** 从API版本18开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| isFocus | boolean | 是 | if component is focused,isFocus will be true. else isFocus is false. |

