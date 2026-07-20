# AccessibilityTransparentCallback

```TypeScript
declare type AccessibilityTransparentCallback = (event: TouchEvent) => void
```

Defines the callback type used in accessibility hover transparent event.

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-unnamed-declare type AccessibilityTransparentCallback = (event: TouchEvent) => void--><!--Device-unnamed-declare type AccessibilityTransparentCallback = (event: TouchEvent) => void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | [TouchEvent](../../apis-input-kit/arkts-apis/arkts-input-multimodalinput-touchevent-touchevent-i.md) | 是 | The value of event contains information about original accessibility hover event.  |

