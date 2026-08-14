# RichEditorController

RichEditor组件的控制器，继承自[RichEditorBaseController](arkts-arkui-richeditor-richeditorbasecontroller-c.md#RichEditorBaseController)。 > **说明：** > > 当内容的长度超过组件显示区域的高度时，调用插入接口（例如[addTextSpan](#addTextSpan)、 > [addImageSpan](#addImageSpan)、[addBuilderSpan](#addBuilderSpan) > 、[addSymbolSpan](#addSymbolSpan)），组件会自动滚动内容使得插入内容末尾可见。

**继承/实现关系：** RichEditorController extends [RichEditorBaseController](arkts-arkui-richeditor-richeditorbasecontroller-c.md#RichEditorBaseController)

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-unnamed-export declare class RichEditorController--><!--Device-unnamed-export declare class RichEditorController-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## addBuilderSpan

```TypeScript
addBuilderSpan(value: CustomBuilder, options?: RichEditorBuilderSpanOptions): int | undefined
```

添加用户自定义布局Span。 > **说明：** > > - RichEditor组件添加占位Span，占位Span调用系统的measure方法计算真实的长宽和位置。 > > - 可通过[RichEditorBuilderSpanOptions](arkts-arkui-richeditor-richeditorbuilderspanoptions-i.md#RichEditorBuilderSpanOptions)设置此builder在RichEditor中的index（一个文字为一个单位）。 > > > - 此占位Span不可获焦，支持拖拽，支持部分通用属性，占位、删除等能力等同于ImageSpan，长度视为一个文字。 > > - 支持通过bindSelectionMenu设置自定义菜单。 > > - 不支持通过[getSpans](#getSpans)，[getSelection](#getSelection)， > onSelect，aboutToDelete获取 > builderSpan信息。 > > - 不支持通过[updateSpanStyle](#updateSpanStyle)， > [updateParagraphStyle](#updateParagraphStyle)等方式更新builder。 > > - 对此builder节点进行复制或粘贴不生效。 > > - builder的布局约束由RichEditor传入，如果builder里最外层组件不设置大小，则会用RichEditor的大小作为maxSize。 > > - builder的手势相关事件机制与通用手势事件相同，如果builder中未设置透传，则仅有builder中的子组件响应。 > > - 如果组件光标闪烁，插入后光标位置更新为新插入builder的后面。 通用属性仅支持[size](../../../reference/apis-arkui/arkui-ts/ts-universal-attributes-size.md#size)、 [padding](../../../reference/apis-arkui/arkui-ts/ts-universal-attributes-size.md#padding)、 [margin](../../../reference/apis-arkui/arkui-ts/ts-universal-attributes-size.md#margin)、 [aspectRatio](../../../reference/apis-arkui/arkui-ts/ts-universal-attributes-layout-constraints.md#aspectratio)、 [borderStyle](../../../reference/apis-arkui/arkui-ts/ts-universal-attributes-border.md#borderstyle)、 [borderWidth](../../../reference/apis-arkui/arkui-ts/ts-universal-attributes-border.md#borderwidth)、 [borderColor](../../../reference/apis-arkui/arkui-ts/ts-universal-attributes-border.md#bordercolor)、 [borderRadius](../../../reference/apis-arkui/arkui-ts/ts-universal-attributes-border.md#borderradius)、 [backgroundColor](../../../reference/apis-arkui/arkui-ts/ts-universal-attributes-background.md#backgroundcolor)、 [backgroundBlurStyle](../../../reference/apis-arkui/arkui-ts/ts-universal-attributes-background.md#backgroundblurstyle9) 、[opacity](../../../reference/apis-arkui/arkui-ts/ts-universal-attributes-opacity.md#opacity)、 [blur](../../../reference/apis-arkui/arkui-ts/ts-universal-attributes-image-effect.md#blur)、 [backdropBlur](../../../reference/apis-arkui/arkui-ts/ts-universal-attributes-background.md#backdropblur)、 [shadow](../../../reference/apis-arkui/arkui-ts/ts-universal-attributes-image-effect.md#shadow)、 [grayscale](../../../reference/apis-arkui/arkui-ts/ts-universal-attributes-image-effect.md#grayscale)、 [brightness](../../../reference/apis-arkui/arkui-ts/ts-universal-attributes-image-effect.md#brightness)、 [saturate](../../../reference/apis-arkui/arkui-ts/ts-universal-attributes-image-effect.md#saturate)、 [contrast](../../../reference/apis-arkui/arkui-ts/ts-universal-attributes-image-effect.md#contrast)、 [invert](../../../reference/apis-arkui/arkui-ts/ts-universal-attributes-image-effect.md#invert)、 [sepia](../../../reference/apis-arkui/arkui-ts/ts-universal-attributes-image-effect.md#sepia)、 [hueRotate](../../../reference/apis-arkui/arkui-ts/ts-universal-attributes-image-effect.md#huerotate)、 [colorBlend](../../../reference/apis-arkui/arkui-ts/ts-universal-attributes-image-effect.md#colorblend)、 [linearGradientBlur](../../../reference/apis-arkui/arkui-ts/ts-universal-attributes-image-effect.md#lineargradientblur12) 、[clip](../../../reference/apis-arkui/arkui-ts/ts-universal-attributes-sharp-clipping.md#clip12)、 [mask](../../../reference/apis-arkui/arkui-ts/ts-universal-attributes-sharp-clipping.md#mask12)、 [foregroundBlurStyle](../../../reference/apis-arkui/arkui-ts/ts-universal-attributes-foreground-blur-style.md#foregroundblurstyle) 、 [accessibilityGroup](../../../reference/apis-arkui/arkui-ts/ts-universal-attributes-accessibility.md#accessibilitygroup) 、 [accessibilityText](../../../reference/apis-arkui/arkui-ts/ts-universal-attributes-accessibility.md#accessibilitytext) 、 [accessibilityDescription](../../../reference/apis-arkui/arkui-ts/ts-universal-attributes-accessibility.md#accessibilitydescription) 、 [accessibilityLevel](../../../reference/apis-arkui/arkui-ts/ts-universal-attributes-accessibility.md#accessibilitylevel) 、 [sphericalEffect](../../../reference/apis-arkui/arkui-ts/ts-universal-attributes-image-effect.md#sphericaleffect12) 、[lightUpEffect](../../../reference/apis-arkui/arkui-ts/ts-universal-attributes-image-effect.md#lightupeffect12) 、 [pixelStretchEffect](../../../reference/apis-arkui/arkui-ts/ts-universal-attributes-image-effect.md#pixelstretcheffect12) 。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-RichEditorController-addBuilderSpan(value: CustomBuilder, options?: RichEditorBuilderSpanOptions): int | undefined--><!--Device-RichEditorController-addBuilderSpan(value: CustomBuilder, options?: RichEditorBuilderSpanOptions): int | undefined-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | CustomBuilder | 是 | 自定义组件。 |
| options | [RichEditorBuilderSpanOptions](arkts-arkui-richeditor-richeditorbuilderspanoptions-i.md) | 否 | builder选项。&lt;br/&gt;缺省时，按照 [RichEditorBuilderSpanOptions](arkts-arkui-richeditor-richeditorbuilderspanoptions-i.md#RichEditorBuilderSpanOptions)中的默认值生效。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| int | 添加完成的builderSpan所在的位置。 |

## addImageSpan

```TypeScript
addImageSpan(value: PixelMap | ResourceStr, options?: RichEditorImageSpanOptions): int | undefined
```

添加图片内容，如果组件光标闪烁，插入后光标位置更新为新插入图片的后面。 该接口为同步接口，在弱网环境下，直接添加网络图片可能会阻塞UI线程造成冻屏问题。不建议直接添加网络图片。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-RichEditorController-addImageSpan(value: PixelMap | ResourceStr, options?: RichEditorImageSpanOptions): int | undefined--><!--Device-RichEditorController-addImageSpan(value: PixelMap | ResourceStr, options?: RichEditorImageSpanOptions): int | undefined-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [PixelMap](../arkts-components/arkts-arkui-pixelmap-t.md) \| [ResourceStr](arkts-arkui-resourcestr-t.md) | 是 | 图片内容。 |
| options | [RichEditorImageSpanOptions](arkts-arkui-richeditor-richeditorimagespanoptions-i.md) | 否 | 图片选项。&lt;br/&gt;缺省时，按照 [RichEditorImageSpanOptions](arkts-arkui-richeditor-richeditorimagespanoptions-i.md#RichEditorImageSpanOptions)中的默认值生效。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| int | 添加完成的ImageSpan所在的位置。&lt;br/&gt;返回undefined时表示controller未与组件绑定。 |

## addSymbolSpan

```TypeScript
addSymbolSpan(value: Resource, options?: RichEditorSymbolSpanOptions): int | undefined
```

在Richeditor中添加SymbolSpan，如果组件光标闪烁，插入后光标位置更新为新插入Symbol的后面。 暂不支持手势、复制、拖拽处理。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-RichEditorController-addSymbolSpan(value: Resource, options?: RichEditorSymbolSpanOptions): int | undefined--><!--Device-RichEditorController-addSymbolSpan(value: Resource, options?: RichEditorSymbolSpanOptions): int | undefined-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [Resource](../../apis-localization-kit/arkts-apis/arkts-localization-resource-resource-i.md) | 是 | 组件内容。 |
| options | [RichEditorSymbolSpanOptions](arkts-arkui-richeditor-richeditorsymbolspanoptions-i.md) | 否 | 组件选项。&lt;br/&gt;缺省时，按照 [RichEditorSymbolSpanOptions](arkts-arkui-richeditor-richeditorsymbolspanoptions-i.md#RichEditorSymbolSpanOptions)中的默认值生效。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| int | 添加完成的SymbolSpan所在的位置。 |

## addTextSpan

```TypeScript
addTextSpan(content: ResourceStr, options?: RichEditorTextSpanOptions): int | undefined
```

添加文本内容，如果组件光标闪烁，插入后光标位置更新为新插入文本的后面。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-RichEditorController-addTextSpan(content: ResourceStr, options?: RichEditorTextSpanOptions): int | undefined--><!--Device-RichEditorController-addTextSpan(content: ResourceStr, options?: RichEditorTextSpanOptions): int | undefined-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| content | [ResourceStr](arkts-arkui-resourcestr-t.md) | 是 | 文本内容。 &lt;br&gt;从API version 20开始，支持Resource类型。 |
| options | [RichEditorTextSpanOptions](arkts-arkui-richeditor-richeditortextspanoptions-i.md) | 否 | 文本选项。&lt;br/&gt;缺省时，按照 [RichEditorTextSpanOptions](arkts-arkui-richeditor-richeditortextspanoptions-i.md#RichEditorTextSpanOptions)中的默认值生效。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| int | 添加完成的TextSpan所在的位置。&lt;br/&gt;返回undefined时表示controller未与组件绑定。 |

## deleteSpans

```TypeScript
deleteSpans(value?: RichEditorRange): void
```

删除指定范围内的文本和图片。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-RichEditorController-deleteSpans(value?: RichEditorRange): void--><!--Device-RichEditorController-deleteSpans(value?: RichEditorRange): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [RichEditorRange](arkts-arkui-richeditor-richeditorrange-i.md) | 否 | 删除范围。省略时，删除所有文本和图片。 |

## fromStyledString

```TypeScript
fromStyledString(value: StyledString): Array<RichEditorSpan> | undefined
```

将属性字符串转换为span信息。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-RichEditorController-fromStyledString(value: StyledString): Array<RichEditorSpan> | undefined--><!--Device-RichEditorController-fromStyledString(value: StyledString): Array<RichEditorSpan> | undefined-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [StyledString](arkts-arkui-styledstring-styledstring-c.md) | 是 | 转换前的属性字符串。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;[RichEditorSpan](arkts-arkui-richeditorspan-t.md)&gt; | 文本和图片Span信息。&lt;br/&gt;返回undefined时表示controller未与组件绑定。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | 参数检查失败。 |

## getParagraphs

```TypeScript
getParagraphs(value?: RichEditorRange): Array<RichEditorParagraphResult> | undefined
```

获取指定范围的段落。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-RichEditorController-getParagraphs(value?: RichEditorRange): Array<RichEditorParagraphResult> | undefined--><!--Device-RichEditorController-getParagraphs(value?: RichEditorRange): Array<RichEditorParagraphResult> | undefined-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [RichEditorRange](arkts-arkui-richeditor-richeditorrange-i.md) | 否 | 需要获取段落的范围。&lt;br/&gt;缺省时，获取所有段落信息。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;[RichEditorParagraphResult](arkts-arkui-richeditor-richeditorparagraphresult-i.md)&gt; | 选中段落的信息。&lt;br/&gt;返回undefined时表示controller未与组件绑定。 |

## getSelection

```TypeScript
getSelection(): RichEditorSelection | undefined
```

获取选中内容。未选中时，返回光标所在span信息。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-RichEditorController-getSelection(): RichEditorSelection | undefined--><!--Device-RichEditorController-getSelection(): RichEditorSelection | undefined-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [RichEditorSelection](arkts-arkui-richeditor-richeditorselection-i.md) | 选中内容信息。&lt;br/&gt;返回undefined时表示controller未与组件绑定。 |

## getSpans

```TypeScript
getSpans(value?: RichEditorRange): Array<RichEditorImageSpanResult | RichEditorTextSpanResult> | undefined
```

获取span信息。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-RichEditorController-getSpans(value?: RichEditorRange): Array<RichEditorImageSpanResult | RichEditorTextSpanResult> | undefined--><!--Device-RichEditorController-getSpans(value?: RichEditorRange): Array<RichEditorImageSpanResult | RichEditorTextSpanResult> | undefined-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [RichEditorRange](arkts-arkui-richeditor-richeditorrange-i.md) | 否 | 需要获取span范围。&lt;br/&gt;缺省时，获取所有span信息。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;[RichEditorImageSpanResult](arkts-arkui-richeditor-richeditorimagespanresult-i.md) \| [RichEditorTextSpanResult](arkts-arkui-richeditor-richeditortextspanresult-i.md)&gt; | 文本和图片Span信息。&lt;br/&gt;返回undefined 时表示controller未与组件绑定。 |

## toStyledString

```TypeScript
toStyledString(value: RichEditorRange): StyledString | undefined
```

将给定范围的组件内容转换成属性字符串。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-RichEditorController-toStyledString(value: RichEditorRange): StyledString | undefined--><!--Device-RichEditorController-toStyledString(value: RichEditorRange): StyledString | undefined-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [RichEditorRange](arkts-arkui-richeditor-richeditorrange-i.md) | 是 | 需要获取的范围。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [StyledString](arkts-arkui-styledstring-styledstring-c.md) | 转换后的属性字符串。&lt;br/&gt;返回undefined时表示controller未与组件绑定。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | 参数检查失败。 |

## updateParagraphStyle

```TypeScript
updateParagraphStyle(value: RichEditorParagraphStyleOptions): void
```

更新段落的样式。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-RichEditorController-updateParagraphStyle(value: RichEditorParagraphStyleOptions): void--><!--Device-RichEditorController-updateParagraphStyle(value: RichEditorParagraphStyleOptions): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [RichEditorParagraphStyleOptions](arkts-arkui-richeditor-richeditorparagraphstyleoptions-i.md) | 是 | 段落的样式选项信息。 |

## updateSpanStyle

```TypeScript
updateSpanStyle(value: RichEditorUpdateTextSpanStyleOptions | RichEditorUpdateImageSpanStyleOptions |
        RichEditorUpdateSymbolSpanStyleOptions): void
```

更新文本、图片或SymbolSpan样式。 若只更新了一个Span的部分内容，则会根据更新部分、未更新部分将该Span拆分为多个Span。 使用该接口更新文本、图片或SymbolSpan样式时默认不会关闭自定义文本选择菜单。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-RichEditorController-updateSpanStyle(value: RichEditorUpdateTextSpanStyleOptions | RichEditorUpdateImageSpanStyleOptions |        RichEditorUpdateSymbolSpanStyleOptions): void--><!--Device-RichEditorController-updateSpanStyle(value: RichEditorUpdateTextSpanStyleOptions | RichEditorUpdateImageSpanStyleOptions |        RichEditorUpdateSymbolSpanStyleOptions): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [RichEditorUpdateTextSpanStyleOptions](arkts-arkui-richeditor-richeditorupdatetextspanstyleoptions-i.md) \| [RichEditorUpdateImageSpanStyleOptions](arkts-arkui-richeditor-richeditorupdateimagespanstyleoptions-i.md) \| [RichEditorUpdateSymbolSpanStyleOptions](arkts-arkui-richeditor-richeditorupdatesymbolspanstyleoptions-i.md) | 是 | 文本、图片或SymbolSpan的样式选项信息。 |

