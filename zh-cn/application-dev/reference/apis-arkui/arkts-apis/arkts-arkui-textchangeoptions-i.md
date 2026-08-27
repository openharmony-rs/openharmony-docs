# TextChangeOptions

文本变化相关信息，包括变化前后的选区范围、变化前的文本内容等。

**起始版本：** 15

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
```

## oldContent

```TypeScript
oldContent: string
```

变化前的文本内容。

**类型：** string

**起始版本：** 15

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本15开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## oldPreviewText

```TypeScript
oldPreviewText: PreviewText
```

变化前的预上屏信息。

**类型：** [PreviewText](arkts-arkui-previewtext-i.md)

**起始版本：** 15

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本15开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## rangeAfter

```TypeScript
rangeAfter: TextRange
```

变化后的选区范围。

**类型：** [TextRange](arkts-arkui-textrange-i.md)

**起始版本：** 15

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本15开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## rangeBefore

```TypeScript
rangeBefore: TextRange
```

变化前的选区范围。

**类型：** [TextRange](arkts-arkui-textrange-i.md)

**起始版本：** 15

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本15开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full
