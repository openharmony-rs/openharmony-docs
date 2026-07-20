# PasteEventCallback

```TypeScript
declare type PasteEventCallback = (event?: PasteEvent) => void
```

粘贴完成前，触发回调。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-unnamed-declare type PasteEventCallback = (event?: PasteEvent) => void--><!--Device-unnamed-declare type PasteEventCallback = (event?: PasteEvent) => void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | [PasteEvent](arkts-arkui-pasteevent-i.md) | 否 | 定义用户粘贴事件。省略时，不接收粘贴事件信息。  |

