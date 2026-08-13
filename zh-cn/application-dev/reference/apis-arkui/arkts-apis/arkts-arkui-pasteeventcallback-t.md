# PasteEventCallback

```TypeScript
export type PasteEventCallback = (event?: PasteEvent) => void
```

粘贴完成前，触发回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unnamed-export type PasteEventCallback = (event?: PasteEvent) => void--><!--Device-unnamed-export type PasteEventCallback = (event?: PasteEvent) => void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | [PasteEvent](arkts-arkui-richeditor-pasteevent-i.md) | 否 | 定义用户粘贴事件。 |

