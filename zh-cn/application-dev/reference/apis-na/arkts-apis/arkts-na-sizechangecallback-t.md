# SizeChangeCallback

```TypeScript
export type SizeChangeCallback = (oldValue: SizeOptions, newValue: SizeOptions) => void
```

Defines the callback type used in onSizeChange.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unnamed-export type SizeChangeCallback = (oldValue: SizeOptions, newValue: SizeOptions) => void--><!--Device-unnamed-export type SizeChangeCallback = (oldValue: SizeOptions, newValue: SizeOptions) => void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| oldValue | [SizeOptions](../../apis-arkui/arkts-apis/arkts-arkui-sizeoptions-i.md) | 是 | the width and height of the component before the change. |
| newValue | [SizeOptions](../../apis-arkui/arkts-apis/arkts-arkui-sizeoptions-i.md) | 是 | the width and height of the component after the change. |

