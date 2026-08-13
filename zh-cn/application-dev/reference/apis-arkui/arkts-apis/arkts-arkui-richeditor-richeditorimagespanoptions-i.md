# RichEditorImageSpanOptions

设置图片的偏移位置和图片样式信息。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-unnamed-export declare interface RichEditorImageSpanOptions--><!--Device-unnamed-export declare interface RichEditorImageSpanOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## gesture

```TypeScript
gesture?: RichEditorGesture
```

行为触发回调。省略时，仅使用系统默认行为。

**类型：** [RichEditorGesture](arkts-arkui-richeditor-richeditorgesture-i.md)

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-RichEditorImageSpanOptions-gesture?: RichEditorGesture--><!--Device-RichEditorImageSpanOptions-gesture?: RichEditorGesture-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## imageStyle

```TypeScript
imageStyle?: RichEditorImageSpanStyle
```

图片样式。

**类型：** [RichEditorImageSpanStyle](arkts-arkui-richeditor-richeditorimagespanstyle-i.md)

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-RichEditorImageSpanOptions-imageStyle?: RichEditorImageSpanStyle--><!--Device-RichEditorImageSpanOptions-imageStyle?: RichEditorImageSpanStyle-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## offset

```TypeScript
offset?: int
```

添加图片的位置。省略时，添加到所有内容的末尾。 当值小于0时，设置在所有内容最前面；当值大于所有内容长度时，设置在所有内容最后面。

**类型：** int

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-RichEditorImageSpanOptions-offset?: int--><!--Device-RichEditorImageSpanOptions-offset?: int-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onHover

```TypeScript
onHover?: OnHoverCallback
```

鼠标悬停触发回调。省略时，不执行相关行为。

**类型：** [OnHoverCallback](arkts-arkui-onhovercallback-t.md)

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-RichEditorImageSpanOptions-onHover?: OnHoverCallback--><!--Device-RichEditorImageSpanOptions-onHover?: OnHoverCallback-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

