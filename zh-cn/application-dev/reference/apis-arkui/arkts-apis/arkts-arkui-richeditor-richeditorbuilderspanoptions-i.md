# RichEditorBuilderSpanOptions

设置builder的偏移位置和样式。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-unnamed-export declare interface RichEditorBuilderSpanOptions--><!--Device-unnamed-export declare interface RichEditorBuilderSpanOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## accessibilitySpanOptions

```TypeScript
accessibilitySpanOptions?: AccessibilitySpanOptions
```

无障碍朗读功能属性。缺省时，取 [AccessibilitySpanOptions](arkts-arkui-accessibilityspanoptions-i.md)的默认值。

**类型：** [AccessibilitySpanOptions](arkts-arkui-textcommon-accessibilityspanoptions-i.md)

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-RichEditorBuilderSpanOptions-accessibilitySpanOptions?: AccessibilitySpanOptions--><!--Device-RichEditorBuilderSpanOptions-accessibilitySpanOptions?: AccessibilitySpanOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## offset

```TypeScript
offset?: int
```

添加builder的位置。省略或者为异常值时，添加到所有内容的最后。

**类型：** int

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-RichEditorBuilderSpanOptions-offset?: int--><!--Device-RichEditorBuilderSpanOptions-offset?: int-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

