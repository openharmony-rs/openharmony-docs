# PasteEventCallback

```TypeScript
declare type PasteEventCallback = (event?: PasteEvent) => void
```

粘贴完成前，触发回调。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | PasteEvent | 否 | 定义用户粘贴事件。 |

