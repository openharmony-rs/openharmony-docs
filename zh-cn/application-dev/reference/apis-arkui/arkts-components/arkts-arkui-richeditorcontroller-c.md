# RichEditorController

RichEditor组件的控制器，继承自[RichEditorBaseController](arkts-arkui-richeditorbasecontroller-c.md#RichEditorBaseController)。 > **说明：** > > 当内容的长度超过组件显示区域的高度时，调用插入接口（例如[addTextSpan](#addTextSpan)、 > [addImageSpan](#addImageSpan)、[addBuilderSpan](#addBuilderSpan) > 、[addSymbolSpan](#addSymbolSpan)），组件会自动滚动内容使得插入内容末尾可见。

## 导入对象 ```ts controller: RichEditorController = new RichEditorController(); ```

**继承/实现关系：** RichEditorController extends [RichEditorBaseController](arkts-arkui-richeditorbasecontroller-c.md#RichEditorBaseController)

**起始版本：** 10

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为10。

**废弃版本：** -1

<!--Device-unnamed-declare class RichEditorController--><!--Device-unnamed-declare class RichEditorController-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## addBuilderSpan

```TypeScript
addBuilderSpan(value: CustomBuilder, options?: RichEditorBuilderSpanOptions): number
```

在RichEditor中添加用户自定义布局（BuilderSpan）。 > **说明：** > > - RichEditor组件添加占位Span，占位Span调用系统的measure方法计算真实的长宽和位置。 > > - 可通过[RichEditorBuilderSpanOptions](arkts-arkui-richeditorbuilderspanoptions-i.md#RichEditorBuilderSpanOptions)设置此builder在RichEditor中的index（一个文字为一个单位）。 > > - 此占位Span不可获焦，支持拖拽，支持部分通用属性，占位、删除等能力等同于ImageSpan，长度视为一个文字。 > > - 支持通过bindSelectionMenu设置自定义菜单。 > > - 不支持通过[getSpans](#getSpans)，[getSelection](#getSelection)， > onSelect，aboutToDelete获取 > builderSpan信息。 > > - 不支持通过[updateSpanStyle](#updateSpanStyle)， > [updateParagraphStyle](#updateParagraphStyle)等方式更新builder。 > > - 对此builder节点进行复制或粘贴不生效。 > > - builder的布局约束由RichEditor传入，如果builder里最外层组件不设置大小，则会用RichEditor的大小作为maxSize。 > > - builder的手势相关事件机制与通用手势事件相同，如果builder中未设置透传，则仅有builder中的子组件响应。 > > - 如果组件光标闪烁，插入后光标位置更新为新插入builder的后面。 > > - 对[addBuilderSpan](#addBuilderSpan)的节点文本， > enableDataDetector、 > dataDetectorConfig、 > enableSelectedDataDetector功能不会生效。 > 通用属性仅支持size、padding、margin、 > aspectRatio、borderStyle、 > borderWidth、borderColor、 > borderRadius、 > backgroundColor、 > backgroundBlurStyle > 、opacity、 > blur、 > backdropBlur、 > shadow、 > grayscale、 > brightness、saturate > 、contrast、 > invert、 > sepia、 > hueRotate、 > colorBlend、 > linearGradientBlur、 > clip、mask、 > foregroundBlurStyle > 、accessibilityGroup、 > accessibilityText、 > accessibilityDescription、 > accessibilityLevel、 > sphericalEffect、 > lightUpEffect、 > pixelStretchEffect。

**起始版本：** 11

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为11。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-RichEditorController-addBuilderSpan(value: CustomBuilder, options?: RichEditorBuilderSpanOptions): number--><!--Device-RichEditorController-addBuilderSpan(value: CustomBuilder, options?: RichEditorBuilderSpanOptions): number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | CustomBuilder | 是 | 自定义布局内容，用于在RichEditor中创建BuilderSpan占位组件。 |
| options | [RichEditorBuilderSpanOptions](arkts-arkui-richeditorbuilderspanoptions-i.md) | 否 | builder选项。当需要设置builder的偏移位置或无障碍属性时传入此参数；省略时，builder添加到所有内容末尾。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 添加完成的builderSpan在所有Span中的索引位置。 |

## addImageSpan

```TypeScript
addImageSpan(value: PixelMap | ResourceStr, options?: RichEditorImageSpanOptions): number
```

添加图片内容。如果组件光标闪烁，插入后光标位置更新为新插入图片的后面。当controller未绑定组件或绑定controller的组件被释放时，该接口调用无效。 该接口为同步接口，在弱网环境下，直接添加网络图片可能会阻塞UI线程造成冻屏问题。不建议直接添加网络图片。

**起始版本：** 10

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为10。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-RichEditorController-addImageSpan(value: PixelMap | ResourceStr, options?: RichEditorImageSpanOptions): number--><!--Device-RichEditorController-addImageSpan(value: PixelMap | ResourceStr, options?: RichEditorImageSpanOptions): number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | PixelMap \| ResourceStr | 是 | 图片内容。 |
| options | [RichEditorImageSpanOptions](arkts-arkui-richeditorimagespanoptions-i.md) | 否 | 图片选项。 &lt;br&gt;当需要设置图片样式、偏移位置或段落样式时传入此参数；不传入时，图片将使用默认样式插入到内容末尾。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 添加完成的ImageSpan在所有Span中的索引位置。 |

## addSymbolSpan

```TypeScript
addSymbolSpan(value: Resource, options?: RichEditorSymbolSpanOptions ): number
```

在RichEditor中添加图标小符号（SymbolSpan）。如果组件光标闪烁，插入后光标位置更新为新插入SymbolSpan的后面。 SymbolSpan暂不支持手势、复制操作和拖拽处理。

**起始版本：** 11

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为11。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-RichEditorController-addSymbolSpan(value: Resource, options?: RichEditorSymbolSpanOptions ): number--><!--Device-RichEditorController-addSymbolSpan(value: Resource, options?: RichEditorSymbolSpanOptions ): number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | Resource | 是 | SymbolSpan图标资源引用，用于指定系统预置或自定义的Symbol图标。 |
| options | [RichEditorSymbolSpanOptions](arkts-arkui-richeditorsymbolspanoptions-i.md) | 否 | symbol选项。 &lt;br&gt;当需要设置SymbolSpan的偏移位置或样式时传入此参数；不传入时，SymbolSpan将使用默认样式插入到内容末尾。 |

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

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为10。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-RichEditorController-addTextSpan(content: ResourceStr, options?: RichEditorTextSpanOptions): number--><!--Device-RichEditorController-addTextSpan(content: ResourceStr, options?: RichEditorTextSpanOptions): number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| content | ResourceStr | 是 | 文本内容。 &lt;br&gt;从API version 20开始，支持Resource类型。<br>**起始版本：** 20 |
| options | [RichEditorTextSpanOptions](arkts-arkui-richeditortextspanoptions-i.md) | 否 | 文本选项。 &lt;br&gt;当需要设置偏移位置、文本样式、段落样式等信息时传入此参数；不传入时，文本将使用默认样式插入到内容末尾。 |

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

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为10。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-RichEditorController-deleteSpans(value?: RichEditorRange): void--><!--Device-RichEditorController-deleteSpans(value?: RichEditorRange): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [RichEditorRange](arkts-arkui-richeditorrange-i.md) | 否 | 删除范围。省略时，删除所有文本和图片。 |

## fromStyledString

```TypeScript
fromStyledString(value: StyledString): Array<RichEditorSpan>
```

将属性字符串转换为span信息。

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-RichEditorController-fromStyledString(value: StyledString): Array<RichEditorSpan>--><!--Device-RichEditorController-fromStyledString(value: StyledString): Array<RichEditorSpan>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | StyledString | 是 | 转换前的属性字符串。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;[RichEditorSpan](arkts-arkui-richeditorspan-t.md)&gt; | 将属性字符串解析后得到的文本和图片Span信息，可用于查询属性字符串中各Span的内容、样式和位置。 &lt;br&gt;当controller未绑定组件或绑定controller的组件被释放时，返回undefined。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | The parameter check failed. |

## getParagraphs

```TypeScript
getParagraphs(value?: RichEditorRange): Array<RichEditorParagraphResult>
```

获取指定范围的段落信息。

**起始版本：** 11

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为11。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-RichEditorController-getParagraphs(value?: RichEditorRange): Array<RichEditorParagraphResult>--><!--Device-RichEditorController-getParagraphs(value?: RichEditorRange): Array<RichEditorParagraphResult>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [RichEditorRange](arkts-arkui-richeditorrange-i.md) | 否 | 需要获取段落的范围。 &lt;br&gt;省略时，获取所有段落信息。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;[RichEditorParagraphResult](arkts-arkui-richeditorparagraphresult-i.md)&gt; | 选中范围内的段落信息，包含各段落的样式和起始结束位置，可用于查询段落排版属性或进行段落样式更新。 &lt;br&gt;当controller未绑定组件或绑定controller的组件被释放时，返回undefined。 |

## getSelection

```TypeScript
getSelection(): RichEditorSelection
```

获取选中内容的范围和span信息。未选中时，返回光标所在span信息。

**起始版本：** 11

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为11。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-RichEditorController-getSelection(): RichEditorSelection--><!--Device-RichEditorController-getSelection(): RichEditorSelection-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [RichEditorSelection](arkts-arkui-richeditorselection-i.md) | 选中区域起始/结束位置及选中文本和图片的详细信息。 &lt;br&gt;当controller未绑定组件或绑定controller的组件被释放时，返回undefined。 |

## getSpans

```TypeScript
getSpans(value?: RichEditorRange): Array<RichEditorImageSpanResult | RichEditorTextSpanResult>
```

获取span信息。

**起始版本：** 10

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为10。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-RichEditorController-getSpans(value?: RichEditorRange): Array<RichEditorImageSpanResult | RichEditorTextSpanResult>--><!--Device-RichEditorController-getSpans(value?: RichEditorRange): Array<RichEditorImageSpanResult | RichEditorTextSpanResult>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [RichEditorRange](arkts-arkui-richeditorrange-i.md) | 否 | 需要获取span的范围。 &lt;br&gt;省略时，获取所有span信息。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;[RichEditorImageSpanResult](arkts-arkui-richeditorimagespanresult-i.md) \| [RichEditorTextSpanResult](arkts-arkui-richeditortextspanresult-i.md)&gt; | 指定范围内的文本和图片Span详细信息，包含各Span的位置、内容、样式等属性，可用 于查询和操作组件内的文本与图片内容。 &lt;br&gt;当controller未绑定组件或绑定controller的组件被释放时，返回undefined。 |

## toStyledString

```TypeScript
toStyledString(value: RichEditorRange): StyledString
```

将给定范围的组件内容转换成属性字符串，SymbolSpan和BuilderSpan不支持转换。

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-RichEditorController-toStyledString(value: RichEditorRange): StyledString--><!--Device-RichEditorController-toStyledString(value: RichEditorRange): StyledString-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [RichEditorRange](arkts-arkui-richeditorrange-i.md) | 是 | 需要获取的范围。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| StyledString | 组件指定范围内容转换后的属性字符串，可用于跨组件传递富文本内容或进行样式编辑操作。 &lt;br&gt;当controller未绑定组件或绑定controller的组件被释放时，返回undefined。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | The parameter check failed. |

## updateParagraphStyle

```TypeScript
updateParagraphStyle(value: RichEditorParagraphStyleOptions): void
```

更新段落的样式。

**起始版本：** 11

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为11。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-RichEditorController-updateParagraphStyle(value: RichEditorParagraphStyleOptions): void--><!--Device-RichEditorController-updateParagraphStyle(value: RichEditorParagraphStyleOptions): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [RichEditorParagraphStyleOptions](arkts-arkui-richeditorparagraphstyleoptions-i.md) | 是 | 段落的样式选项信息。 |

## updateSpanStyle

```TypeScript
updateSpanStyle(value: RichEditorUpdateTextSpanStyleOptions | RichEditorUpdateImageSpanStyleOptions | RichEditorUpdateSymbolSpanStyleOptions): void
```

更新文本、图片或SymbolSpan样式。 若只更新了一个Span的部分内容，则会根据更新部分、未更新部分将该Span拆分为多个Span。当controller未绑定组件或绑定controller的组件被释放时，该接口调用无效。 使用该接口更新文本、图片或SymbolSpan样式时默认不会关闭自定义文本选择菜单。

**起始版本：** 10

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为10。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-RichEditorController-updateSpanStyle(value: RichEditorUpdateTextSpanStyleOptions | RichEditorUpdateImageSpanStyleOptions | RichEditorUpdateSymbolSpanStyleOptions): void--><!--Device-RichEditorController-updateSpanStyle(value: RichEditorUpdateTextSpanStyleOptions | RichEditorUpdateImageSpanStyleOptions | RichEditorUpdateSymbolSpanStyleOptions): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [RichEditorUpdateTextSpanStyleOptions](arkts-arkui-richeditorupdatetextspanstyleoptions-i.md) \| [RichEditorUpdateImageSpanStyleOptions](arkts-arkui-richeditorupdateimagespanstyleoptions-i.md) \| [RichEditorUpdateSymbolSpanStyleOptions](arkts-arkui-richeditorupdatesymbolspanstyleoptions-i.md) | 是 | 文本、图片或SymbolSpan的样式选项信息。<br>**起始版本：** 11 |

