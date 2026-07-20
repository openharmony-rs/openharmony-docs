# RichEditorSymbolSpanOptions

设置SymbolSpan组件的偏移位置和样式。

**起始版本：** 11

<!--Device-unnamed-declare interface RichEditorSymbolSpanOptions--><!--Device-unnamed-declare interface RichEditorSymbolSpanOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## offset

```TypeScript
offset?: number
```

添加SymbolSpan的位置。省略时，添加到所有内容的最后。

如果值小于0，添加到所有内容的最前面；如果值大于所有内容的长度，添加到所有内容的最后面。

**类型：** number

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-RichEditorSymbolSpanOptions-offset?: number--><!--Device-RichEditorSymbolSpanOptions-offset?: number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## style

```TypeScript
style?: RichEditorSymbolSpanStyle
```

SymbolSpan样式信息。当需要自定义SymbolSpan的颜色、大小、粗细、渲染策略等样式时传入此参数；省略时，使用系统默认样式信息。

**类型：** RichEditorSymbolSpanStyle

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-RichEditorSymbolSpanOptions-style?: RichEditorSymbolSpanStyle--><!--Device-RichEditorSymbolSpanOptions-style?: RichEditorSymbolSpanStyle-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

