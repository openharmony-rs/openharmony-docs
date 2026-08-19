# OnPasteCallback

```TypeScript
declare type OnPasteCallback = (content: string, event: PasteEvent) => void
```

粘贴回调。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-unnamed-declare type OnPasteCallback = (content: string, event: PasteEvent) => void--><!--Device-unnamed-declare type OnPasteCallback = (content: string, event: PasteEvent) => void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| content | string | 是 | 粘贴的文本内容。 |
| event | PasteEvent | 是 | 用户自定义的粘贴事件。 |

