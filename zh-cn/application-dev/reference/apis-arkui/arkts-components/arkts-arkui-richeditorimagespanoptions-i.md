# RichEditorImageSpanOptions

设置图片的偏移位置和图片样式信息。

**起始版本：** 10

<!--Device-unnamed-declare interface RichEditorImageSpanOptions--><!--Device-unnamed-declare interface RichEditorImageSpanOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## gesture

```TypeScript
gesture?: RichEditorGesture
```

行为触发回调。省略时，仅使用系统默认行为。

**类型：** RichEditorGesture

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-RichEditorImageSpanOptions-gesture?: RichEditorGesture--><!--Device-RichEditorImageSpanOptions-gesture?: RichEditorGesture-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## imageStyle

```TypeScript
imageStyle?: RichEditorImageSpanStyle
```

图片样式信息。当需要自定义图片的大小、垂直对齐方式、缩放类型等样式时传入此参数；省略时，使用系统默认图片样式。

**类型：** RichEditorImageSpanStyle

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-RichEditorImageSpanOptions-imageStyle?: RichEditorImageSpanStyle--><!--Device-RichEditorImageSpanOptions-imageStyle?: RichEditorImageSpanStyle-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## offset

```TypeScript
offset?: number
```

添加图片的位置。省略时，添加到所有内容的末尾。

当值小于0时，设置在所有内容最前面；当值大于所有内容长度时，设置在所有内容最后面。

**类型：** number

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-RichEditorImageSpanOptions-offset?: number--><!--Device-RichEditorImageSpanOptions-offset?: number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onHover

```TypeScript
onHover?: OnHoverCallback
```

鼠标悬停触发回调。省略时，不执行鼠标悬停回调行为。

**类型：** OnHoverCallback

**起始版本：** 14

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本14开始，该接口支持在原子化服务API中使用。

<!--Device-RichEditorImageSpanOptions-onHover?: OnHoverCallback--><!--Device-RichEditorImageSpanOptions-onHover?: OnHoverCallback-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

