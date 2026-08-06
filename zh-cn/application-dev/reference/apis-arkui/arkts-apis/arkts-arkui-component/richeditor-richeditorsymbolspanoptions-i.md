# RichEditorSymbolSpanOptions

设置SymbolSpan组件的偏移位置和样式。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-unnamed-export declare interface RichEditorSymbolSpanOptions--><!--Device-unnamed-export declare interface RichEditorSymbolSpanOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## offset

```TypeScript
offset?: int
```

添加组件的位置。省略时，添加到所有内容的最后。 如果值小于0，添加到所有内容的最前面；如果值大于所有内容的长度，添加到所有内容的最后面。

**类型：** int

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-RichEditorSymbolSpanOptions-offset?: int--><!--Device-RichEditorSymbolSpanOptions-offset?: int-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## style

```TypeScript
style?: RichEditorSymbolSpanStyle
```

组件样式信息。省略时，使用系统默认样式信息。

**类型：** RichEditorSymbolSpanStyle

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-RichEditorSymbolSpanOptions-style?: RichEditorSymbolSpanStyle--><!--Device-RichEditorSymbolSpanOptions-style?: RichEditorSymbolSpanStyle-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

