# RichEditorController

RichEditor组件的控制器，继承自[RichEditorBaseController](arkts-arkui-rich-editor-richeditorbasecontroller-c.md)。

> **说明：**  
>  
> 当内容的长度超过组件显示区域的高度时，调用插入接口（例如[addTextSpan](arkts-arkui-rich-editor-richeditorcontroller-c.md#addtextspan-1)、  
> [addImageSpan](arkts-arkui-rich-editor-richeditorcontroller-c.md#addimagespan-1)、[addBuilderSpan](arkts-arkui-rich-editor-richeditorcontroller-c.md#addbuilderspan-1)  
> 、[addSymbolSpan](arkts-arkui-rich-editor-richeditorcontroller-c.md#addsymbolspan-1)），组件会自动滚动内容使得插入内容末尾可见。

## 导入对象

```ts
controller: RichEditorController = new RichEditorController();
```

**继承/实现关系：** RichEditorController extends [RichEditorBaseController](arkts-arkui-rich-editor-richeditorbasecontroller-c.md)

**起始版本：** 10

<!--Device-unnamed-declare class RichEditorController extends RichEditorBaseController--><!--Device-unnamed-declare class RichEditorController extends RichEditorBaseController-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## addBuilderSpan

```TypeScript
addBuilderSpan(value: CustomBuilder, options?: RichEditorBuilderSpanOptions): number
```

在RichEditor中添加用户自定义布局（BuilderSpan）。

> **说明：**  
>  
> - RichEditor组件添加占位Span，占位Span调用系统的measure方法计算真实的长宽和位置。  
>  
> - 可通过[RichEditorBuilderSpanOptions](arkts-arkui-rich-editor-richeditorbuilderspanoptions-i.md)设置此builder在RichEditor中的index（一个文字为一个单位）。  
>  
> - 此占位Span不可获焦，支持拖拽，支持部分通用属性，占位、删除等能力等同于ImageSpan，长度视为一个文字。  
>  
> - 支持通过[bindSelectionMenu](RichEditorAttribute#bindSelectionMenu)设置自定义菜单。  
>  
> - 不支持通过[getSpans](arkts-arkui-rich-editor-richeditorcontroller-c.md#getspans-1)，[getSelection](arkts-arkui-rich-editor-richeditorcontroller-c.md#getselection-1)，  
> [onSelect](RichEditorAttribute#onSelect)，[aboutToDelete](RichEditorAttribute#aboutToDelete)获取  
> builderSpan信息。  
>  
> - 不支持通过[updateSpanStyle](arkts-arkui-rich-editor-richeditorcontroller-c.md#updatespanstyle-1)，  
> [updateParagraphStyle](arkts-arkui-rich-editor-richeditorcontroller-c.md#updateparagraphstyle-1)等方式更新builder。  
>  
> - 对此builder节点进行复制或粘贴不生效。  
>  
> - builder的布局约束由RichEditor传入，如果builder里最外层组件不设置大小，则会用RichEditor的大小作为maxSize。  
>  
> - builder的手势相关事件机制与通用手势事件相同，如果builder中未设置透传，则仅有builder中的子组件响应。  
>  
> - 如果组件光标闪烁，插入后光标位置更新为新插入builder的后面。  
>  
> - 对[addBuilderSpan](arkts-arkui-rich-editor-richeditorcontroller-c.md#addbuilderspan-1)的节点文本，  
> [enableDataDetector](RichEditorAttribute#enableDataDetector)、  
> [dataDetectorConfig](RichEditorAttribute#dataDetectorConfig)、  
> [enableSelectedDataDetector](RichEditorAttribute#enableSelectedDataDetector)功能不会生效。  
> 通用属性仅支持[size](arkts-arkui-common-commonmethod-c.md#size-1)、[padding](arkts-arkui-common-commonmethod-c.md#padding-1)、[margin](arkts-arkui-common-commonmethod-c.md#margin-1)、  
> [aspectRatio](arkts-arkui-common-commonmethod-c.md#aspectratio-1)、[borderStyle](arkts-arkui-common-commonmethod-c.md#borderstyle-1)、  
> [borderWidth](arkts-arkui-common-commonmethod-c.md#borderwidth-1)、[borderColor](arkts-arkui-common-commonmethod-c.md#bordercolor-1)、  
> [borderRadius](arkts-arkui-common-commonmethod-c.md#borderradius-1)、  
> [backgroundColor](arkts-arkui-common-commonmethod-c.md#backgroundcolor-1)、  
> [backgroundBlurStyle](arkts-arkui-common-commonmethod-c.md#backgroundblurstyle-1)  
> 、[opacity](arkts-arkui-common-commonmethod-c.md#opacity-1)、  
> [blur](arkts-arkui-common-commonmethod-c.md#blur-1)、  
> [backdropBlur](arkts-arkui-common-commonmethod-c.md#backdropblur-1)、  
> [shadow](arkts-arkui-common-commonmethod-c.md#shadow-1)、  
> [grayscale](arkts-arkui-common-commonmethod-c.md#grayscale-1)、  
> [brightness](arkts-arkui-common-commonmethod-c.md#brightness-1)、[saturate](arkts-arkui-common-commonmethod-c.md#saturate-1)  
> 、[contrast](arkts-arkui-common-commonmethod-c.md#contrast-1)、  
> [invert](arkts-arkui-common-commonmethod-c.md#invert-1)、  
> [sepia](arkts-arkui-common-commonmethod-c.md#sepia-1)、  
> [hueRotate](arkts-arkui-common-commonmethod-c.md#huerotate-1)、  
> [colorBlend](arkts-arkui-common-commonmethod-c.md#colorblend-1)、  
> [linearGradientBlur](arkts-arkui-common-commonmethod-c.md#lineargradientblur-1)、  
> [clip](arkts-arkui-common-commonmethod-c.md#clip-1)、[mask](arkts-arkui-common-commonmethod-c.md#mask-1)、  
> [foregroundBlurStyle](arkts-arkui-common-commonmethod-c.md#foregroundblurstyle-1)  
> 、[accessibilityGroup](arkts-arkui-common-commonmethod-c.md#accessibilitygroup-1)、  
> [accessibilityText](arkts-arkui-common-commonmethod-c.md#accessibilitytext-1)、  
> [accessibilityDescription](arkts-arkui-common-commonmethod-c.md#accessibilitydescription-1)、  
> [accessibilityLevel](arkts-arkui-common-commonmethod-c.md#accessibilitylevel-1)、  
> [sphericalEffect](arkts-arkui-common-commonmethod-c.md#sphericaleffect-1)、  
> [lightUpEffect](arkts-arkui-common-commonmethod-c.md#lightupeffect-1)、  
> [pixelStretchEffect](arkts-arkui-common-commonmethod-c.md#pixelstretcheffect-1)。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-RichEditorController-addBuilderSpan(value: CustomBuilder, options?: RichEditorBuilderSpanOptions): number--><!--Device-RichEditorController-addBuilderSpan(value: CustomBuilder, options?: RichEditorBuilderSpanOptions): number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [CustomBuilder](arkts-arkui-custombuilder-t.md) | 是 | 自定义布局内容，用于在RichEditor中创建BuilderSpan占位组件。 |
| options | [RichEditorBuilderSpanOptions](arkts-arkui-rich-editor-richeditorbuilderspanoptions-i.md) | 否 | builder选项。当需要设置builder的偏移位置或无障碍属性时传入此参数；省略时，builder添加到所有内容末尾。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 添加完成的builderSpan在所有Span中的索引位置。 |

## addImageSpan

```TypeScript
addImageSpan(value: PixelMap | ResourceStr, options?: RichEditorImageSpanOptions): number
```

添加图片内容。如果组件光标闪烁，插入后光标位置更新为新插入图片的后面。当controller未绑定组件或绑定controller的组件被释放时，该接口调用无效。

该接口为同步接口，在弱网环境下，直接添加网络图片可能会阻塞UI线程造成冻屏问题。不建议直接添加网络图片。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-RichEditorController-addImageSpan(value: PixelMap | ResourceStr, options?: RichEditorImageSpanOptions): number--><!--Device-RichEditorController-addImageSpan(value: PixelMap | ResourceStr, options?: RichEditorImageSpanOptions): number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | PixelMap \| ResourceStr | 是 | 图片内容。 |
| options | [RichEditorImageSpanOptions](arkts-arkui-rich-editor-richeditorimagespanoptions-i.md) | 否 | 图片选项。<br>当需要设置图片样式、偏移位置或段落样式时传入此参数；不传入时，图片将使用默认样式插入到内容末尾。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 添加完成的ImageSpan在所有Span中的索引位置。 |

## addSymbolSpan

```TypeScript
addSymbolSpan(value: Resource, options?: RichEditorSymbolSpanOptions ): number
```

在RichEditor中添加图标小符号（SymbolSpan）。如果组件光标闪烁，插入后光标位置更新为新插入SymbolSpan的后面。

SymbolSpan暂不支持手势、复制操作和拖拽处理。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-RichEditorController-addSymbolSpan(value: Resource, options?: RichEditorSymbolSpanOptions ): number--><!--Device-RichEditorController-addSymbolSpan(value: Resource, options?: RichEditorSymbolSpanOptions ): number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [Resource](../../apis-localization-kit/arkts-apis/arkts-localization-resource-resource-i.md) | 是 | SymbolSpan图标资源引用，用于指定系统预置或自定义的Symbol图标。 |
| options | [RichEditorSymbolSpanOptions](arkts-arkui-rich-editor-richeditorsymbolspanoptions-i.md) | 否 | symbol选项。<br>当需要设置SymbolSpan的偏移位置或样式时传入此参数；不传入时，SymbolSpan将使用默认样式插入到内容末尾。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 添加完成的SymbolSpan在所有Span中的索引位置。 |

## addTextSpan

```TypeScript
addTextSpan(content: ResourceStr, options?: RichEditorTextSpanOptions): number
```

添加文本内容。如果组件光标闪烁，插入后光标位置更新为新插入文本的后面。当controller未绑定组件或绑定controller的组件被释放时，该接口调用无效。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-RichEditorController-addTextSpan(content: ResourceStr, options?: RichEditorTextSpanOptions): number--><!--Device-RichEditorController-addTextSpan(content: ResourceStr, options?: RichEditorTextSpanOptions): number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| content | [ResourceStr](../arkts-apis/arkts-arkui-resourcestr-t.md) | 是 | 文本内容。<br>从API version 20开始，支持Resource类型。<br>**起始版本：** 20 |
| options | [RichEditorTextSpanOptions](arkts-arkui-rich-editor-richeditortextspanoptions-i.md) | 否 | 文本选项。<br>当需要设置偏移位置、文本样式、段落样式等信息时传入此参数；不传入时，文本将使用默认样式插入到内容末尾。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 添加完成的TextSpan在所有Span中的索引位置。 |

## deleteSpans

```TypeScript
deleteSpans(value?: RichEditorRange): void
```

删除指定范围内的文本和图片。当controller未绑定组件或绑定controller的组件被释放时，该接口调用无效。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-RichEditorController-deleteSpans(value?: RichEditorRange): void--><!--Device-RichEditorController-deleteSpans(value?: RichEditorRange): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [RichEditorRange](arkts-arkui-rich-editor-richeditorrange-i.md) | 否 | 删除范围。省略时，删除所有文本和图片。 |

## fromStyledString

```TypeScript
fromStyledString(value: StyledString): Array<RichEditorSpan>
```

将属性字符串转换为span信息。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-RichEditorController-fromStyledString(value: StyledString): Array<RichEditorSpan>--><!--Device-RichEditorController-fromStyledString(value: StyledString): Array<RichEditorSpan>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [StyledString](../arkts-apis/arkts-arkui-styled-string-styledstring-c.md) | 是 | 转换前的属性字符串。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Array](../../apis-arkts/arkts-apis/arkts-arkts-collections-array-c.md)<RichEditorSpan> | 将属性字符串解析后得到的文本和图片Span信息，可用于查询属性字符串中各Span的内容、样式和位置。<br>当controller未绑定组件或绑定controller的组件被释放时，返回undefined。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | The parameter check failed. |

## getParagraphs

```TypeScript
getParagraphs(value?: RichEditorRange): Array<RichEditorParagraphResult>
```

获取指定范围的段落信息。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-RichEditorController-getParagraphs(value?: RichEditorRange): Array<RichEditorParagraphResult>--><!--Device-RichEditorController-getParagraphs(value?: RichEditorRange): Array<RichEditorParagraphResult>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [RichEditorRange](arkts-arkui-rich-editor-richeditorrange-i.md) | 否 | 需要获取段落的范围。<br>省略时，获取所有段落信息。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Array](../../apis-arkts/arkts-apis/arkts-arkts-collections-array-c.md)<RichEditorParagraphResult> | 选中范围内的段落信息，包含各段落的样式和起始结束位置，可用于查询段落排版属性或进行段落样式更新。<br>当controller未绑定组件或绑定controller的组件被释放时，返回undefined。 |

## getSelection

```TypeScript
getSelection(): RichEditorSelection
```

获取选中内容的范围和span信息。未选中时，返回光标所在span信息。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-RichEditorController-getSelection(): RichEditorSelection--><!--Device-RichEditorController-getSelection(): RichEditorSelection-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [RichEditorSelection](arkts-arkui-rich-editor-richeditorselection-i.md) | 选中区域起始/结束位置及选中文本和图片的详细信息。<br>当controller未绑定组件或绑定controller的组件被释放时，返回undefined。 |

## getSpans

```TypeScript
getSpans(value?: RichEditorRange): Array<RichEditorImageSpanResult | RichEditorTextSpanResult>
```

获取span信息。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-RichEditorController-getSpans(value?: RichEditorRange): Array<RichEditorImageSpanResult | RichEditorTextSpanResult>--><!--Device-RichEditorController-getSpans(value?: RichEditorRange): Array<RichEditorImageSpanResult | RichEditorTextSpanResult>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [RichEditorRange](arkts-arkui-rich-editor-richeditorrange-i.md) | 否 | 需要获取span的范围。<br>省略时，获取所有span信息。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Array](../../apis-arkts/arkts-apis/arkts-arkts-collections-array-c.md)<RichEditorImageSpanResult \| RichEditorTextSpanResult> | 指定范围内的文本和图片Span详细信息，包含各Span的位置、内容、样式等属性，可用于查询和操作组件内的文本与图片内容。<br>当controller未绑定组件或绑定controller的组件被释放时，返回undefined。 |

## toStyledString

```TypeScript
toStyledString(value: RichEditorRange): StyledString
```

将给定范围的组件内容转换成属性字符串，SymbolSpan和BuilderSpan不支持转换。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-RichEditorController-toStyledString(value: RichEditorRange): StyledString--><!--Device-RichEditorController-toStyledString(value: RichEditorRange): StyledString-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [RichEditorRange](arkts-arkui-rich-editor-richeditorrange-i.md) | 是 | 需要获取的范围。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [StyledString](../arkts-apis/arkts-arkui-styled-string-styledstring-c.md) | 组件指定范围内容转换后的属性字符串，可用于跨组件传递富文本内容或进行样式编辑操作。<br>当controller未绑定组件或绑定controller的组件被释放时，返回undefined。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | The parameter check failed. |

## updateParagraphStyle

```TypeScript
updateParagraphStyle(value: RichEditorParagraphStyleOptions): void
```

更新段落的样式。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-RichEditorController-updateParagraphStyle(value: RichEditorParagraphStyleOptions): void--><!--Device-RichEditorController-updateParagraphStyle(value: RichEditorParagraphStyleOptions): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [RichEditorParagraphStyleOptions](arkts-arkui-rich-editor-richeditorparagraphstyleoptions-i.md) | 是 | 段落的样式选项信息。 |

## updateSpanStyle

```TypeScript
updateSpanStyle(value: RichEditorUpdateTextSpanStyleOptions | RichEditorUpdateImageSpanStyleOptions | RichEditorUpdateSymbolSpanStyleOptions): void
```

更新文本、图片或SymbolSpan样式。

若只更新了一个Span的部分内容，则会根据更新部分、未更新部分将该Span拆分为多个Span。当controller未绑定组件或绑定controller的组件被释放时，该接口调用无效。

使用该接口更新文本、图片或SymbolSpan样式时默认不会关闭自定义文本选择菜单。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-RichEditorController-updateSpanStyle(value: RichEditorUpdateTextSpanStyleOptions | RichEditorUpdateImageSpanStyleOptions | RichEditorUpdateSymbolSpanStyleOptions): void--><!--Device-RichEditorController-updateSpanStyle(value: RichEditorUpdateTextSpanStyleOptions | RichEditorUpdateImageSpanStyleOptions | RichEditorUpdateSymbolSpanStyleOptions): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | RichEditorUpdateTextSpanStyleOptions \| RichEditorUpdateImageSpanStyleOptions \| RichEditorUpdateSymbolSpanStyleOptions | 是 | 文本、图片或SymbolSpan的样式选项信息。<br>**起始版本：** 11 |

